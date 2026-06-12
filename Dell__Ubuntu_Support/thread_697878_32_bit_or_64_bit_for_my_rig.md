---
title: "32 bit or 64 bit for my rig"
date: 2008-02-15
forum: Dell  Ubuntu Support
---

### Post by EllsworthT on 2008-02-15
I was wondering which version of Ubuntu (Gutsy) I should run on my rig (Seen in signature) the live cd (32 bit) or the 64 bit.

Thanks.

---

### Post by dayhawk4 on 2008-02-17
This is a question that I have been asking myself as well.  From reading all of the other posts on this subject, it is a matter of personal preference and usage.  

Down sides:

When working with any code that you don't have access, it may not be possible to get a compiled 64-bit version (must look at individual packages).  These issues include

codecs (compression and decompression libraries for audio and video as well as DVDs, etc.)

java (from what I have been reading, currently only available in 32-bit version, though there is a way to install the 32-bit version and get it to work)

flash (again, 32-bit version can be installed like java, and there are several howtos, different people get different mileage out of it from what I have been reading)

restricted drivers -- Some hardware vendors are releasing drivers with there cards that allow for use in linux.  Nvidia is an example, though they have both 32-bit and 64-bit versions available.

There are several very informative sections in the 64-bit forum worth going through which point to several other very long articles on the differences between 64-bit and 32-bit.  If your installing a fresh system, I would give it a try.  Maybe make a dual boot linux box and try them both!  Best of luck and let me know how it turns out.....

dayhawk4

> **EllsworthT said:**
> I was wondering which version of Ubuntu (Gutsy) I should run on my rig (Seen in signature) the live cd (32 bit) or the 64 bit.

Thanks.

---

### Post by bluedragon436 on 2008-02-17
Honestly I would run the 32bit version but that is just me...I am running the 32 bit version on both of my 64bit computers...I tried to install the 64bit version on one of them and had a few issues when setting the hardware up...and I tried the 32 bit on my other computer (the exact same setup) and it worked just fine with the normal few small issues that I was able to tweak and take care of quickly...

---

### Post by pormogo on 2008-02-18
This is a question I've been juggling with as well. When I moved into my new apartment I decided to do some hard drive re organization and move my main desktop to 7.10 64bit (from 7.04 32bit). Upon rebooting I didn't notice any issues. But within the few weeks I saw the following error start rearing it's ugly head. 

*[ 29.281831] PCI: Cannot allocate resource region 0 of device 0000:00:00.0*

I made a forum thread about it ([http://ubuntuforums.org/showthread.php?p=4276315#post4276315](http://ubuntuforums.org/showthread.php?p=4276315#post4276315))  but no one responded and I have yet to find out why this is happening (on the same system using 32 bit 7.04 this didn't happen). I've also had hell with the newest version of amd's fglrx driver ([http://ubuntuforums.org/showthread.php?t=694003](http://ubuntuforums.org/showthread.php?t=694003)) and getting it running with 2 monitors running compiz. I haven't actually thought to consider that 64bit might be the issue until right now =P as it is really, the only difference between the config before and after I played some hard disk musical bays.  

I was wondering what kind of installs the dell's built with ubuntu come with. I'm going to be getting one of the Ubuntu pre loaded M1330's. Are those loaded up with 64 bit or 32 bit?

---

### Post by frankos44 on 2008-02-18
Ive been running 32 bit for over a year and made the plunge to 64 bit only last week.

The reason for running the 32 bit  initially was certain apps I depended on didnt work.  

With a bit of effort I managed to get these apps to work properly now. 

The 64 bit system initially didnt seem to be much faster but when I loaded compiz-fusion I noticed a big improvement. I now have breath taking smooth advanced desktop effects such as rotating cube, much much better than on 32 bit in my case.

$ sudo apt-get remove gnome-compiz-manager
$ sudo apt-get install compizconfig-settings-manager

I wont be using 32 bit anymore on this PC.

---

### Post by pormogo on 2008-02-18
I actually haven't noticed any speed differences between the 64bit version of the distribution and the 32bit version. In all honesty it seems when using things like flash (which uses a wrapper for the 32bit version) it seems like it's eating more CPU then it used to. Just what I happened to notice.

---

