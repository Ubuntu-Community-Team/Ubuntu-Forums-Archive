---
title: "error 25 disk read error"
date: 2009-04-17
forum: General Help
---

### Post by shendric on 2009-04-17
I tried to update my 8.10 machine, and it froze.  I tried to restart, and now I get Error 25: disk read error when I try to boot.  When I "press any key to continue..." I go back to grub, which gives me multiple kernel options.  None of them boot.

How can I boot from a CD (I don't have a boot disk) so I can see if the data is still salvageable?  Or is that the best procedure at this point?

Any help would be greatly appreciated.

Sean

---

### Post by Klaz168 on 2009-04-17
I think its a problem with GRUB. Boot into a live CD and re-install.

---

### Post by jrdonnaruma on 2009-04-17
If you have a live-cd from when you installed 8.10 just boot with that and see if you can access the drive and data. Otherwise, download another live cd, or the Linux System Rescue cd (Or usb version), burn, boot, move data, and your all set. (you can also boot a live cd from a USB, just search for it, or look in the ubuntu wiki.)

---

### Post by shendric on 2009-04-17
> **jrdonnaruma said:**
> If you have a live-cd from when you installed 8.10 just boot with that and see if you can access the drive and data. Otherwise, download another live cd, or the Linux System Rescue cd (Or usb version), burn, boot, move data, and your all set. (you can also boot a live cd from a USB, just search for it, or look in the ubuntu wiki.)

Thanks jrdonnaruma, I'm downloading the live-cd on another machine, but it's going to be a while.  When you say "move data," are you meaning onto another drive?  How will I access the hard drive that won't boot?  Do you think I'll just be able to access it normally from the LiveCD?  

I've seen some things around about reinstalling grub, or editing menu.lst.  I'm ok with getting a new drive (although this one is only 3 months old), but I'm just looking at my options.

Sean

---

### Post by shendric on 2009-04-17
> **Klaz168 said:**
> I think its a problem with GRUB. Boot into a live CD and re-install.

Do you mean reinstall 8.10?  Wouldn't that delete all previous data?  There's data on that drive that hasn't been backed up yet.

Sean

---

### Post by cariboo on 2009-04-17
Follow this [thread=224351]howto[/thread] to repair grub. Almost any Ubuntu live cd will work.

Jim

---

### Post by Herman on 2009-04-17
Most often in the past, GRUB Error 25 has been caused by adding or removing a hard drive or cable, or changing the jumper settings on IDE drives (including the CD/DVD drive) incorrectly. Have you added or removed any drives lately or have you been doing any work inside your computer case recently that might have caused you to remove any cables for access?
Also, try checking your BIOS settings and make sure all your hard drives are properly detected and set up correctly by the BIOS.

---

### Post by shendric on 2009-04-17
> **cariboo907 said:**
> Follow this [thread=224351]howto[/thread] to repair grub. Almost any Ubuntu live cd will work.

Jim

Thanks!  I'll give it a look.

Sean

---

### Post by shendric on 2009-04-17
> **Herman said:**
> Most often in the past, GRUB Error 25 has been caused by adding or removing a hard drive or cable, or changing the jumper settings on IDE drives (including the CD/DVD drive) incorrectly. Have you added or removed any drives lately or have you been doing any work inside your computer case recently that might have caused you to remove any cables for access?
Also, try checking your BIOS settings and make sure all your hard drives are properly detected and set up correctly by the BIOS.

Haven't been mucking around with it.  It got shut down due to a power outage, and when I rebooted it, I decided to let it do all the updates it was wanting to do.  After downloading the updates, it just started spinning, and showing me errors.  I tried other options before shutting it down hard and restarting again.  After that, I got the error 25 messages.

Sean

---

### Post by Herman on 2009-04-17
> Haven't been mucking around with it. It got shut down due to a power outage, and when I rebooted it, I decided to let it do all the updates it was wanting to do. After downloading the updates, it just started spinning, and showing me errors. I tried other options before shutting it down hard and restarting again. After that, I got the error 25 messages. AHA! Now we're getting warmer!
Please try booting your latest Ubuntu LiveCD and either [run a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")  or [run a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") from the command line, (whichever you prefer).
If you use Gnome Partition Editor for that, make sure you save the details as they may have important information in them. :)

If you use the command line, also save the details, the command line will give you useful feedback.

---

### Post by shendric on 2009-04-18
> **Herman said:**
> AHA! Now we're getting warmer!
Please try booting your latest Ubuntu LiveCD and either [run a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")  or [run a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") from the command line, (whichever you prefer).
If you use Gnome Partition Editor for that, make sure you save the details as they may have important information in them. :)

If you use the command line, also save the details, the command line will give you useful feedback.

ok, I downloaded the 8.10 Live CD, burned the iso and booted into it.  It seemed to boot up fine, I heard the "ubuntu startup sound", but got nothing but a blank screen.  I then used CTRL-ALT-F1 to leave the gui and get the command line.  I tried to run fdisk -l to get a list of partitions but got nothing.  I tried to navigate to the drives, but got nothing.  When I booted up I just used the first option of "try ubuntu without changing your computer".

Am I missing something?

I'd really appreciate any help, because I'd like to sleep sometime in the near future. :)

Sean

---

### Post by shendric on 2009-04-18
ok, so I was able to boot the live cd using safe graphics mode.  when I went to GParted, it says that it detects no devices.  This sounds like a bad thing.

