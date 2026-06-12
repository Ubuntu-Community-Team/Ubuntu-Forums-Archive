---
title: "Gnome panel problem"
date: 2010-05-22
forum: Desktop Environments
---

### Post by ronni on 2010-05-22
Hi,

I've just made a fresh install of Ubuntu 10.04.

When I right-click a panel and choose "New Panel", the panel is made, but is not visible. The panel is placed on the left side of the screen, and icons on the desktop is moved to the right. Also windows does not use the full width of the screen when maximized.

I've tried to remove the panel configuration in my home directory, logout and login, installing ATI drivers and running a gnome-panel command (from another post on ubuntu forums), but nothing works.

Any suggestions on this?

---

### Post by balaknair on 2010-05-22
I have the same issue on 10.04, some sort of bug in gnome-panel 2.30 apparently.
Here's what works for me.

Hit Alt-F2--> type in ***killall gnome-panel*** and hit enter.

This will restart the gnome-panel application and the new panel ought to become visible.

---

### Post by clymir on 2010-05-24
I've ALSO  just made an install of Ubuntu 10.04. :

GNONE PANEL causes a fatal instability if I try running it "unexpanded".  

The system completely hangs except that I can close opera and truecrypt before I fall back to BIOS. 

System Monitor will not start-up for a kill... nothing "system" at all will respond infact, and the panel I  "unexpanded" just sits there quivering like its trying to escape a loop.

 I also noticed that two of everything appears on the panel
 when first unexpanded, and if I re-expand it right away there is no issue.

I'd like NOT to have to fall back to 8.04.4: I threw my disc out. One difference here tho:

 I ended up upgrading instead on this machine, of three I  installed it on, because it wouldnt boot the same CD: It DOES pass the checksum tests.

Any ideas are appreciated. Thanks.

---

