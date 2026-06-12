---
title: "booting ubuntu from physical disk in vmware"
date: 2006-09-20
forum: Desktop Environments
---

### Post by baumer1122 on 2006-09-20
So I'm stuck using Windows at work, no way around it. My laptop is dual-boot at least and I'd like to try to get VMWare to run off the physical disk so I can use Ubuntu via VMWare in Windows. Is this possible?

So far, it loads grub, but after that it can't mount the root partition. It shows /dev/hda1-5, but none of them work. Is there any chance of getting this to work?

---

### Post by heffo_j on 2006-09-21
Hi there,
I recentl;y read somewhere that someone did the reverse, i.e. fired up XP partition under Ubuntu/VMware host.

Try the vmware forums. They don't answer questions much though - lots of posts unanswered. I'm sure I saw something there. Try searching their forum.

The easiest way to ger Ubuntu to work though ist he download the browser appliance. It is Firefox in Ubuntu 5.10 (or was last time I looked). 

Regards
John

---

### Post by sefs on 2006-09-21
It indeed works well.  I installed xubuntu 6.06 onto vmware server in windows, and it went just like a normal installation.   I am not sure why yours is not working...but just to let you know that it actually works.

The steps I followed to installed were nothing fancy just the basic follow the wizard excepting all defaults ect.

How though did you get so many disk drives showing up in your installation.

---

### Post by pod25 on 2006-09-21
> **baumer1122 said:**
> So I'm stuck using Windows at work, no way around it. My laptop is dual-boot at least and I'd like to try to get VMWare to run off the physical disk so I can use Ubuntu via VMWare in Windows. Is this possible?

So far, it loads grub, but after that it can't mount the root partition. It shows /dev/hda1-5, but none of them work. Is there any chance of getting this to work?

I got it to work doing the reverse, installed vmware onto ubuntu then installed xp pro into vmware, works like a charm. Though I only use it to network my printer.

Try this link [How to install vmware onto ubuntu]("http://www.ubuntuforums.org/showthread.php?t=183209")

---

