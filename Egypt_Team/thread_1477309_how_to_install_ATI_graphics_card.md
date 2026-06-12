---
title: "how to install ATI graphics card???"
date: 2010-05-08
forum: Egypt Team
---

### Post by black panther on 2010-05-08
I have this problem long ago......only 8-10 could install it
but after it no other release could do that
I have ATI radeon 2100 integrated with mother board
when I open the hardware drivers it says no propietary drivers are in use on this system
I tried this command in terminal :
sudo
apt-get install xserver-xorg-video=ati
and it gets downloaded but it couldn't configure the card.
whenever I try to even confugure the visual effects it says couldn't apply
then I tried to install all ATI packages from the software center then I had ATI catalyst control center when H opened it a message came out saying
(There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.)
i couldn't understand what does the ( aticonfig ) means??
I want to know now what else can I do??
I have now linux UBUNTU 10-4 
ATI radeon 2100 512 vram
please I am in a bad need to configure it...I can't get any design programe to work without the card installed

---

### Post by mahmoud mohamed on 2010-05-08
i hope it helps u :)

[http://ubuntuforums.org/showthread.php?p=3177662](http://ubuntuforums.org/showthread.php?p=3177662)

---

### Post by TheHardDisk on 2010-05-08
Please do NOT follow Envy installations as it is obsolete and WILL break yous system.

Follow this:
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
install the latest xorg edgers ppa...

before that, try to install:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.3&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.3&lang=English)

if it doesnt work then follow the ubuntu wiki

---

