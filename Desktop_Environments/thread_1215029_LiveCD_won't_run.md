---
title: "LiveCD won't run"
date: 2009-07-16
forum: Desktop Environments
---

### Post by Cascadian on 2009-07-16
My problem PC is an IBM T42 laptop running XP Pro SP3. I think a virus and (perhaps) a totally clogged registry finally did something so bad to my PC that it won't boot up anymore. Just after the Microsoft logo screen comes up, then goes away in preparation for loading the Win/XP operating system, I get a blue screen that tells me I have a fatal error and the system reboots... over and over.
 
I wanted to run Ubuntu's Linux O.S. from a cd (i.e., a 'liveCD') so that I could look into the PC to try to determine what may be wrong. Or to run a Registry cleaner... whatever!
 
But, even though I changed the CD drive to be the first in the sequence of devices from which an O.S. will be loaded, nothing happens. The CD drive operates but I still go on to the Microsoft logo screen and, shortly afterwards, the blue screen of death.
 
The 'LiveCD' contains one file: a 6nnMB .iso file for a 32-bit Intel system. What am I doing wrong? Why is Windows still continuing to try to load even though I've told the system to get the O.S. that I want to run from the CD?
 
Thanks in advance for your help.

---

### Post by merlinus on 2009-07-16
You need to burn it as a disk image, not a data disk.  You should see directories and files on the cd.

Be sure to checksum your .iso, and burn at no more than 4x.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Cascadian on 2009-07-16
Thanks, Merlin, your answer has made my initial problem crystal clear. I thought I saw somewhere on the Ubuntu site, a picture of the CD's contents in Windows Explorer (?) that showed all of the files that are on the CD. I just could never find it again in order to better understand what they were talking about. Not finding that image caused me to just trudge my way into the totally wrong format for what I'm trying to do.
 
I'll give 'er another go and report back!
 
Thanks again - you're a magician

---

### Post by lisati on 2009-07-16
> **Cascadian said:**
> My problem PC is an IBM T42 laptop running XP Pro SP3. I think a virus and (perhaps) a totally clogged registry finally did something so bad to my PC that it won't boot up anymore. Just after the Microsoft logo screen comes up, then goes away in preparation for loading the Win/XP operating system, I get a blue screen that tells me I have a fatal error and the system reboots... over and over.
 
I wanted to run Ubuntu's Linux O.S. from a cd (i.e., a 'liveCD') so that I could look into the PC to try to determine what may be wrong. Or to run a Registry cleaner... whatever!
 
But, even though I changed the CD drive to be the first in the sequence of devices from which an O.S. will be loaded, nothing happens. The CD drive operates but I still go on to the Microsoft logo screen and, shortly afterwards, the blue screen of death.
 
The 'LiveCD' contains one file: a 6nnMB .iso file for a 32-bit Intel system. What am I doing wrong? Why is Windows still continuing to try to load even though I've told the system to get the O.S. that I want to run from the CD?
 
Thanks in advance for your help.

My Compaq desktop went a bit berserk in after installing XP SP3, turns out there was a patch/update from the manufacturer needed to let it run SP3. Your machine might need one too.

If you go with [what merlinus said]("https://help.ubuntu.com/community/BurningIsoHowto"), you should be fine for getting Ubuntu up and running.

---

