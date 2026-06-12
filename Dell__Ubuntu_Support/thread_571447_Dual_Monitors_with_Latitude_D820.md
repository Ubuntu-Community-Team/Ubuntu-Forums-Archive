---
title: "Dual Monitors with Latitude D820"
date: 2007-10-09
forum: Dell  Ubuntu Support
---

### Post by hzambran on 2007-10-09
Hi, I-m using Ubuntu Feisty 7.04 on a Dell Latitude D820, and I-m wondering how to set up two monitors.

I achieved something with the command

gksudo nvidia-settings

but when I try to save the cong. file I got the following error

ERROR: Failed to generate an X config file!

Regards

Mauricio

---

### Post by phr0ze on 2007-10-10
I'd hate to say it, but wait 8 days and upgrade to Gutsy before doing any further trouble shooting. It may work out of the box in Gutsy.

---

### Post by =JeffH on 2007-10-10
So u have an nvidia graphics adapter which is what I have on my D820. 

I recently [*got hotkey switching between builtin LCD and external monitors working*]("http://www.nvnews.net/vbulletin/showpost.php?p=1407211&postcount=81") by using the 100.14.09 rev of the nvidia binary (sigh) driver, [*which is here*]("http://www.nvidia.com/object/linux_display_ia32_100.14.09.html"). 

You may want to borrow my xorg.conf file, which is in [*this post here on the nvidia forums*]("http://www.nvnews.net/vbulletin/showthread.php?t=100060"). 

Somewhat extraneous recent info leading up to my getting it working [*begins here*]("http://www.nvnews.net/vbulletin/showpost.php?p=1399914&postcount=12"). Bottom line is that the current 100.14.19 driver didn't work for me. The [*entire thread beginning last summer is here*]("http://www.nvnews.net/vbulletin/showthread.php?t=92641").  

hope this helps, 

=JeffH

ps: Also note that with Xinerama turned on, as is done in my xorg.conf, if you restart X with an external monitor attached and use my xorg.conf (which nvidia-settings can gen for you), you can have a single desktop that spans both monitors, which is useful. however, it can't be turned on/off without restarting X -- there's no apparent way to dynamically enable it. [*See my post about  this here*]("http://www.nvnews.net/vbulletin/showthread.php?t=100065").

pps: I think we should all be encouraging nvidia to migrate their driver posture to an open source one, which would necessitate their publishing their GPU specs. Beats me why they feel they have to keep them secret -- they aren't charging for drivers. And the apparent word is that ATI/AMD is going to publish theirs.

---

