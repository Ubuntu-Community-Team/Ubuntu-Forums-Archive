---
title: "I don't find the usb-serial.h????help!!!!!!!!!!!!!!!"
date: 2009-04-21
forum: General Help
---

### Post by spiceoflife on 2009-04-21
Hello!!!

I'm trying to install the ti_usb_3410_5052 driver but when i try to compile this driver the following error shows up:

configure: error: cannot find usb-serial.h in kernel sources

So how could i resolve this problem??????????????

---

### Post by Wayne_V on 2009-04-21
> $ git log -p a969888ce91673c7f4b86520d851a6f0d5a5fa7d
commit a969888ce91673c7f4b86520d851a6f0d5a5fa7d
Author: Greg Kroah-Hartman <gregkh at suse.de>
Date:   Tue Jul 11 21:22:58 2006 -0700
 
    [PATCH] USB: move usb-serial.h to include/linux/usb/
 
    USB serial outside of the kernel tree can not build properly due to
    usb-serial.h being buried down in the source tree.  This patch moves the
    location of the file to include/linux/usb and fixes up all of the usb
    serial drivers to handle the move properly.

The driver source you have must be pretty old -- is there anything newer?   Does usbserial.ko already support your hardware?

---

### Post by Wayne_V on 2009-04-21
See this post: [http://ubuntuforums.org/showthread.php?t=979460](http://ubuntuforums.org/showthread.php?t=979460)

---

### Post by spiceoflife on 2009-04-22
hello!
my problem is that how to include the usb_serial.h into my kernel ubuntu 8.10!!

---

### Post by 3rdalbum on 2009-04-22
> **spiceoflife said:**
> hello!
my problem is that how to include the usb_serial.h into my kernel ubuntu 8.10!!

Did you try putting the firmware into the directory specified in the linked thread and then plugging in the device? If not, then TRY IT NOW. Chances are that there is a perfectly good driver already in-kernel that is just waiting for the device's firmware file.

---

### Post by spiceoflife on 2009-04-22
I putted the firmware but nothing new.this what i get:

zina@zina-laptop:~/Bureau/newnewnew/ti_usb_2.6-1.0$ ./configure --prefix=/home/zina/usb/

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking os type... ok
checking kernel version... 2.6.27-11-generic
checking kernel sources... found /lib/modules/2.6.27-11-generic/build
checking usb-serial.h... not found
configure: error: cannot find usb-serial.h in kernel sources


zina@zina-laptop:~/Bureau/newnewnew/ti_usb_2.6-1.0$ dmesg

[  783.940208] usb 3-1: new full speed USB device using uhci_hcd and address 3
[  784.131215] usb 3-1: configuration #1 chosen from 1 choice
[  810.136220] usb 3-1: USB disconnect, address 3
[  979.216183] usb 3-1: new full speed USB device using uhci_hcd and address 4
[  979.407226] usb 3-1: configuration #1 chosen from 1 choice

---

### Post by lnarasimhan on 2010-01-01
hello,

 git log -p a969888ce91673c7f4b86520d851a6f0d5a5fa7d

 when i try to do this i get an error saying that "Not a git repositry".  I am not finding a straight way to locate the usb-serial.h file in ubuntu. I am unable to install the ti_usb_3410_5052.ko module due to this. Please some one help me in locating this file. I am using ubuntu 8.10 and kernel version is 2.6.27.16

---

