---
title: "Ubuntu 12.04 lts very slow to boot to desktop"
date: 2013-11-02
forum: Desktop Environments
---

### Post by mmcl26554 on 2013-11-02
I have a Gateway GZ7112 all in one computer.  I have Ubuntu 12.04lts and Vista each installed on their own drive.  I tried to install it as a dual boot but Grub would never boot Vista so I gave up on that.  I select which OS to boot with the F10 boot menu. When I select Ubuntu it will take a full 3 minutes to boot to the desktop.   I have no idea why this is so.   So I am looking for some help.
Michael

UPDATE:
I have another computer an HP model a367c it has a Pentium 4 2.4 GHz with 2 Gb or ram and running the exact same OS (Vista Ultimate) loaded from the same disk. I just loaded Ubuntu 12.04 lts and It works just great Grub will boot both OS and Ubuntu boots faster than Vista, just like it should.   So there is something about the Gateway that is not Linux friendly, sure wish I could figure out what it is.  I see there are a lot of info on the internet for slow boot so it is not an uncommon problem.  I'll do more research and try some of those fixes while I wait for a response here.

---

### Post by mmcl26554 on 2013-11-09
The attachment is boot chart for this computer.  I really don't understand what it means so could someone decipher it for me. 
Thanks
Michael

---

### Post by oldfred on 2013-11-09
I do not know how to read a boot chart and as an attachment it is too tiny to read.

But I do review log files for errors, repeated attempts to load something and either later sucess or failure or very long times between entries.
You can use log file view that is in some versions or :
       gksudo gedit /var/log/dmesg

There are many log files so you may want to review others also.

---

### Post by mmcl26554 on 2013-11-10
Fred,
 Yes it is rather small in it's present form but when you load it with a graphics program you can expand it so it is readable.   That's is what I had to do.  
I have looked at the dmesg log but I don't understand what it means.   Would you like me to copy and post the whole log or just attach the file?
Michael

---

### Post by oldfred on 2013-11-10
Better to to show the few lines with errors or longer times between entries in code tags. You can easily add code tags with # in advance editor. I use quote in quick reply and manual edit quote to code.

I boot with an SSD and it shows total boot time of 8.6. But my BIOS & grub take at least 15 sec.
This is the "long" time entry I have: :)
```
[    3.757998] usbhid: USB HID core driver
[    4.600116] EXT4-fs (sde3): mounted filesystem with ordered data mode. Opts: (null)
[    7.057454] Adding 3076412k swap on /dev/sdd11.  Priority:-1 extents:1 across:3076412k 

```

---

### Post by mmcl26554 on 2013-11-10
I can do what you ask.   However, I think the problem area doesn't show up on this log.   Since it takes a full 3 minutes from selecting the drive to boot from to desktop (I have it login automatically).   If I read the log correctly the number to the left of the (.) is seconds.   The max number I see there is 96 which is a minute and one half.  So what happened to the other 1.5 minutes?    But I will cut out the times longer than 10 seconds and post them.    I will also see if the "Boot chart" people can give me some incite to their program.
Michael

---

### Post by oldfred on 2013-11-10
With my system BIOS takes about 12 sec and grub 3 or 4. So are either of them very slow?
New UEFI systems boot thru UEFI very quickly.

---

### Post by mmcl26554 on 2013-11-10
After I select the drive with Ubuntu the screen turns black with only a flashing (-) in the upper left corner for about 90 seconds, then the screen turns purple for another 90 seconds then the desktop comes up and all is well after that.
Michael

---

### Post by oldfred on 2013-11-10
From grub menu remove splash quiet so you can see boot process. You may need another boot parameter?
What BIOS setting do you have for the hard drives? AHCI or large, not IDE nor RAID?

---

### Post by mmcl26554 on 2013-11-11
Fred,
I changed to the bios setting to AHCI but it took amybe 30 seconds longer to boot to the desktop
I also removed splash quiet but I didn't see nay thing that would be a problem, but then I don't really know what I am looking for. and it took 3 minutes to get to the screen where this data showed up during boot up.
Here is what I copied with dmesg:
[PHP][   24.880943] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   29.010589] wlan0: authenticate with 00:24:a5:c8:3c:df
[   29.027821] wlan0: send auth to 00:24:a5:c8:3c:df (try 1/3)
[   29.029620] wlan0: authenticated
[   29.032069] wlan0: associate with 00:24:a5:c8:3c:df (try 1/3)
[   29.036110] wlan0: RX AssocResp from 00:24:a5:c8:3c:df (capab=0x431 status=0 aid=7)
[   29.065135] wlan0: associated
[   29.065185] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   51.929408] audit_printk_skb: 57 callbacks suppressed
[   51.929414] type=1400 audit(1384199590.740:31): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1872 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

[/PHP]

It shows only 51 seconds but it actually took 360 seconds to boot to desktop   so there is a full 120 seconds which is not showing up on any log.   What is this thing doing during the time when I select the drive and the cursor flashes until the purple screen starts?  How do I find out this?
Michael

---

### Post by oldfred on 2013-11-11
Are you using IPv6? It looks like it takes a bit to set that up for your wifi. You may be able to change to ignore in network settings.

Do not know what is happening at startup. The only time I have slow boot is when it runs fsck first. That is normally scheduled every 40 or 60 reboots.

Are you booting from same drive as install?

---

