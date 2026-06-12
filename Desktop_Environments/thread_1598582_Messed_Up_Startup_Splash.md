---
title: "Messed Up Startup Splash"
date: 2010-10-16
forum: Desktop Environments
---

### Post by motsteve on 2010-10-16
I have just updated my Ubuntu to Maverick and so far so good.  However, even in Lucid Lynx my startup splash screen showed Xubuntu even though I had only tried it once and went back to Gnome.  I searched high and low for a fix on the forums and found all kinds of info and no fixes.  I have had success by taking part of one forum answer and gluing it to another one to come up with a solution:

 To set the Ubuntu splash screen:

        $ sudo update-alternatives --config default.plymouth
#Then pick the startup splash that you want from the numbered list.

Then:
        $ sudo update-initramfs -u

Then reboot.

I hope this helps someone out there like me who was totally lost.:)

---

