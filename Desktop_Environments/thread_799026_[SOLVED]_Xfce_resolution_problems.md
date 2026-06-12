---
title: "[SOLVED] Xfce resolution problems"
date: 2008-05-18
forum: Desktop Environments
---

### Post by absolutezero1287 on 2008-05-18
I'm on Ubuntu 8.04 and everything's working great. I got tired of Gnome and decided to give XFCE a shot and now it's my default desktop environment. Today I decided to tweak it. I changed around the theme and all that. Then I decided to see what it would look like on a different resolution. I went higher than my default 1024X768 and the screen went blank. I waited for a while and the screen was still blank...so I reluctantly hit the power button.

Upon trying to log in to my xfce session, all I got was a beige-ish background (the one from the human theme). I was able to move the mouse around but that's it. There were no icons or anything else that was remotely useful. I'm on the failsafe Gnome session right now. Is there anything that I can do?

---

### Post by garyedwardjohnston on 2008-05-18
Boot in safe graphics mode from the login menu, then change it back and reboot.

---

### Post by absolutezero1287 on 2008-05-18
Well, I couldn't find the safe graphics mode option. All that I had at the login screen were the usual shut down, restart, hibernate, change session, etc. So I choose recovery mode (or something like that) from grub's boot menu. I then chose the to fix "x" which restored the default settings for xorg. Thanks for your help, but I got it. ;)

---

### Post by garyedwardjohnston on 2008-05-23
Good stuff.

---

