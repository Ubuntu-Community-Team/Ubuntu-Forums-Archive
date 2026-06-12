---
title: "how to RAID desktop drives"
date: 2012-11-14
forum: Desktop Environments
---

### Post by DJeXo on 2012-11-14
hey guys,
        I'm trying to build up a 12.04 Desktop with the following config:

I have a hp microserver n36l that has 4 bays which are connected to a raid card, I've setup the controller options to be single drives so they appear individually. I've additionally got another sata port which has another drive of the same size as well as a 64GB SSD hdd I'll be installing the OS onto.

So it's like this
RAID COntroller = 4x 2TB WD Green Drive  (single drive mode)
SATA port = 1x 2TB WD green drive
eSATA port = 64GB SSD (ubuntu desktop install)

What I want to achieve is to software raid the 4xWD green drives to be RAID5 with the extra WD green drive in the SATA port as the RAID spare.

I've tried installing the desktop 12.04 and install mdadm to attempt to build the raid but it never finds the devices despite running gpart which confirms the drives 

/dev/sda = WD Green 2TB 
/dev/sdb = WD Green 2TB 
/dev/sdc = WD Green 2TB 
/dev/sde = WD Green 2TB 
/dev/sdg = WD Green 2TB (spare)
/dev/sdf = SSD drive (Operating System)


I run the following command within the desktop environment and it gives me an error saying 'no raid devices found' (not exact error message).

here is my syntax
sudo mdadm --create /dev/md0 --chunk=4 --level=5 --raid-devices=4 /dev/sda /dev/sdb /dev/sdc /dev/sde --spare-devices=1  /dev/sdg



am I doing something wrong? or is there a GUI friendly way I could go about creating this RAID? or perhaps there is a limitation to this that I'm missing?

I don't want to complicate it by installing an OS on it and would like to store any RAID config information on the SSD.

any help appreciated. :-)

---

### Post by DJeXo on 2012-11-15
anybody? any possible clues or better methods?

---

### Post by rickkos on 2012-11-15
Hey DjeXo,
 
Did you find a solution to this issue? I am looking at doing the same thing but have no good instructions yet.
 
I will reciprocate if I find any solutions.
 
Cheers,
Rick

---

### Post by DJeXo on 2012-11-15
not as yet, I'll continue working on it and post my results.

I think I may have more joy by going through the setup for the server ISO till I have the raid setup then reboot and install the desktop version instead. 

I *would* prefer server but have had little success as I don't know what components are missing to turn a server install into a desktop variant (the server install doesn't recognise some of my devices as the desktop version picks it up right away)

---

