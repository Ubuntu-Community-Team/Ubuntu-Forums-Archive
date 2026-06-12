---
title: "No panel bars after wine+vlc"
date: 2007-05-06
forum: Desktop Environments
---

### Post by Valeranth on 2007-05-06
I recently, less then a hour ago, installed vlc threw wine so that I could play some .mkv files my friend had sent me. When it started it was in full screen yet my desktop icons and other windows where still over it, causing a flicker affect. I evently managed to kick it into full-screen mode and it all worked fine. For a time. 

After it was done, and I had managed to close it, None of my desktop panels where there. Ctrl+alt+Backspace right? Nope. Ive tried everything to get the panel bars back but the only think that seems to work is failsafe gnome.

I am using Xubuntu with beryl, and no beryl never gave me problems before and will still work fine without the panel bars (they are also still gone with beryl off, I don't have it set to normally start up), and have the normal Ubuntu desktop installed.

Any Ideas on what to do?

---

### Post by RCC2k7 on 2007-05-06
Try pressing ALT+F2 and at the Run Command dialog, type "killall gnome-panel" without the quotes, then press Enter. The panels should reload. 

If you can't access even the Run Command dialog, you can issue this command by logging into a text console (ALT+CTRL+F1) using the same username you used for logging into the desktop. When you issue the command, press ALT+CTRL+F7 to return to your desktop.

If any of these suggestions work, you can actually create a desktop launcher with the above command, name it Restore Panels (or whatever you prefer) and that way you can restore the panels just by double-clicking a desktop icon.

This should at least provide you with temporary relief while you find a permanent solution.

---

### Post by notwen on 2007-05-06
Doubt this is your issue, but you could try using VLC for linux and by-pass having to use wine at all for playing your .mkv files. =]

---