Is there something else I need to do to get it to detect those drives?

Sean

---

### Post by shendric on 2009-04-18
ok, so some more looking around led me to some talk about GParted having trouble detecting SATA drives.  The drive I'm hoping to fix is a SATA drive.  If GParted can't seem to detect it, and fsck -l doesn't detect it, and I don't see any partition-like names in /dev, what can I do to fix this, if anything?  I don't know the name of the partition that ubuntu is on (sdaX or hdX, etc.).

Again, any help or advice would be appreciated.

Sean

---

### Post by Klaz168 on 2009-04-18
Did you add new disks recently, changed jumpers/cables or something like that? I'd say get in your BIOS and check whether your disks are read or not

If you can provide more information that'd be better

---

### Post by shendric on 2009-04-18
> **Klaz168 said:**
> Did you add new disks recently, changed jumpers/cables or something like that? I'd say get in your BIOS and check whether your disks are read or not

If you can provide more information that'd be better

Here's what I get in BIOS, which is not good, I'd say:

Under Boot: Hard Drive Order - No Hard Disk Drive

I didn't make any changes to the hardware, I haven't even opened it since it was built.

What other information would be useful?  Just let me know, and I'll be glad to get it.

---

### Post by shendric on 2009-04-18
I appreciate everyone's help, but it looks like I'm the unhappy owner of a defective hard drive.

---

### Post by Herman on 2009-04-18
Sorry for the late reply, I guess it's the time zone difference. 

GParted has trouble recognizing SATA drives? What was the date of the website where you read that? I remember a few years ago when Ubuntu was just getting started and GParted was in it's early stages of development when that was an issue for a few people, but I haven't heard for it for a long time now. There will always be new hardware being invented though, that the developers need to keep up with. I think they're doing a pretty good job though, actually, I'm amazed!

I'm sorry to hear your hard disk might be faulty of your motherboard is having problems detecting it. 
> ok, I downloaded the 8.10 Live CD, burned the iso and booted into it. It seemed to boot up fine, I heard the "ubuntu startup sound", but got nothing but a blank screen. I then used CTRL-ALT-F1 to leave the gui and get the command line. I tried to run fdisk -l to get a list of partitions but got nothing. I tried to navigate to the drives, but got nothing. When I booted up I just used the first option of "try ubuntu without changing your computer".> ok, so I was able to boot the live cd using safe graphics mode. when I went to GParted, it says that it detects no devices. This sounds like a bad thing.
Is there something else I need to do to get it to detect those drives?You needed to boot in 'Safe Graphics Mode'?

I'm not sure, but I think you should consider the possibility that it might be the power supply first, before you go blaming the hard disk. Power supplies are the part of the most computers that are most prone to failure. (Because most people buy the cheapest one they can get).  In my locality, they are also subject to a lot of abuse from out-of-spec electricity supplied from the power company. Where I live we need good surge protectors or a UPS unit.
It could be that you hard drive is okay, but it isn't getting enough power from the power supply to spin it up. 
Try going into your BIOS and looking for something like a [System Health Check]("http://www.users.bigpond.net.au/hermanzone/p1.htm#System_Health_Check").
Are your voltages nice and steady? Or are they up and down like a yo-yo?
Are they somewhere close to what they're supposed to be?

---

### Post by shendric on 2009-04-19
No worries on the late reply.  I finally took it to a friend of mine to see if we could recover some of the data.

> **Herman said:**
> Sorry for the late reply, I guess it's the time zone difference. 

GParted has trouble recognizing SATA drives? What was the date of the website where you read that? I remember a few years ago when Ubuntu was just getting started and GParted was in it's early stages of development when that was an issue for a few people, but I haven't heard for it for a long time now. There will always be new hardware being invented though, that the developers need to keep up with. I think they're doing a pretty good job though, actually, I'm amazed!


I'm not sure of the date.  Just something I was seeing a few people say, and I wasn't sure if that would have something to do with it.

> **Herman said:**
> 

I'm sorry to hear your hard disk might be faulty of your motherboard is having problems detecting it. 
You needed to boot in 'Safe Graphics Mode'?


I had read somewhere that if you get a blank white screen like I did that booting in Safe Graphics Mode would work.  And it did.

> **Herman said:**
> 

I'm not sure, but I think you should consider the possibility that it might be the power supply first, before you go blaming the hard disk. Power supplies are the part of the most computers that are most prone to failure. (Because most people buy the cheapest one they can get).  In my locality, they are also subject to a lot of abuse from out-of-spec electricity supplied from the power company. Where I live we need good surge protectors or a UPS unit.
It could be that you hard drive is okay, but it isn't getting enough power from the power supply to spin it up. 
Try going into your BIOS and looking for something like a [System Health Check]("http://www.users.bigpond.net.au/hermanzone/p1.htm#System_Health_Check").
Are your voltages nice and steady? Or are they up and down like a yo-yo?
Are they somewhere close to what they're supposed to be?

I'll have to take a look at that.  I was able to recover some of the critical data off of the drive, and I'm going to attempt to clone it, if possible.  The friend of mine who does data recovery was leaning towards a corruption of some of the data on the disk, but it's not certain.

---

### Post by shendric on 2009-04-19
Just checked the voltages, and they're pretty darn steady.  And right where they should be.

I was also thinking of trying to connect the drive to the secondary drive controller and changing the BIOS to boot up from there.

---

