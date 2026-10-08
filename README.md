# Definitely Not Passwords

*Your passwords are definitely not in here.*

A local-first password vault for Windows. Your passwords live in one encrypted `.dnpv` file that you keep
wherever you like. There's no account, no cloud and no telemetry, and the app never connects to the
network.

This repository holds the **released builds** only. Download them from
[Releases](https://github.com/stevenklinck/Definitely-Not-Passwords-Releases/releases).

## Download

Each release has:

| File | What it is |
|---|---|
| `DefinitelyNotPasswords-<version>-win-x64.msi` | Installer (Windows 10/11, 64-bit) |
| `DefinitelyNotPasswords-<version>-win-x64-portable.zip` | The same app without installing; extract and run `DefinitelyNotPasswords.exe` |
| `SHA256SUMS.txt` | Checksums for the files above |
| `THIRD-PARTY-NOTICES.txt` | Licences of the open-source components included in the app |

### Check your download

In PowerShell, in the folder you downloaded to:

```powershell
Get-FileHash .\DefinitelyNotPasswords-*-win-x64.msi -Algorithm SHA256
```

The hash must match the line for that file in `SHA256SUMS.txt`.

### "Windows protected your PC"

The builds aren't code-signed yet, so SmartScreen may warn the first time you run them. Check the
checksum first, then choose **More info → Run anyway**.

## How your vault is protected

- The master password is stretched with **Argon2id**, tuned to take about a second on your PC, so
  guessing passwords offline is slow.
- The vault is encrypted with **AES-256-GCM**, using the `cryptography` library and OpenSSL. Nothing is
  home-grown.
- Everything inside the vault is encrypted, including entry titles and group names.
- Saves are crash-safe, and encrypted backups (`.bak1` …) are kept beside the vault.
- Copied passwords are cleared from the clipboard after a timeout and kept out of Windows Clipboard
  History.
- The vault locks after inactivity, when Windows locks or sleeps, and optionally on minimise.

**There is no password reset.** If you forget a vault's master password, nobody can recover it.

## Uninstalling

Uninstalling removes the program only. It never deletes vault files, backups or your settings
(`%LOCALAPPDATA%\DefinitelyNotPasswords`).

---

Copyright © 2026 Steven Klinck. Third-party components are listed with their licences in
`THIRD-PARTY-NOTICES.txt`.
