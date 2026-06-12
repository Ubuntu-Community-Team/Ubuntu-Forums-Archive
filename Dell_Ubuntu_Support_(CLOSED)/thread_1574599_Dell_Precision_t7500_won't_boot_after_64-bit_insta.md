---
title: "Dell Precision t7500 won't boot after 64-bit installation"
date: 2010-09-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by l0uismustdie on 2010-09-14
Hello I just installed Ubuntu 10.04 64-bit on a Dell Precision T7500 and now upon reboot I am faced with a screen that says
```

Searching for devices at HBA 0...
HBA     ID     LUN     VENDOR     PRODUCT               REVISION    CAPACITY
0         0      0   ATA            WDC WD100FAES-7  1D05         931 GB
0                   LSILogic     SAS1068E-IR          0.25.47.00    NV 2D:09
Dell Inc. MPT boot ROM successfully installed

```Then the machine hangs here indefinitely.  Any ideas?

---

### Post by l0uismustdie on 2010-09-17
Just a little bump.  I reinstalled Ubuntu again and this didn't solve anything.  Anyone out there?

---

### Post by ptptaylor on 2010-09-18
I'm not entirely sure what the problem is, but it could be fixed with a grub update.
Insert the live CD you installed with, and try without installing. 
Go into a terminal (ctrl alt t) and type "sudo update-grub" .

---

### Post by l0uismustdie on 2010-09-21
Thanks for replying.  The problem is that the system isn't booting but rather hanging at the screen I posted originally.  I tried your suggestion but this didn't seem to have any effect and upon reboot it is still hanging on the same screen indefinitely.

---

### Post by ojiving on 2010-09-27
Did you ever find a solution? I'm having the same problem...

---

### Post by l0uismustdie on 2010-09-28
I think I have located the problem in that the HD (sdf1) isn't bootable.  However, I haven't been able to install Ubuntu with the HD in a bootable state.  I have tried to format the drive, to be bootable, after an install but this seems to fail.

---

### Post by ojiving on 2010-09-28
At some point I thought that was my problem. But I just did a fresh install, and now when I use the live c.d. and type "sudo fdisk =l", it shows /dev/sda1 as being bootable...

---

### Post by ojiving on 2010-09-28
I'm wondering if this could be hardware RAID vs. software RAID problem. If I understand correctly, ubuntu is installing with dmraid included, which I believe is for software RAID. I'm pretty sure that I have hardware RAID. I'm trying a fresh install with the nodmraid option selected. I'll keep you posted...

---

### Post by ojiving on 2010-09-28
With a little bit of help from my tech support I've found the fix. I had to change the grub file (hold down shift while booting, then when you get the grub screen press e). I added "rootdelay=60 nomodeset" to the line "GRUB_CMDLINE_LINUX_DEFAULT quiet splash"  .

The rootdelay problem was that the computer is a bit slow too boot. nomodeset has to do with the nvidia graphics card. Not sure if it will work for you as well.. (As with much of linux, I don't really understand why it works, it just does.)

For more details, see: [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by l0uismustdie on 2010-10-17
So, I tried your solution but didn't have any success.  My solution was installing 10.10 which works.

---

### Post by Le loup on 2011-04-07
Hello l0uismustdie,

Did you install the Ubuntu 10.10 Desktop 64bit onto your Dellt7500? and what is your maximum amout of memory you've added into it? Thanks

---

### Post by allure on 2011-12-20
If I may provide a solution for 10.04:
A customer had this exact problem after installing Ubuntu 10.04 and we tried a bunch of things but one thing I know that is a specific issue on the Dell T7500 is the SAS Controller on the motherboard.
I know this isn't exactly a Linux solution, but it is a Linux issue (incompatibility with the SAS Controller, I think).
Bypass the SAS Controller and the problem goes away:

[LIST]
[*]Open the case, find the SATA cable going from the hard disk into the motherboard, I expect it goes into a SAS-controlled SATA port. Unplug it and plug it into the SATA0 port nearby - the SATA ribbon might be too short, so either get a longer one or move the HDD into the next bay. The DVD drive might be in SATA0, so put the DVD drive cable into SATA1.
[*]Boot into the BIOS and disable the SAS Controller and enable drives: SATA0 and SATA1.
[/LIST]

Now it should boot :]

---

### Post by geokarako on 2012-04-24
I tried what you suggested and it still didn't boot. But not only that... I also couldn't make bios "see" the hard drives I had connected to the SATA 0 and 1. Do you have any suggestions or any tricks to tell me about that? Thank you very much in advance!

---

