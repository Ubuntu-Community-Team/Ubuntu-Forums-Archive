---
title: "Login Screen Resolution Problem"
date: 2005-09-08
forum: Desktop Environments
---

### Post by imipolex on 2005-09-08
Hello. I just finished installing Ubuntu 5.04 (nice distro!). One problem though--the login screen is set by default to a higher resolution/refresh rate than my monitor supports so I get ugly squiggly lines running vertically across the screen. The first time I logged in I set the resolution to 1024 x 768 in Gnome so now everything is fine once I'm logged in but the login screen is still screwed up. Any ideas on how to change this? I'm not afraid of editing config files so if that's the easiest way to do it let me know. Thanks for any help.

---

### Post by scav on 2005-09-08
[QUOTE=imipolex]Hello. I just finished installing Ubuntu 5.04 (nice distro!). One problem though--the login screen is set by default to a higher resolution/refresh rate than my monitor supports so I get ugly squiggly lines running vertically across the screen. The first time I logged in I set the resolution to 1024 x 768 in Gnome so now everything is fine once I'm logged in but the login screen is still screwed up. Any ideas on how to change this? I'm not afraid of editing config files so if that's the easiest way to do it let me know. Thanks for any help.[/QUOTE]


Check the /etc/X11/xorg.conf file, global resolution settings are there

---

### Post by imipolex on 2005-09-08
Thanks--that helped. I deleted the unsupported resolution from /etc/X11/xorg.conf and it fixed the problem. For anyone else who happens to have the same problem in the future here's the exact line to modify:

in "Screen" section of xorg.conf note the 'DefaultDepth' (24 in my case) then go to the SubSection for that default depth and modify the 'Modes' line to show only supported reolutions.

---

### Post by Archangel on 2005-09-09
OK, I have a similar problem and it sounds like what you are suggesting will fix the problem, but how do I edit the file from the recovery mode, thats how far I can get it to boot?

---

