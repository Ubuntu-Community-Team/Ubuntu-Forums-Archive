---
title: "Bootable USB with Ubuntu 10.04 refuses to install"
date: 2011-09-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RSASKA on 2011-09-10
[SIZE=3]Hello,

Currently have Ubuntu 9.04 on Dell 1545

Attempted to create bootable USB with Ubuntu 10.04 so I can do I clean install. In the past, I tried to upgrade from 9.04 to 9.10, but the screen would get frozen after the installation.

TO create the bootable USB, I did the following[/SIZE]

[SIZE=3]* Downloaded Ubuntu 10.04 ISO
* System > Administration > USB Startup Disk Creator

Once I created the disk, I rebooted the laptop, and the Purple screen with "Ubuntu" appears momentarily. Then, the screen goes blank forever. 

Tried few more attempts.

I want to install Ubuntu 10.04 on Dell 1545, and all I have is USB. 

Please help!!!!!!!!!!! 
[/SIZE]

---

### Post by mue.de on 2011-09-11
There's some trouble with nvidia graphics chipset, you'll find a lot postings regarding that problem
Does your machine uses it?

mue.de

---

### Post by RSASKA on 2011-09-11
> **mue.de said:**
> There's some trouble with nvidia graphics chipset, you'll find a lot postings regarding that problem



How do I find out whether my laptop uses nvidia graphics chipset. This is a Dell 1545 running Ubuntu 9.04.

---

### Post by RSASKA on 2011-09-11
[SIZE=3]I attempted to create bootable USB with 11.04 twice and evertime at startup I get a black screen that says something along the lines of

configuration file cannot find keyword
boot:

Are there any drivers I need to install in order for this to work?[/SIZE]

---

### Post by garolou on 2011-12-12
Did you ever manage to do an install using the usb key?

to get past the 'boot:' prompt issue....(for 10.04 at least) type 'help' and press enter. This will raise the menu. Pressing enter again will launch the default install.

Hopefully that is enough to resolve your problem. In my case however, the install is looking for a cd-rom. I would try to fool it to look again at the usb drive it is running from, but it is not listed in the /dev directory.

Has anyone ever managed to install a 10.04 server with a usb drive only? I have done it with a CD install and will do so if I am forced to, but would rather not have to break open a box and start moving hardware around to be able to install software.

---

### Post by RSASKA on 2011-12-18
> **garolou said:**
> Did you ever manage to do an install using the usb key?
...
Has anyone ever managed to install a 10.04 server with a usb drive only? I have done it with a CD install and will do so if I am forced to, but would rather not have to break open a box and start moving hardware around to be able to install software.


I ended up doing the following.


[LIST=1]
[*]Get 16 GB USB
[*]Follow directions from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
[*]Use Windows OS to format the 16 GB USB in FAT32
[*]Burn Ubuntu ISO onto USB
[/LIST]

After these steps, I was able to boot the laptop with this USB and install 11.04

i believe the trick was going onto a Windows computer to format the USB in FAT 32 rather than Ubuntu.

---

