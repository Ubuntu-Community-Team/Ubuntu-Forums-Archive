---
title: "Few questions about Live USB installation"
date: 2009-03-09
forum: General Help
---

### Post by TnTonly on 2009-03-09
Well, I have make a Ubuntu Live USB disk using "Create a USB startup disk" options. But I have a few questions

1. My computer uses a NVIDIA graphic driver that couldn't turn on at start up. Each time I login, I have to Activate the driver and Ctrl + Alt + Backspace to take effect. Should I do something so that I don't have to do that again and again?

2. I just want to ask, if I make few modification on that Ubuntu USB, such as install some applications, change theme..., will that available on my PC after installing if I choose Install on desktop?

---

### Post by C.S.Cameron on 2009-03-09
1) Depending on how much disk space you have allowed for persistence, Nvidia drivers installed using System/Administration/Hardware Drivers should be persistent.
2) Modifications will not be included if the disk is used to install Ubuntu. But you can save the debs to the disk and install the applications separately.

---

### Post by TnTonly on 2009-03-09
> **C.S.Cameron said:**
> 1) Depending on how much disk space you have allowed for persistence, Nvidia drivers installed using System/Administration/Hardware Drivers should be persistent.


For me it isn't, and I don't know why. I'm pretty sure that I have enough disk space allowed for persistence, and everything else except NVIDIA drivers remain as it was when I reboot. In fact, the problem is I only have to install NVIDIA driver only once. The second time forth I only have to Activate it. It's not activated by default, and the problem is after activating it, I have to restart the X server to take effect, which takes a while.

---

### Post by TnTonly on 2009-03-10
Anyone can help?

---

### Post by TnTonly on 2009-03-10
Eh... One more question, I want to make a bootable DVD exactly exactly the same as my Ubuntu on USB (Ofcourse I can't make it persistence like my USB), how can I do that?

---

### Post by TnTonly on 2009-03-12
Noone answers? :(

Another question, I've made pretty much changes on my USB Ubuntu, and now I want to increase the casper-rw file to have extra space WITHOUT losing my old data, how could I do that?

---

### Post by C.S.Cameron on 2009-03-12
I think I was wrong about Nvidia drivers being persistent on a Live CD disk image persistent install.
They work ok when Ubuntu is installed using the install utility from the Live CD.
I'm not sure how to clone from a flash drive to a Live CD but it sounds like it should be possible. You can clone to a second flash drive using "sudo dd if=/dev/sda of=/dev/sdb"
You can create an ext3 partition, (using gparted), and label it casper-rw and then copy the data from the casper-rw file to this partition. This partition can then be expanded as required.

---

### Post by TnTonly on 2009-03-12
Thank you, I'm much appreciate ^^ Actually I still don't know how to "copy the data from the casper-rw file to this partition", but I guess I will figure out a way.

---

### Post by TnTonly on 2009-04-24
Same issue, new problem. 

Because of xorg.conf is not persistence, but created everytime boot on USB, so I have to Activate the driver and Alt + Ctrl + Backspace. 

But know, they disable Alt + Ctrl + Backspace in Ubuntu 9.04, which is only enable by modify xorg.conf, which is not modifiable. How the hell could I activate my driver?

P/S: I have tried gdm restart but no luck.

---

