---
title: "driver for dell P2311H"
date: 2011-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by InVirtualBox on 2011-06-30
Hi,

I have been trying to improve on the 600x400 resolution on my 23inch monitor (!) in Ubuntu (Gnome) but it just wont work!

I've done system>preferences etc - no option better than 600x400, also have tried to look at xorg.conf file but its either empty or missing. I have a windows driver for the monitor and it gives great 1920x1080, but I am running ubuntu in a machine inside a virtual box and its here that I have the problem!

Can anyone suggest how to sort this out?

Thanks in advance!

---

### Post by ajgreeny on 2011-06-30
This is more likely down to the driver for your graphics card.  What hardware are you using?

---

### Post by mikewhatever on 2011-06-30
If Ubuntu runs in VirtualBox, you need to install Guest additions for Ubuntu to be able to get higher resolutions. Once installed, simply expand the VirtualBox window, and the resolution will auto-adjust.
[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

---

### Post by InVirtualBox on 2011-07-01
mikewhatever: Thanks! Its much better now :D Perfect!
 
ajgreeny: its a dell monitor, and it seems they only have windows OS drivers... thats the problem!

---

