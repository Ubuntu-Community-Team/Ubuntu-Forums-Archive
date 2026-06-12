---
title: "Ubuntu on Dell Mini 10"
date: 2010-02-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lupodellasleppa on 2010-02-19
Hi all, I'm new to the forum, and new to Ubuntu
First of all, sorry if there's any post wich already solves this problem, I'd be very glad if somebody could address that to me, but I've been searching over and over without any result.
My problem is: I've bought a Dell Mini10 last summer with Ubuntu Hardy, Dell version, already installed on it, and I'm trying to get a standard Ubuntu distribution installed, possibly upgraded. Fact is, I've read about lots of people who did it but none of them described how they did. So I've started to find out a solution myself, but my little expericend brought me to no results: I've downloaded UNR 9.10, installed usb-creator, plugged my USB drive, made it a bootable drive, restarted the computer booting from the USB drive, and all I got was a blinking white undescore on a black screen; so I tried repeating the process with many other distros and they all ended up in the same little undersore, the blinking one. Then I found out that Ubuntu 8.04's got some problems with usb-creator, sometimes it doesn't work out really well. So I created a bootable drive with UNetbootin on a PC and used that on the Dell Mini and I finally got in an Ubuntu installation process. But all my hopes went gone once again when I understood the process was going kinda weird and leading o nowhere.
Now, after been looking everywhere for months without finding anything useful and trying anything my non-experienced mind could think about, I'm really tired and asking for help in first person to find a way to install a standard Ubuntu distro without the use of an external CD reader (wich I don't have).
Thanks for any help, and sorry if my english's not perfect.

---

### Post by snowpine on 2010-02-19
The Dell Mini 10 has a GMA500 graphics card, which is not well supported by most Linux versions out-of-the-box. Read through this thread and decide if it's something you're comfortable trying: 

[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

If that sounds like it is over your head, I would recommend sticking with the factory pre-installed 8.04, which includes all necessary drivers and will be fully supported through April 2011. Good luck either way!

---

### Post by lupodellasleppa on 2010-02-19
Yes I think I can take it, but I need to upgrade to a standard 9.10 first :D thanks a lot anyway

---

### Post by kio_http on 2010-02-19
Use unetbootin rather than usb creator, it will be much easier. Take the generic option don't choose distribution as ubuntu.

---

### Post by mikewhatever on 2010-02-19
You'll have to deal with low resolution mode during the installation. When done, install the driver by running the poulsbo.sh script with sudo.

```
wget [http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh](http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh)
```

For more info:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

