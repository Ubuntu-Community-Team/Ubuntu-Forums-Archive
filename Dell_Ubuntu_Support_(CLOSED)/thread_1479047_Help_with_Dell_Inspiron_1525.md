---
title: "Help with Dell Inspiron 1525"
date: 2010-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Woolio1 on 2010-05-10
My friend has a Dell Inspiron 1525. Everything works except for the wireless. I'm not sure which card it has, but LSPCI in the terminal returned a Broadcom BCM4312 card. 

Does anyone know how to get the firmware and drivers?

It's on Ubuntu 10.04, if that means anything.

---

### Post by OooBuntuRox on 2010-05-10
Try this:  system>Administrator>Hardware drivers. Two will probably come up. I use the sts in a 1545 it's the proprietary driver. I don't recall the other but I believe bot are for broadcom half/ mini cards.

OooBuntuRox:guitar:

---

### Post by xboxSlayer on 2010-05-12
Thanks, selected Broadcom STA wireless driver and everything works great.

---

### Post by OooBuntuRox on 2010-05-13
[SIZE=3]
I'm glad is was that simple for you and nothing more serious. So far, I  seem to be having better WiFi performance with 10.04 than with 9.04  (Overall, I didn't like 9.10 and stuck with 9.04).

remember to mark your question as solved.

take care, OooBuntuRox[/SIZE]   :guitar:

---

### Post by zoftware on 2010-05-13
How did you guys install 10.04 on the Inspiron?

We have been trying to instal the ubuntu-10.04-desktop-i386.iso

It is not working. We keep getting an I/O error.

Is there a different download?

Trying to escape MS.

Thanks

---

### Post by OooBuntuRox on 2010-05-17
> **zoftware said:**
> How did you guys install 10.04 on the Inspiron?

We have been trying to instal the ubuntu-10.04-desktop-i386.iso

It is not working. We keep getting an I/O error.

Is there a different download?

Trying to escape MS.

Thanks

I tried both the i386 and the 64 bit. Both worked for me. Although I did have more lock ups with 64 bit. The boot would freeze as the system panel was about to load. I found some info on updating grub. Once I did that it seems to be working fine.

Be very sure you  do a total HD MS backup in case you want to back out for any reason. You may never find your drivers again should you need them.

Also, I tried the generic 32 bit and the dell ISO. I like the generic better. I think the dell ISO is moblin. It has huge icons on the desktop and a Dell ELU that you have to agree to. I didn't like either caviot. Also, it doesn't let you modify the desktop.

Anyway, once you burned your iso image properly to DVD (it won't fit on a cd, it's a 1 g file), put it in your dvd drive and reboot. It pretty much does the rest. If you keep failing on dvd, do the test boot and make a bootable USB drive. I believe you can still do an install to HD from a USB drive.

If everything on your system works properly and you still can't install, you probably have to set the disk boot order in your bios. Put the dvd and usb before your hd on the drive list.

I assume that you are doing a fresh install and NOT trying to install through windows. If you are installing through windows, you're on your own. I haven't done it. If you do a backup before ubuntu install, you can make a dual boot system too after you re-partition your hd.

Try that and see how it goes.

[SIZE=3]Also, Follow these links and poke around:

[http://linux.dell.com/files/ubuntu/](http://linux.dell.com/files/ubuntu/)

[http://linux.dell.com/files/ubuntu/lucid/iso-images/](http://linux.dell.com/files/ubuntu/lucid/iso-images/)

[http://en.community.dell.com/support...overy-iso.aspx]("http://en.community.dell.com/support-forums/software-os/w/linux/ubuntu-9-04-dell-factory-recovery-iso.aspx")

[http://en.community.dell.com/support...overy-iso.aspx]("http://en.community.dell.com/support-forums/software-os/w/linux/ubuntu-8-04-dell-factory-recovery-iso.aspx")
[/SIZE]
OooBuntuRox :guitar:

---

