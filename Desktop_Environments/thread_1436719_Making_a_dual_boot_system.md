---
title: "Making a dual boot system"
date: 2010-03-23
forum: Desktop Environments
---

### Post by mickelsen on 2010-03-23
I have a Ubuntu system running ver. 8.04.0. I have added a second hard disk to the system and I would like to make it into a dual boot system with Ubuntu and Windows XP. I would like XP to occupy the second disk. Can someone tell me where to look to find instruction and help to do this? I'm not too far down the road on my Linux system so I could start over from scratch if I had to.
Anyway, if you could help me, I would really appreciate it because I don't even know where to start.
Thanks,
Mark

---

### Post by TitanusEramius on 2010-03-23
Well, depending on your hardware-setup it might not be that hard to do. In short it would look like this:

Set BIOS to boot from CD
Boot up, and start, the WinXP installation from the CD
Make sure WinXP goes on the right disk
Restart into Ubuntu when WinXP is installed (if Ubuntu still boots)
Update GRUB

One problem there can happen here is if WinXP overwrites GRUB, but this can be fixed if you are using the Ubuntu-cd as a live-cd.

This explains the last part:
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

Good luck :)

---

### Post by pricetech on 2010-03-23
Start by deciding whether you want to put XP on the second disk by itself and use your BIOS to determine which drive to boot.  (assuming your BIOS will allow such an option, some do some don't)

Otherwise, since you said you don't mind reinstalling Ubuntu, set your second drive up as your primary master and install XP on it, then hook the original drive up as a secondary master and install Ubuntu.  The install process will find XP on the first drive and make an option for it in the bootloader.

You'll have to put XP on the system's first drive either way since Windows has never to my knowledge been very cooperative if installed anywhere else.

---

### Post by sixdrift on 2010-03-23
I agree with pricetech. I think your heading for a Windows nightmare if you try to force Windows to do something different. If you don't mind reinstalling, then start by installing Windows on the first drive/partition. Once that is on and stable, then boot the live CD and then either carve out a partition on the first drive, or use a second drive, and install Ubuntu there. 

In general you will be happier (and done a lot sooner) if you install Windows first and then install Linux as the dual boot.

---

### Post by mickelsen on 2010-03-24
Thanks for the guidance. I'm going the way of Windows first and then Linux. Since my second disk was the system disk for my previous XP system, all I had to do was repair it to bring up the XP system with all the previous files in place. The hardware box has a wireless LAN card in it and the XP system came right up on the LAN just as it was working before. I am able to boot Ubuntu using the LiveCD disk, but I can't get it to come up on the Internet. Obviously, the LAN hardware is working since it works for the XP side. So now I need to get the documentation on how to get Ubuntu to connect to the Internet. I'm sure it's here on this site somewhere.
Thanks for all your help.
Mark

---

### Post by mickelsen on 2010-03-25
I was really hoping that someone would post a reply about how to get my system up and running on the Internet.  I'm having no luck at all.
I have a Linksys wireless LAN card, a WMP54GS v1.1.  It is working just fine when my system is running Windows XP.  I'm hoping that it is just a matter of finding a list of instructions that I can follow to install the driver and get it working with Linux.
Anyone that can help, please reply.
Thanks,
Mark

---

### Post by mickelsen on 2010-03-31
I've got my system dual booting just fine now.  But I would like to change one thing.  When the system is first reset, it comes up with a list of about five different things that I can boot to.  Is there a way that I can edit or rearrange that list?  I would like to put Windows at the top so that if nothing happens, it is the default system that it boots to.  Is this possible?
Thanks again,
Mark

---

