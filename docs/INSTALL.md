# Install and activate ClipSync

Downloads and SHA‑256 checksums: <https://osvald-studio.com/download>

## 1. Android

1. Download `ClipSync-<version>.apk` on the phone (or copy it over).
2. Open the file. Android asks to allow installs from your browser or file manager the first time — allow it, then tap **Install**.
3. Open ClipSync and grant only what you need:
   - **Notifications** — to show phone notifications on the computer and to control media.
   - **Nearby devices / Local network** (Android 13+ / 17+) — required for discovery on your Wi‑Fi.
   - **Camera** — only to scan a pairing QR code.
   - Calls, Photos, Microphone (mirroring audio) and **Accessibility** (control from the computer) are optional and are asked for only when you turn those features on in **Settings**.
4. On Android 10+ the phone cannot read the clipboard in the background: send with ClipSync open, the **Send clipboard** tile / notification, or the Share sheet. Receiving works in the background.

**Phones without Google services (Huawei etc.)** — the APK works as is; QR scanning is built in.

**Updates** — ClipSync checks for updates daily on Wi‑Fi (Settings → *Check for updates*). The download is verified against a signed manifest and the app's own signing key before Android asks you to install it. [Obtainium](https://github.com/ImranR98/Obtainium) can also track the download page.

## 2. Linux

- **Ubuntu / Debian**: `sudo apt install ./ClipSync-<version>-amd64.deb`, then start *ClipSync* from the app grid. It lives in the tray (GNOME needs the AppIndicator extension, on by default in Ubuntu).
- **Any distribution**: `chmod +x ClipSync-<version>-x86_64.AppImage && ./ClipSync-<version>-x86_64.AppImage`.
- **Firewall**: if `ufw` is on, ClipSync shows the exact one‑time command. It is:
  `sudo ufw allow from 192.168.0.0/24 to any port 8766:8768 proto tcp comment ClipSync` (adjust your subnet) plus UDP 8770 and 5353.
- Settings → *Start at login* adds an XDG autostart entry.

## 3. Windows

Run `ClipSync-Setup-<version>.exe` (or the portable `.exe`). Windows SmartScreen may warn because the installer is not code‑signed by a certificate authority: click **More info → Run anyway** after checking the SHA‑256 on the download page. ClipSync starts in the tray and can start with Windows.

## 4. macOS

1. Open `ClipSync-<version>.dmg` and drag ClipSync into **Applications**.
2. First launch: macOS says the app cannot be verified. Open **System Settings → Privacy & Security**, scroll to *Security*, click **Open Anyway**, confirm.
   Terminal alternative: `xattr -dr com.apple.quarantine /Applications/ClipSync.app`
3. Allow **Local Network** access when asked (or in *Privacy & Security → Local Network*).
4. ClipSync lives in the menu bar. For media control it asks for Automation access to Spotify / Music the first time.

## 5. Pair devices

1. Put all devices on the same Wi‑Fi.
2. Open **Devices** on both. The other device appears by its name (e.g. *OnePlus 6T*, *Linux PCMS*).
3. Tap **Pair** on one device. A **6‑digit code** appears on both screens — approve only if they match.
4. Done. Devices stay paired; names update automatically if you rename a device.

If a device does not appear: check that the router does not isolate clients (guest Wi‑Fi), that no VPN is active, and the firewall note above. You can also enter the IP address manually on the computer.

## 6. Activate your license

1. Buy a key on the [website](https://osvald-studio.com/buy). You pay $19 once in USDC on the Base network; the key `OSV-XXXX-XXXX-XXXX-XXXX` is shown as soon as the payment confirms (usually within a minute). Save it.
2. On any device: **Settings → License → Activate**, paste the key. The device registers one of your 5 seats and becomes **Pro**.
3. Other paired devices receive the license automatically from the activated one (encrypted, over your Wi‑Fi) and register their own seat. If a device was offline, activate it with the same key.
4. Moving to a new phone or computer: **Settings → License → Deactivate this device** on the old one, or open <https://osvald-studio.com/activate>, enter the key and unlink the device there. Then activate the new one.

The app checks the license with the server about once a month; it keeps working offline in between.

## 7. Uninstall

- Android: like any app. Pairings on other devices can be removed in their **Devices** list.
- Linux: `sudo apt remove clipsync` or delete the AppImage; settings live in `~/.config/ClipSync`.
- Windows: *Apps & features*, or the *Uninstall* button in ClipSync's About.
- macOS: drag ClipSync out of Applications; keys are in Keychain under *ClipSync*.