### Post by mmcl26554 on 2013-11-11
I was reading in another post about bootchart, in that post the problem was with the hard drive.  Although mine is an older and smaller (60Gb) that is always a possibility.  I have another drive I can try so I'm going to try than and post the outcome.
Michael

---

### Post by mmcl26554 on 2013-11-11
Fred,
If you will remember from another thread that you participated in, I have 2 drives, Vista in one, Ubuntu in another.   I originally tried to set it up as a dual boot but Grub would never boot Vista, no matter what I did.   Even the people at  "Boot repair" couldn't come up with an Idea which fixed this.   So I reinstalled 12.04, without the Vista drive in the computer and I select which OS I want by using F10 and selecting the drive it's on.   Since I did the changes you asked me to and ran update grub now the menu with Vista on it is displayed, but I don't even go there.   If I select the drive with Vista on it the grub menu does not come up and Vista boots quickly and without problem.  Also I do not use [COLOR=#000000]IPv6.   So if you can give me a heads up on how to turn it off in Ubuntu.
Michael[/COLOR]

---

### Post by oldfred on 2013-11-11
Oh that system. I do not normally reconized systems as I post a lot and see similar systems a lot. And even get my own posts mixed up. :)

There are two ways to configure Internet and they should not be mixed. The most common is gui network connections (in 12.04, sometime things change a bit in other versions). Serverals and a few edit files directly.
In network connections you have wired and maybe wireless. Click on edit and under IPv6 change to ignore. See if it boots a few seconds faster, but that probalby will not change the large problem which I do not have an answer for.

---

### Post by mmcl26554 on 2013-11-11
Fred,
It doesn't get better as you get older!   But, I know you do a lot of posting and helping and understand it's difficult to sort it all out.    I remember before I retired and doing home health, I couldn't remember patients names well, but if I was told where they live I could remember everything about them.   I always found this curious. 
Michael

---

### Post by mmcl26554 on 2013-11-13
Well I tried some things.  I installed a different hard drive and a fresh install of Vista Business edition.   I installed Ubuntu 12.04lts via WUBI.    It still takes 3 minutes to boot counting from selecting Ubuntu on the boot menu to the desktop.   I did disable IPv6 which made no difference in the boot time.   Dmesg shows a boot time of 46 seconds, for some reason it doesn't capture the first 2:15.   I have no idea what is going on for that time or what Ubuntu is waiting to happen before it actually starts to boot.   That answer would take someone with a lot, lot,lot, more experience than I have.   But I sure am curious about what the cause is.
Michael

---

### Post by oldfred on 2013-11-13
have not idea how to check that either. Not sure if BIOS, grub or if it is running some sort of hidden filecheck.

One user did post that he had a DVD in the drive and every reboot it was trying to run fsck on DVD which it obviously could not do and had to time out.
Another had BIOS set with floppy drive and had no floppy drive, so BIOS spent a lot of time looking for the floppy drive.
I might just review BIOS settings and see if anything looks out of place. It can be hard to tell what it might be. 
But I did find installing a new BIOS update resets to defaults. So I had to take photos of my BIOS screens so I knew all the changes that I had made. Took a while the first time to try to remember the changes. 
Oldfred has the memory issues also.

---

### Post by mmcl26554 on 2013-11-14
OldFred,
Thanks for your efforts!   Gateway does not have any new bios firmware beyond the original.    They won't talk to me about the computer unless I give them $100 (no chance of that).   Once Ubuntu gets up and running it works well so if I want to use it I'll just have to live with the 180second boot time.  The thing that is interesting about all this is Grub will NOT work in a dual boot mode.   That is it will not boot Vista, just hangs.    However I do get dual boot with WUBI.   I've worked with the "Boot repair" people but they couldn't resolve it.   Vista  boots fine (about 40 seconds).   So maybe these computers are just married to Microsoft and that's all that will work on them.

Fred regarding the memory issue, my Mother used to justify it by saying Her brain was getting full.    At first I just laughed it off, but come to think about it a computer with a nearly full hard drive would slow down at least with data search.    More data more time to find what you want.   So why not your brain?    I have found I can ultimately remember most of what I want but it just takes longer.    I also discover I have difficulty understanding fast talking people, especially yourn people who seem to be a group of speed talkers.    I think the conduction velocity of our nervous system has decreased and also thought processes and memory retrieval.  
If you have anymore ideas just post them here.
Thanks
Michael

---

### Post by oldfred on 2013-11-14
If you have wubi, you cannot boot Windows from the grub menu. Wubi actually boots from the Windows boot loader and you get Vista's BCD to have another entry for Ubuntu. So you should get a Windows boot and then grub/Ubuntu boot.
A full install to a separate partition should work better.

       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

But wubi is being discontinued as it does not work with gpt partitioned drives which all new UEFI systems now have.

---

### Post by mmcl26554 on 2013-11-14
I just recently tried WUBI because with Ubuntu in a separate drive and with grub dual boot didn't work.    After working with that setup I installed Ubuntu to the separate drive as the only OS on the computer and still boot times were long.   I could select the OS I wanted by having the computer boot from the selected drive after pressing F10.   I wondered if WUBI would work any better so I a couple days ago I tried WUBI,   I get a dual menu that works but boot times for Ubuntu are still long.   So WUBI is just a recent try in the saga of long boot time for Ubuntu.  But if I want a dual boot menu WUBI is the only one that works.   I tried separate drive installations but grub can boot Vista.
Michael

---