### Post by madverb on 2012-11-16
1. Don't use RAID5 with a spare! Just use RAID10.
2. pretend from now on that there is no such thing as RAID5. RAID5 is legacy junk and needs to be forgotten.
3. [http://kamlau.com/software/how-to-setup-raid10-with-ubuntu/](http://kamlau.com/software/how-to-setup-raid10-with-ubuntu/)
4. ???
5. Profit

---

### Post by DJeXo on 2012-11-18
thanks for the advice madverb!

I managed to get RAID5 installed using the server install --> committed changes and rebooted to install the desktop version but to no avail (it didn't see the RAID I setup)... so I had no choice at this point to continue the installation.

Once I rebooted the RAID came up in a degraded state indicating one of my drives was dead, I'm checking into this as when I ran a diag against the drive it was fine?

anyways, I'll try installing the desktop version again and try mdadm to configure raid 10.

madverb - do you have any suggestions on how to setup RAID from an installed desktop 12.04.1 with my above config? ?

---

### Post by DJeXo on 2012-11-18
sorry, I should have read your link more closely. 

Based on that article - I need to pre-format the drives prior to RAIDing them up?
(it doesn't mention it but the disks being attached indicate it)

---

### Post by rubylaser on 2012-11-20
> **madverb said:**
> 1. Don't use RAID5 with a spare! Just use RAID10.
2. pretend from now on that there is no such thing as RAID5. RAID5 is legacy junk and needs to be forgotten.
3. [http://kamlau.com/software/how-to-setup-raid10-with-ubuntu/](http://kamlau.com/software/how-to-setup-raid10-with-ubuntu/)
4. ???
5. Profit

I wouldn't say that RAID10 is always the correct solution in all situations.  You can still lose your array if you lose two disks from the same mirror, and with mdadm, you cannot currently expand a RAID10 array (Note: with 3.2 you cannot resize any mdadm RAID10 arrays, but with kernels > 3.4-rc, you can grow RAID10, but only for 'near' and 'offset' layouts).  With the OP wanting to use a spare, this would be a situation where RAID6 is a fine solution.  It ALWAYS survives two disk failures and can be expanded with mdadm.

Also, in most cases LVM is not needed with mdadm anymore (unless you want LVM snapshots).  mdadm arrays and easily be expanded and even reduced pretty easily. And, for home users, SnapRAID (with 2 parity disks if you'd like) is another resilient, expandable solution.

---

### Post by steeldriver on 2012-11-20
A bit OT but if you are planning on / using WDC Green drives in RAID as per the original post you should be aware of possible excessive load cycle counts

[http://www.storagereview.com/how_to_stop_excessive_load_cycles_on_the_western_digital_2tb_caviar_green_wd20ears_with_wdidle3](http://www.storagereview.com/how_to_stop_excessive_load_cycles_on_the_western_digital_2tb_caviar_green_wd20ears_with_wdidle3)

Regards

---

### Post by madverb on 2012-11-20
Yes RAID6 is fine... but why use a spare when you have 4 drives? I never said RAID10 is always the best solution. I just recommended it over RAID5 with a spare. RAID6 with a spare might be a good idea but you have to take into account slower rebuild times. Degraded performance during rebuilds. Lower performance in general in comparison to RAID10.

---

### Post by madverb on 2012-11-20
> **steeldriver said:**
> A bit OT but if you are planning on / using WDC Green drives in RAID as per the original post you should be aware of possible excessive load cycle counts

[http://www.storagereview.com/how_to_stop_excessive_load_cycles_on_the_western_digital_2tb_caviar_green_wd20ears_with_wdidle3](http://www.storagereview.com/how_to_stop_excessive_load_cycles_on_the_western_digital_2tb_caviar_green_wd20ears_with_wdidle3)

Regards

I'm pretty sure you can modify the drives firmware so they don't go idle.

---

### Post by steeldriver on 2012-11-20
> **madverb said:**
> I'm pretty sure you can modify the drives firmware so they don't go idle.

indeed - that's what the link I posted is about - you can use WD's own wdidle3.exe if you can boot MS or the open source idle3-tools

---

### Post by rubylaser on 2012-11-20
> **madverb said:**
> Yes RAID6 is fine... but why use a spare when you have 4 drives? I never said RAID10 is always the best solution. I just recommended it over RAID5 with a spare. RAID6 with a spare might be a good idea but you have to take into account slower rebuild times. Degraded performance during rebuilds. Lower performance in general in comparison to RAID10.

I never mentioned using a spare with RAID6. I said the OP was planning on using a spare with RAID5, so it would make sense to just use RAID6 instead.  You'd end up with the same size disk array as a RAID10, but have one that you could expand in the future, and it can always survive two disk failures (potentially more fault tolerant than a RAID10 array).  

Any of these solutions, RAID5/6/10 will all easily saturate a gigabit connection, so the lower performance argument doesn't make sense for a home user's fileserver unless they are trying to host VMs on the machine or using LACP or 10GBe to achieve speeds greater than gigabit. For most home users, the tradeoff between slightly lower performance vs the RAID10, with the ability to easily expand, and always surviving two disk failures makes a lot of sense.

If you are happy with RAID10, that's great, I had no intention of saying what you proposed was a bad idea.  I use a mix of RAID1/6/10 at work all the time depending on the reliability and performance requirements. I was just presenting another option the the OP and providing the potential  downsides of going with mdadm RAID10.  It's good to know the pros and cons of any solution before you get way down the road and realize you can't expand if you want to. If he ever plans to grow in the future, RAID10 really isn't a viable solution at this point (may be with future mdadm and kernel releases).  In either case, RAID6/10 are both better solutions in terms of reliability than RAID5.

Depending on what the OP plans to store on the array, the simplicity of SnapRAID may be better than all of these solutions.  Or, if data integrity is of upmost importance, ZFS may be a better solution, it's hard to provide the best idea without really knowing the use case. Sorry if you felt I was attacking your position, that was not my intent :)

---

### Post by DJeXo on 2012-11-25
thanks for the additional info guys, RAID6 is looking more viable as I'd like to have the option to lets say expand the drives out to 3TB disks when they become more affordable without a major overhaul.
I'll be primarily using this array for tv/movies/music/cctv logging but will also be storing documents/profile from my home domain.
THe frontend of this server will be a XBMC media server but I plan to use it for other services as I build them making it AIO. 

I'll keep you guys posted as I've already done a test run of assembling an array but a HDD appears to be degraded already (BIOS picks it up without problems) so once I finish investigating that I'll continue.

---

### Post by DJeXo on 2013-01-07
well... after some back/forth and waiting for raid to build I've finally had to reduce my drives to 4 in RAID5 without a spare.
the spare was attached to a eSATA port to which I noticed it was the one that kept giving the RAID grief starting up hence I removed it.

I tried doing my work via terminal with mdadm but noticed that running palimsest with root credentials gave me more fruitful results.

I haven't created an automount for startup as yet because I'm tweaking the RAID for abit more speed,
so currently I run ext4 and it runs fine on 2gb ram!

stay tuned as I'm not home to display exact results from teh linux box.

---

### Post by Cheesemill on 2013-01-07
Have you seen this thread talking about a RAID tuning script?

[http://ubuntuforums.org/showthread.php?t=1916607](http://ubuntuforums.org/showthread.php?t=1916607)

---

