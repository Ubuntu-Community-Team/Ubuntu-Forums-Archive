---
title: "Which image shall I download to install Ubuntu 9.04 desktop"
date: 2009-05-25
forum: General Help
---

### Post by satimis on 2009-05-25
Hi folks,


I need to install Ubuntu 9.04 i386 workstation on a new HD with net installation.  I expect using USB stick to boot the PC starting installation.  On following sites;

[http://mirror.aarnet.edu.au/pub/ubuntu/releases/9.04/](http://mirror.aarnet.edu.au/pub/ubuntu/releases/9.04/)

[http://ftp.hostrino.com/pub/ubuntu/archive/dists/jaunty/main/installer-i386/current/images/netboot/](http://ftp.hostrino.com/pub/ubuntu/archive/dists/jaunty/main/installer-i386/current/images/netboot/)

I found follows;
```

mini.iso
netboot.tar.gz
ubuntu-9.04-netbook-remix-i386.img  
etc.

```

Please advise whether to download "mini.iso" OR "netboot.tar.gz" OR "ubuntu-9.04-netbook-remix-i386.img" ?  Pointer would be appreciated.  TIA


B.R.
satimis

---

### Post by themusicalduck on 2009-05-25
Do you want to install the standard Ubuntu desktop version? You could use the netbook remix .img file if you liked, but its a version of Ubuntu that's designed for netbooks and not normal desktops or laptops.

If you have access to an Ubuntu install, then the best way to make a USB disk is to download an Ubuntu .iso from [www.ubuntu.com](www.ubuntu.com) and use the 'USB Startup Disk Creator' program under System > Administration.

UNetBootin I think is another way to make a USB disk and is also available under windows if you only have use of a windows install. This program also downloads the .iso automatically for you if you like.

---

### Post by satimis on 2009-05-25
> **themusicalduck said:**
> Do you want to install the standard Ubuntu desktop version? You could use the netbook remix .img file if you liked, but its a version of Ubuntu that's designed for netbooks and not normal desktops or laptops.
Hi themusicalduck,

Thanks for your advice.

I only need a standard Ubuntu desktop.  What I'm prepared to do is testing server consolidation installing Ubuntu 9.04 workstation as host. On its top I'll install KVM and guests. The host is used for installing/configuring the guests which are headless servers except Windows.

```

PC &#8211; AMD dualcore CPU with 4G RAM onboard

Ubuntu 9.04 workstation &#8211; host
Ubuntu 9.04 server/Debian 5.0 &#8211; guest
Windows Server 2008/Windows Vista
KVM &#8211; Virtualization software

```

> 
If you have access to an Ubuntu install, then the best way to make a USB disk is to download an Ubuntu .iso from [www.ubuntu.com](www.ubuntu.com) and use the 'USB Startup Disk Creator' program under System > Administration.

I can't find 'USB Startup Disk Creator' on a Ubuntu 8.04 workstation.  I can mount the USB stick on terminal and run wget to download the iso.image on the stick.  Can it work?

> 
UNetBootin I think is another way to make a USB disk and is also available under windows if you only have use of a windows install. This program also downloads the .iso automatically for you if you like.
The new HD is empty.


Edit:

Now I have ubuntu-9.04-desktop-i386.iso download on an Ubuntu desktop PC. Can I copy it on an USB stick starting installation on another PC with new HD installed? The PC has boot USB function.


B.R.
satimis

---

### Post by themusicalduck on 2009-05-26
I'm not sure of the availability for the USB startup disk creator on 8.04, but have a look for it on Add/Remove on the 8.04 station and it might be there. It's the easiest program to use for making a USB install disk in my experience.

If it isn't there then UNetbootin probably will be. UNetbootin is basically the same program but with a few more features. You should be able to make the USB disk on the 8.04 station using this program if startup disk creator isn't available. Both programs let you load a .iso file and then select a connected USB disk to load the installer onto. You should backup any files on the USB disk first in case it gets reformatted or files are deleted.

While it is possible to just copy the contents of a CD to the USB disk, the USB disk needs to be properly formatted and readied for booting, which these programs should do automatically and so is probably the easiest method.

> I can mount the USB stick on terminal and run wget to download the iso.image on the stick. Can it work?


This wouldn't work as it would only copy the iso image file and not the actual installer onto the disk.

Hope this helps.

EDIT: Your original post is a little vague, but I'm assuming you simply want to install Ubuntu on a desktop PC using a USB disk right? I'm not sure what you mean by 'on a new HD with net installation' but these steps should work to just install Ubuntu onto a new PC.

---

### Post by satimis on 2009-05-26
> **themusicalduck said:**
> I'm not sure of the availability for the USB startup disk creator on 8.04, but have a look for it on Add/Remove on the 8.04 station and it might be there. It's the easiest program to use for making a USB install disk in my experience.

If it isn't there then UNetbootin probably will be. UNetbootin is basically the same program but with a few more features. You should be able to make the USB disk on the 8.04 station using this program if startup disk creator isn't available. Both programs let you load a .iso file and then select a connected USB disk to load the installer onto. You should backup any files on the USB disk first in case it gets reformatted or files are deleted.

While it is possible to just copy the contents of a CD to the USB disk, the USB disk needs to be properly formatted and readied for booting, which these programs should do automatically and so is probably the easiest method.



This wouldn't work as it would only copy the iso image file and not the actual installer onto the disk.

Hope this helps.

EDIT: Your original post is a little vague, but I'm assuming you simply want to install Ubuntu on a desktop PC using a USB disk right? I'm not sure what you mean by 'on a new HD with net installation' but these steps should work to just install Ubuntu onto a new PC.
Hi themusicalduck and folks,


Thanks for your advice.

With an iso image in hand it would be much easier for me to burn  a CD installer rather than following the steps described on following URL;

Install Ubuntu from a USB stick
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


I did netboot installation several years ago with only a bootable floppy, now with an USB stick.  Unfortunately I forgot the steps.  It was rather simple only downloading a small image on Internet.

Now I have the CD installer ready for installing Ubuntu 9.04.

Anyway thanks again for your assistance.


B.R.
satimis

---

