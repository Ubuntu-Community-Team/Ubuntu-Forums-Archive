---
title: "[SOLVED] xorg.conf Unable to be backed up."
date: 2008-09-24
forum: Desktop Environments
---

### Post by LOTM on 2008-09-24
I'm still a bit of a newbie to all this so bear with me in case this is a really simply issue. 

I just switched from Windows XP to Ubuntu on Monday due to my XP install randomly destroying itself. So far, I've been very happy with Ubuntu, everything has worked easier, the programs run smoother, etc. However, I have a Dual 22" 16:10 Widescreen monitor setup, and I've figured out that setting it up is evidently is 1 part luck and 2 parts black magic. I am using a nVidia 7600GT graphics card, so I followed the standard advice and installed the proprietary drivers for it, then after much confusion with how Terminal worked, finally found the nvidia-settings tool. Now, I've figured out how to use the tool, and set it up, I set it for Twinview, and applied it, but that just made my monitors into one abnormally wide monitor that was cumbersome to use, so I tried the other option, "Use monitor as separate X Screen." Now, when I hit apply after setting that, it shuts off my 2nd monitor and gives some message about not having applied everything. So i tried the "Save to X Configuration file, Except when I tell it to do it, it pops up an error saying "Unable to create new X config backup file '/etc/x11/xorg.conf.backup'. Do you have any idea why this might be happening and what I need to do to fix it?

Thanks for reading the huge block of text... If you need more info, I can give it.

---

### Post by sayakb on 2008-09-24
Run nvidia-settings as root. At a terminal, type in:
```
gksudo nvidia-settings
```

---

### Post by LOTM on 2008-09-24
Thank you, that worked perfectly.

---

