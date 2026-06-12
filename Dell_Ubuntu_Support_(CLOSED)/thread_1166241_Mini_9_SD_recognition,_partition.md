---
title: "Mini 9 SD recognition, partition?"
date: 2009-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rallg on 2009-05-21
I have a mini 9 with Ubuntu 9.04 (regular release, not remix) and the latest BIOS update (A05).

Recently I obtained a new 16G class 6 SD card. I have not previously used the card slot on this computer. Sometimes, when I insert the card, it mounts. Other times, it is unrecognized and cannot be mounted. I wonder if I have a hardware problem (could be as simple as dirt in the slot), or if others are having this problem?

When I am able to mount the card, it is unrecognized in the partition manager (Gparted). Is this behavior normal? I have not had any problem with (say) partitioning USB pendrives.

---

### Post by jaqrah on 2009-05-21
Rallg, I can't help you with your problem but I have a question for you.  In my dell mini 9 literature that came with the netbook, it mentioned there was supposed to be a plastic insert that fit into the sd slot to help keep out dirt and other debris. It mentions this on page 17 of the Inspiron set up guide (it is green and white) American version. I did not get one of these plastic inserts.  I wonder if you or anybody else did?  It sure would help keep crap out of that huge slot.  I ask because one of your concerns was dirt in the slot.

---

### Post by anjilslaire on 2009-05-21
My mini 9 does not have a plastic insert, but myy 1420 came with one.

---

### Post by Rallg on 2009-05-23
I do not know whether a dummy card was there when the machine was new.

---

### Post by Blue Sassley on 2009-05-24
Rallg, I'm in the same boat as you, I just bought a 16GB SDHC Class 6 card and can't seem to get Ubuntu Netbook Remix 9.04 to read it in anyway' not even in Gparted.

I have found a post on the My Dell Mini forums of people talking about using SDHC cards in there Mini's:

[http://www.mydellmini.com/forum/dell-mini-9-discussion/8463-question-about-minis-sdhc-capabilities.html#post69798](http://www.mydellmini.com/forum/dell-mini-9-discussion/8463-question-about-minis-sdhc-capabilities.html#post69798)


Blue

---

### Post by lswartz on 2009-05-24
Does it mount if you install before you start up your computer? Mine always mounts. If I install after booting I have to right click & mount it, but  that has always worked. I normally just leave it in the slot all the time anyhow.

16 GB OCZ SDHC
Hardy 8.04

---

### Post by Blue Sassley on 2009-05-25
I can't see my SD card at all, it never shows up, but I can put in a way smaller normal CD card and see that one just fine.

Blue

---

### Post by jimrz on 2009-05-25
> **jaqrah said:**
> Rallg, I can't help you with your problem but I have a question for you.  In my dell mini 9 literature that came with the netbook, it mentioned there was supposed to be a plastic insert that fit into the sd slot to help keep out dirt and other debris. It mentions this on page 17 of the Inspiron set up guide (it is green and white) American version. I did not get one of these plastic inserts.  I wonder if you or anybody else did?  It sure would help keep crap out of that huge slot.  I ask because one of your concerns was dirt in the slot.

my vostro a90 (same as mini 9 but from the small biz section) did come with the plastic insert

---

### Post by The Jinx on 2009-05-25
> **jimrz said:**
> my vostro a90 (same as mini 9 but from the small biz section) did come with the plastic insert

Ditto, I am also running a 4gb Class 2 SDHC card as well with no problems

---

### Post by james_xxx on 2009-05-26
I am also having issues using a generic (adata) 2GB SD card in my Mini 9, using Jaunty. 

A friend had recently told me that an SD card in his Mini 9 appeared to have become corrupted, and he believed that it had happened when the Mini 9 went into 'suspend', upon closing the lid. His was formatted to Fat 16 or 32.

I recently purchased the SD card I mentioned above, and with the problem this friend had experienced in mind, I decided to reformat mine to a Linux file system, and chose Ext4. I installed and fired-up gparted, and I thought it was interesting when I discovered that it could not see the SD card. I wound up having to format it using 'mkfs'. 

Aftewards, I moved a video and some music files to the SD card, and just left it inserted in the Mini for a day or so. Some time later, after a reboot or two, I tried to access the SD card, and it has ever since told me that it cannot be mounted.

There is some kind of issue here, and it would good to figure out how the problem can be addressed. 

Is this similar to what others are experiencing?

---

### Post by Blue Sassley on 2009-05-26
Here is what I am seeing every time I insert my 16GB SDHC card

```
blue@MINI9:~$ dmesg | tail
[   29.450574] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   31.510800] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   81.052158] usb 5-1: new full speed USB device using uhci_hcd and address 2
[   81.224308] usb 5-1: configuration #1 chosen from 1 choice
[   81.282666] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   81.286551] usbcore: registered new interface driver btusb
[   83.467977] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   83.472279] input: Microsoft Bluetooth Notebook Mouse 5000 as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/bluetooth/hci0/hci0:11/input9
[   83.485579] generic-bluetooth 0005:045E:0700.0001: input,hidraw0: BLUETOOTH HID v1.00 Mouse [Microsoft Bluetooth Notebook Mouse 5000] on 00:22:69:CA:40:B2
[  738.195439] [COLOR="Red"]mmc0: error -84 whilst initialising SD card[/COLOR]

```

Blue

---

### Post by armandh on 2009-05-27
Kingston 4 Gb formated Fat 32 in mini-9 original bios

appears on desktop as 4.0 GB Media with an SD card Icon

works every time

mounts on start up
un-mounts from right click menu
mounts when inserted

contents window appears after hibernation or suspend

---

### Post by Blue Sassley on 2009-08-02
I have found the issue to fix the SD card issue in my Mini 9 you might want to try it out:

[http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html](http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html)

> Next, there is a known issue with the SD card readers stemming from Jaunty's version of the Linux kernel that causes the left reader to fail with this error:

    mmc0: error -84 whilst initialising SD card

The left-side SD reader is otherwise not acknowledged, i.e. it doesn't create a /dev/ entry when cards are inserted and hotplug doesn't mount the disk (this problem also exists on the Dell Mini 9, so you guys can benefit from this too). To correct the situation, type into a terminal:

    sudo gedit /etc/modprobe.d/options

and add (be wary of line breaks; I recommend copy/pasting instead of manually typing):

    options sdhci debug_quirks=1

    ProblemType: Bug
    Architecture: i386
    DistroRelease: Ubuntu 9.04
    Package: linux-image-2.6.28-6-generic 2.6.28-6.17
    ProcCmdLine: User Name=UUID=e309fb14-05db-4e9a-b137-c6bf63eeb6a4 ro quiet splash elevator=noop
    ProcEnviron:
    SHELL=/bin/bash
    LANG=it_IT.UTF-8
    ProcVersionSignature: Ubuntu 2.6.28-6.17-generic
    SourcePackage: linux

Reboot and most everything should work properly, hotplugging and all. Also to be aware of, the right-side reader does not work properly if there is not a card in it at boot. In this case, it won't show any trace anywhere that you even have a right-side reader.

For both of these fixes, all we've done is created a text file that the system loads as it boots. If you wish to undo these fixes, you can just delete the text files and it'll go back to normal.
Thanks,
Blue

---

