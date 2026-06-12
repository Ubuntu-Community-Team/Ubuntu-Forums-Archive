---
title: "Need help in setting up compiz fusion on my laptop"
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by yinglcs2 on 2007-08-03
Hi,

I need some help in setting up compiz fusion on my laptop.

I see a sticky thread here:
[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

But my question is do I need to enable my graphic card for 3d effect first before I can start the installation described in the thread? My laptop has a graphic card from ATI.

Thank you.

---

### Post by dougfractal on 2007-08-05
> do I need to enable my graphic card for 3d effect first before I can start   
**Yes**


Please provide more info
> 
lsb_release -d
uname -r

lspci -nn

glxinfo | head -4

cat /etc/X11/xorg.conf


---

