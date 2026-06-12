---
title: "nVidia problem"
date: 2005-04-05
forum: Desktop Environments
---

### Post by Linatux on 2005-04-05
Have desktop (KDE) running fine. Installed nVidia driver, enabled, changed xorg.conf etc.  X & nVidia start fine, but some parts of my desktop ('start bar') are blurry (not refresh), desktop doesn't seem to refresh properly (pop-ups stay on screen) & I can't read anything (font problem?) - typing in the dark. Kill KDM, reset xorg.conf back to "nv" (DRI etc) and everything back to normal. 

Good chance that upgrade/dist-upgrade will fix my problem, but 300Mb on dial-up is not an option. Anyone had similar problem & know what I need to fix it. 

This machine is running an old PCI TNT2 card. Next step (if I can get this working) will be to upgrade my main machine to Ubantu, but can't afford to do until everything works correctly.

---

### Post by freelsjd on 2005-04-06
What are you running if you are not running Ubuntu now ?  This is a kubuntu help forum.

Do you have a svga card/monitor or a dvi card/monitor ?

what version of the nvidia driver are you running ?  ARe you running the driver from the Ubuntu install or the latest driver from nvidia ?

---

### Post by dermotti on 2005-04-06
I have this same exact problem. It occured un nvidia 62.99 and the latest nvidia driver. MY system has all the latest updates too.

---

### Post by Linatux on 2005-04-07
[QUOTE=freelsjd]What are you running if you are not running Ubuntu now ?  This is a kubuntu help forum. 
[COLOR=Red]I have several boxes. Main one currently on a mix'n'match Knoppix/Debian/other-bits. Testing Kubantu on spare machine.[/COLOR]

Do you have a svga card/monitor or a dvi card/monitor ? [COLOR=Red]SVGA - TNT2 M64 & ViewSonic CRT monitor ... both old, but both run fine.[/COLOR]

what version of the nvidia driver are you running ?  ARe you running the driver from the Ubuntu install or the latest driver from nvidia ?[/QUOTE]
[COLOR=Red]oops - forgot to check. Posting from work as forum wouldn't remember my credentials from home. Whatever was in preview ISO about a week ago. Trying to update, but dial-up dodgy lately.[/COLOR]

---

### Post by Linatux on 2005-04-11
Upgraded some X & nVidia packages - all seems to be fine now.
Maybe a package was missing?

---

