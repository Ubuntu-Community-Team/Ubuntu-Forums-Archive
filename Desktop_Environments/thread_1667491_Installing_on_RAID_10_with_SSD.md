---
title: "Installing on RAID 10 with SSD"
date: 2011-01-14
forum: Desktop Environments
---

### Post by phylae on 2011-01-14
I am putting together a "workstation." By that I mean a machine that will be used for desktop-like tasks, but is probably closer to a server when it comes to the physical hardware.

I'm planning to install Ubuntu 10.04 (I'd like to stay with the LTS, if possible.)

The main will have 4 SSD drives (this one I think [http://www.crucial.com/store/partspecs.aspx?IMODULE=CTFDDAC064MAG-1G1](http://www.crucial.com/store/partspecs.aspx?IMODULE=CTFDDAC064MAG-1G1)). I would like to set them up with software RAID 10.

1) will it be possible to install Ubuntu directly to a RAID 10 setup (and boot from it)? I have seen some reports that older versions of Ubuntu could only install to RAID 0, 1, and 5.

2) I have read that TRIM is disabled when using SSDs in RAID. Should I be concerned about that? I have heard of some TRIM-like utilities than cause a greater load on the system, but are fine when run during down time. What are the recommended best practices for this?

3) I have read that the SSD drives will last longer if a certain % (some say 20%) remains unused. Is this true? What is a good %? I have heard that using LVM to block of this % can make sure you don't accidentally write to it. Is that the best way to do it?

4) In a RAID setup, how do I know if the array is in a degraded state? Do I need to set up some sort of monitoring or will I see an error message in GNOME?

5) I use VirtualBox for Windows occasionally. (Not my choice, but I have to check websites in IE and GoToMeeting doesn't support Linux.) I don't keep much on the Windows VMs, but the disk usage really adds up quickly. Probably 30-40% of my current disk usage is VirtualBox files. I'm assuming that network storage for these would be too slow; (my link to a fileserver is only 100Mbps). Do you think I'd be better off storing these on a standard harddrive to save space on the SSDs (and theoretically pro-long their life)?

6) Which filesystem do you recommend for the SSDs on RAID 10? I have read a lot of confusing things about which filesystems are good/bad for SSDs. My past machines have all been ext3/4. I'm quite happy to try something new. But I don't want to be super bleeding edge. I tried ZFS a couple years ago and that was too much pain. I don't want to go through the trouble of RAID only to mess something up with the filesystem.

7) Are there any other best practices, articles, blog post, or links you can recommend (relating to RAID 10 and/or SSD)?


Thank you!

---

### Post by kidders on 2011-01-16
Hi there,

I can only answer some of your questions, but your post has gone unanswered for a whole day now, so here goes ...

> **phylae said:**
> will it be possible to install Ubuntu directly to a RAID 10 setupOff the top of my head I can't remember ... The best way to be sure is to try. To save time, I would create a RAID array first, and see if the installer notices it. If not, maybe it will create one of its own from scratch. If you find it just won't play ball, you could always resort to a non-RAID install & move your OS onto an array afterwards.

If you have to go down the post-install RAID road, it'd probably be best to put /boot on a partition by itself from the start, just to keep life simple.

> **phylae said:**
> I have read that TRIM is disabled when using SSDs in RAID. Should I be concerned about that? I have heard of some TRIM-like utilities than cause a greater load on the system, but are fine when run during down time. What are the recommended best practices for this?TRIM is part of the ATA specification, so the abstraction layer sitting between your interface (eg /dev/md0) and the physical hardware will probably render TRIM/discard instructions ineffective. Similarly, your VirtualBox environment won't be able to send TRIM instructions to your SSDs.

As you mentioned, some SSDs are capable of delaying garbage collection until the device is idle. It's not something the end user has any control over though.

> **phylae said:**
> I have read that the SSD drives will last longer if a certain % (some say 20%) remains unused.That's true, in that less data = less I/O. Over-provisioning also has performance benefits, although I imagine the effect would be fairly short-term. Most SSDs are already over-provisioned out of the box.

The main observation I'd make here is that you're already planning to run RAID, use virtual machines and (unless you're mad :p ) set up swap partitions on SSDs, all of which will negatively affect their lifespans over and above "normal" use. In that context, I'm not confident that leaving large chunks of your disks unallocated will achieve much more than deprive you of 10s of gigabytes of disk space you've paid through the nose for.

> **phylae said:**
> In a RAID setup, how do I know if the array is in a degraded state?Something like **mdadm --detail /dev/md0** will tell you. You can have mdadm mail you when it spots a failure, if you'd like.

> **phylae said:**
> I'm assuming that network storage for these would be too slow; (my link to a fileserver is only 100Mbps).AoE over a gigabit connection might be worth considering, but 100Mbps would be *miles* too slow, especially if by "fileserver" you mean something running a standard file sharing protocol.

To be honest, I'm very dubious about the wisdom of using RAID on SSDs. If you don't mind me asking, why are you interested in doing it? On the face of it, dropping the RAID and storing your Linux OS & VirtualBox images on SSDs, seems like a better use of resources. You could put your personal files on HDDs.

In terms of perceived performance, for instance, it seems smarter to put files responsible for launch-time latency (eg dynamically linked libraries) on an SSD. It's a pretty silly example, but suppose you wanted to play an MP3. The majority of the time taken to do it is spent waiting for the MP3 player to launch ... Once that's done, actually initiating the playback of the MPEG data itself is essentially instantaneous. Under typical desktop conditions, the best way to give a box a "zippy" feeling is to try to accelerate tasks like booting, launching big apps, etc. All RAID would do is negate some of the SSD advantage, and give you redundant copies of lots of files that came straight off a CD anyway.

> **phylae said:**
> Which filesystem do you recommend for the SSDs on RAID 10?That's a hugely complex question, and always depends on exactly what you'll be doing with your computer. Stick to something mature, with a complete toolset & widespread adoption. In the right contexts, filesystems like XFS, JFS, EXT2/3/4 & ReiserFS are all good options.

I hope at least *some* of that is helpful.

---

### Post by phylae on 2011-01-18
> **kidders said:**
> 
I can only answer some of your questions, but your post has gone unanswered for a whole day now, so here goes ...


Thank you so much for replying! And sorry for being so slow to answer. I accidentally turned off email notifications so I thought nobody had answered.


> **kidders said:**
> 
The best way to be sure is to try. To save time, I would create a RAID array first, and see if the installer notices it.
Will do. I'll (try to remember to) post back here with the results.

> **kidders said:**
> 
it'd probably be best to put /boot on a partition by itself

That's what I've got on my laptop, so I was thinking I'd stick with that.

> **kidders said:**
> 
TRIM is part of the ATA specification, so the abstraction layer sitting between your interface (eg /dev/md0) and the physical hardware will probably render TRIM/discard instructions ineffective. Similarly, your VirtualBox environment won't be able to send TRIM instructions to your SSDs.


Thank you for clarifying that.

> **kidders said:**
> 
As you mentioned, some SSDs are capable of delaying garbage collection until the device is idle. It's not something the end user has any control over though.

That's interesting. The forums I was reading seemed to be referring to extra tools that I would install and schedule to run on a regular basis. Something like the Windows defrag tools.


> **kidders said:**
> 
...I'm not confident that leaving large chunks of your disks unallocated will achieve much more than deprive you of 10s of gigabytes of disk space
Thanks. That's interesting to know.


> **kidders said:**
> you've paid through the nose for.
Actually, the drives weren't too bad. Since this is for work, I get some pretty nice tax breaks. And I don't need a lot disk space.


> **kidders said:**
> 
Something like **mdadm --detail /dev/md0** will tell you. You can have mdadm mail you when it spots a failure, if you'd like.

Thanks. That is a great starting point for me.


> **kidders said:**
> 
AoE over a gigabit connection might be worth considering, but 100Mbps would be *miles* too slow, especially if by "fileserver" you mean something running a standard file sharing protocol.


I'm not familiar with AoE. I'll definitely need to read up on it more. It could be a good option once I upgrade the wiring to gigabit.

The "fileserver" I am referring to is basically a simple Ubuntu Server machine with a bunch of hard drives and running Samba. (I chose Samba because originally I had to support some Windows clients, and I've just been too lazy to switch it.) Currently I use it to store media, pictures, documents, and backups.




> **kidders said:**
> 
To be honest, I'm very dubious about the wisdom of using RAID on SSDs. If you don't mind me asking, why are you interested in doing it? On the face of it, dropping the RAID and storing your Linux OS & VirtualBox images on SSDs, seems like a better use of resources. You could put your personal files on HDDs.


I wanted RAID because, although I have a decent backup strategy (sync to my "fileserver" which in turn syncs to JungleDisk) if a drive fails, I'd rather just be able to replace the drive and keep going than have to go through a lengthy reinstall/restore process. We're talking about about 30-60 minutes of recovery effort for RAID vs. 10-20 hours for a reinstall/restore. (I have a lot of extra stuff, including custom-compiled stuff.)

I wanted RAID 10 because the price difference between 2 128GB drives and 4 64GB drives was pretty small, and I figured I might as well get the performance boost. Assuming I was doing at least RAID 1, RAID 10 seemed like a safe performance boost.

My "personal" files are pretty much all stored on HDDs on my fileserver. They are either small enough or infrequently accessed enough that the 100Mbps is not a problem.


> **kidders said:**
> 
In terms of perceived performance, for instance, it seems smarter to put files responsible for launch-time latency (eg dynamically linked libraries) on an SSD.

This completely makes sense. I want anything I install with apt-get, as well as anything I custom-compile to be on the SSDs. I want fast launch time for programs.
I also would really like my MySQL and PostgreSQL databases running on SSDs too. They contain very little data. But I run tons of automated tests, and I expect that these will speed up a lot on SSDs. (Of course, I'd be better off running these off a RAM drive. Maybe I'll set that up soon.)


> **kidders said:**
> 
It's a pretty silly example, but suppose you wanted to play an MP3. The majority of the time taken to do it is spent waiting for the MP3 player to launch ... Once that's done, actually initiating the playback of the MPEG data itself is essentially instantaneous.

I totally understand this. All my media (video, audio, images) will be stored on HDDs. That's part of why I don't need much disk space.


> **kidders said:**
> 
Under typical desktop conditions, the best way to give a box a "zippy" feeling is to try to accelerate tasks like booting, launching big apps, etc.

See below for for details on my intended use. But yes, this is where I expect to notice the biggest difference.


> **kidders said:**
> 
All RAID would do is negate some of the SSD advantage, and give you redundant copies of lots of files that came straight off a CD anyway.


My understanding was that RAID 10 was usually faster than a single drive. (i.e. The performance gains from the "0" layer out-weighed the performance hit of the "1" layer.) Is this not true for SSDs?

As mentioned above, my goal with RAID is mostly to save the time reinstalling/recompiling stuff. It is all recoverable. But it takes a ton of time.


> **kidders said:**
> 
That's a hugely complex question, and always depends on exactly what you'll be doing with your computer. Stick to something mature, with a complete toolset & widespread adoption. In the right contexts, filesystems like XFS, JFS, EXT2/3/4 & ReiserFS are all good options.


It's good to know that I won't go too far wrong. If there is no obvious reason to switch, I'll probably just stick with EXT4, seem it seems to be Ubuntu's default now.

As for the usage, it is mostly programming, with a focus on web applications. I run a number of databases and web servers. I'll often have a ton (50-100) browser windows open (between several different browsers). I'm running automated test suites almost constantly. I do a ton a screen sharing and voice chat with Skype.
Occasionally I'll (de)compress some large backups that could be a few GBs. But mostly I'm dealing with lots of small source files and lots of running applications (which may or may not involve disk IO).

Thank you!

---

### Post by kidders on 2011-01-19
> **phylae said:**
> The forums I was reading seemed to be referring to extra tools that I would install and schedule to run on a regular basis. Something like the Windows defrag tools.No, you could be right ... Some SSD manufacturers might well offer that feature. I can't imagine it being terribly useful though!

> **phylae said:**
> I'm not familiar with AoE.It basically just boils down to running the ATA protocol over an Ethernet (ie not TCP/IP) connection. It's no good for conventional file sharing, but is probably the most efficient way of accessing another machine's hard disk.

> **phylae said:**
> My understanding was that RAID 10 was usually faster than a single drive.That's generally true of HDDs, but it would surprise me if the same could be said for SSDs. One thing to be very careful of is that your SSD, partition geometry, RAID blocks/stripes & filesystems all be properly aligned. You'd be surprised how easy it is to take the edge off the performance of something like an SSD by rushing through your fdisk/mdadm/mkfs commands. On the other hand, if you get everything right, you should be able to minimise any long-term performance impact of running software RAID on your SSDs.

---

### Post by phylae on 2011-01-23
> **kidders said:**
> It basically just boils down to running the ATA protocol over an Ethernet (ie not TCP/IP) connection. It's no good for conventional file sharing, but is probably the most efficient way of accessing another machine's hard disk.
OK. Based on the other research I did, it looks like it won't be a serious option for me yet. But it is good to be aware of it.



> **kidders said:**
> That's generally true of HDDs, but it would surprise me if the same could be said for SSDs. One thing to be very careful of is that your SSD, partition geometry, RAID blocks/stripes & filesystems all be properly aligned. You'd be surprised how easy it is to take the edge off the performance of something like an SSD by rushing through your fdisk/mdadm/mkfs commands. On the other hand, if you get everything right, you should be able to minimise any long-term performance impact of running software RAID on your SSDs.
Sounds like I have a lot more reading to do. Thanks for pointing me in the right direction.


The hardware should be arriving in the mail within a few days, so I should have some results to post within the next week or two.

---

### Post by asmoore82 on 2011-01-23
I pass on simple words of wisdom that I only wish I could take credit for...

> A RAID is *not* a backup.

---

### Post by phylae on 2011-01-24
> **asmoore82 said:**
> A RAID is not a backup.

This cannot be repeated often enough!

I think I am fairly well covered in the area of backups. I use rsync to copy things I care about to a server on my local network. That server uses rsync to copy to another hard drive within the same machine. And I sync basically everything (except home videos, which I have on tape anyway) on that server to JungleDisk.

My main goal with RAID is to speed up recovery time in the case of a hard drive failure. Buying/replacing a drive is a lot faster than reinstalling/recompiling/recustomizing my whole environment.

---

### Post by phylae on 2011-01-31
Woohoo! My hardware finally arrived. After 3 days of Memtest86+ I have got Ubuntu installed!

It was actually quite a pain deciding on my setup. Here is what I ended up with:
[LIST]
[*]1 500MB partition on each drive for /boot. I know 500MB this is overkill. But I got sick of clearing out old kernals when /boot got full. These are set up as RAID1 with mdadm. I never tried it with RAID10. It is formatted ext3.
[*]Grub installed in the mbr of all 4 drives.
[*]The rest of each drive set up as a software RAID10 with mdadm. Gives me about 120GB.
[*]LVM running on top of the RAID10.
[*]3 Logical Volumes, RootLV is formatted ext4 and is 18GB, SwapLV is 16GB (just slightly bigger than size of RAM), and HomeLV is also ext4 and takes up the remaining space.
[/LIST]

It was quite a pain. I think I went through 4-5 installation attempts before it was successful. I think most of the pain was caused by the fact that I originally used GPT (i.e. GUID) for the partition table. It seems that a lot of tools, including the grub installer, don't like GPT yet. Once I switched to a standard MBR (gparted called it an "msdos" partition table), things started getting better.

In case anyone sees this and needs help, just PM me. I don't think I could write a full tutorial since I tried so many things, I don't totally understand *how* I got it working.

I good starting place is these links:
[LIST]
[*][http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html](http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html)
[*][http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)
[/LIST]
Those show how to install with RAID1 and LVM. The process I used was sort-of a combination of the two tutorials.



As a side note, I also tried using two RAID1 arrays with mdadm and letting LVM do the striping. I thought this could be more flexible because I could easily add 2 more drives in RAID1 later on, then just add them to the LVM volume group. However, when I ran the Ubuntu benchmark (System | Administration | Disk Utility) and bonnie the results came back with RAID1 + LVM being about half the speed for both read and write. As it stands with RAID10 + LVM, my home partition's average read according to Ubuntu's benchmark is 546.9MB/s. (Personal comparison, my laptop gets 20.5MB/s.)


Finally, I did a quick test that my RAID arrays are setup properly. I shut down, unplugged one of the drives (it happened to be /dev/sdb), then rebooted. The system came up fine (I previously opted to allow boot while degraded). I added a file to the degraded RAID10 array as a test.

mdadm detected the degraded arrays. But the system still totally worked. I did expect mdadm to send me an email (it didn't). I need to look into that.

Then I shut off, plugged the drive back in, and rebooted. Since the RAID10 array had changed while a drive was unplugged, it didn't automatically rebuild the array. (The RAID1 array didn't change so it came back at 100%.) I ran this:
```
sudo mdadm /dev/md1 --add /dev/sdb2
```
and about 20-30 minutes later the RAID10 array was no longer degraded.

I know I probably *should* test unplugging each other drive. But that needs to wait for another day.

Thanks again for all the great info. I've done **way** too much reading about RAID/LVM/grub/etc. in the past few days. But I guess it was worth it--it works! Maybe I'll post back again when I have got more of the system set up.

---

### Post by phylae on 2011-01-31
I thought it might be helpful to someone if I went back a directly answered my own questions.

> **phylae said:**
> 
The main will have 4 SSD drives (this one I think [http://www.crucial.com/store/partspecs.aspx?IMODULE=CTFDDAC064MAG-1G1](http://www.crucial.com/store/partspecs.aspx?IMODULE=CTFDDAC064MAG-1G1)). I would like to set them up with software RAID 10.

Software RAID was the way to go. I tried the FakeRAID that is built into the motherboard (Intel ICH10R). However, it wasn't working well. I have heard of some others getting it working (see below for the links). But the main argument in favour of it was the ability to dual-boot with Windows. I don't want dual-boot. mdadm seems to have better notification options when something goes wrong.

> **phylae said:**
> 
1) will it be possible to install Ubuntu directly to a RAID 10 setup (and boot from it)? I have seen some reports that older versions of Ubuntu could only install to RAID 0, 1, and 5.


I did grub from RAID1, and the rest (including /) on RAID10 + LVM. The reports about only being able to install Ubuntu on RAID 0, 1, and 5 refer to limitations in the installer's pre-defined RAID options. If you set up your partitions manually (using a LiveCD for example) then you can do almost anything you want.

> **phylae said:**
> 
2) I have read that TRIM is disabled when using SSDs in RAID. Should I be concerned about that? I have heard of some TRIM-like utilities than cause a greater load on the system, but are fine when run during down time. What are the recommended best practices for this?


I still don't know much about TRIM. I did enable AHCI in the BIOS, which theoretically helps in this area. But I don't know how to test to make sure it is having the expected result.

> **phylae said:**
> 
3) I have read that the SSD drives will last longer if a certain % (some say 20%) remains unused. Is this true? What is a good %? I have heard that using LVM to block of this % can make sure you don't accidentally write to it. Is that the best way to do it?


I did not allocate any space for this purpose. / has it's own 18GB logical volume. I expect 5-8GB of this will not be used.
I also have a 16GB swap logical volume. I also don't expect this to be used*. That gives me over 20GB that will almost never used so I think I am covered in this area.

*I am going to set up a UPS and have it trigger a hibernate during a power outage. That's the only time I expect to need swap. However, since a power outage is fairly rare (1/month at worst) this doesn't need the speed of SSD. If I find that I actually never use swap other than for hibernating, I will likely move swap onto a HDD.

> **phylae said:**
> 
4) In a RAID setup, how do I know if the array is in a degraded state? Do I need to set up some sort of monitoring or will I see an error message in GNOME?


It is possible to set up mdadm to send an email when it detects a problem.

I used this tutorial: [http://basskozz.wordpress.com/2008/12/07/how-to-setup-a-raid5-software-mdadm-array-w-email-notifications-via-gmail-the-easy-way/](http://basskozz.wordpress.com/2008/12/07/how-to-setup-a-raid5-software-mdadm-array-w-email-notifications-via-gmail-the-easy-way/)

I also found this one later, which probably would have been easier:
[http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/](http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/)

NOTE: When I manually disconnected a drive and booted, mdadm did NOT send me an email. I still need to figure out why.


> **phylae said:**
> 
5) I use VirtualBox for Windows occasionally. (Not my choice, but I have to check websites in IE and GoToMeeting doesn't support Linux.) I don't keep much on the Windows VMs, but the disk usage really adds up quickly. Probably 30-40% of my current disk usage is VirtualBox files. I'm assuming that network storage for these would be too slow; (my link to a fileserver is only 100Mbps). Do you think I'd be better off storing these on a standard harddrive to save space on the SSDs (and theoretically pro-long their life)?


I found an old 120GB HDD. I'm going to use that to store most of the VirtualBox hard disks. The 1-2 virtual machines that I use often, will have a small "hard disk" (about 5GB) stored on the SSDs. I'll install Windows and most programs on this drive. Then I'll add a 2nd "drive" which will be located on the 120GB HDD. This will be bigger (20-30GB) and will store any large files I need to work with, as well as any larger programs I need to install. Virtual machines I don't use often will just go on the HDD.
I think this will give a nice balance between space, performance, and the life of the SSDs.


> **phylae said:**
> 
6) Which filesystem do you recommend for the SSDs on RAID 10? I have read a lot of confusing things about which filesystems are good/bad for SSDs. My past machines have all been ext3/4. I'm quite happy to try something new. But I don't want to be super bleeding edge. I tried ZFS a couple years ago and that was too much pain. I don't want to go through the trouble of RAID only to mess something up with the filesystem.

I'm using ext3 for /boot and ext4 for the rest. So far I can't see a compelling reason to try any others (for this system) until zfs or btrfs are stable and well integrated.

> **phylae said:**
> 
7) Are there any other best practices, articles, blog post, or links you can recommend (relating to RAID 10 and/or SSD)?


[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

FakeRAID: [http://ubuntuforums.org/showthread.php?t=1573402](http://ubuntuforums.org/showthread.php?t=1573402)
FakeRAID: [http://ubuntuforums.org/showthread.php?t=1574765](http://ubuntuforums.org/showthread.php?t=1574765)

[http://aplawrence.com/Linux/rebuildraid.html](http://aplawrence.com/Linux/rebuildraid.html)

[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

Benchmarking with bonnie: [http://www.barricane.com/ssd-bonnie-benchmark-ocz-vertex-samsung](http://www.barricane.com/ssd-bonnie-benchmark-ocz-vertex-samsung)

[http://www.linuxdynasty.org/lvm2-how-to.html](http://www.linuxdynasty.org/lvm2-how-to.html)

Common LVM tasks: [http://docstore.mik.ua/manuals/hp-ux/en/5992-4589/ch03s03.html](http://docstore.mik.ua/manuals/hp-ux/en/5992-4589/ch03s03.html)
Very helpful, but not totally applicable to Ubuntu.

[http://www.howtoforge.org/install-ubuntu-with-software-raid-10](http://www.howtoforge.org/install-ubuntu-with-software-raid-10)

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

[http://www.rodsbooks.com/gdisk/whygdisk.html](http://www.rodsbooks.com/gdisk/whygdisk.html)
This convinced me to try GPT, but I think GPT caused most of my headaches.

[http://www.basicconfig.com/hex_codes_system_id](http://www.basicconfig.com/hex_codes_system_id)

[http://symbolik.wordpress.com/2009/05/01/howto-kubuntu-904-raid-10-lvm2-and-xfs/](http://symbolik.wordpress.com/2009/05/01/howto-kubuntu-904-raid-10-lvm2-and-xfs/)

[http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html](http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html)
Very helpful. This is close to what I did.

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
Some simple info on mdadm

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

---

### Post by phylae on 2011-01-31
> **phylae said:**
> 
NOTE: When I manually disconnected a drive and booted, mdadm did NOT send me an email. I still need to figure out why.


I just got the email about 10 minutes ago. This is several hours late. I'm not sure if the problem is gmail's fault or my configuration settings. Anyway, several hours late isn't too bad since this isn't a mission critical system. I'd likely have to run it degraded for a couple days anyway while I wait for a new drive to come in the mail.

---

### Post by srs5694 on 2011-01-31
> **phylae said:**
> I think most of the pain was caused by the fact that I originally used GPT (i.e. GUID) for the partition table. It seems that a lot of tools, including the grub installer, don't like GPT yet. Once I switched to a standard MBR (gparted called it an "msdos" partition table), things started getting better.

Actually, the GRUB 2 that the last couple versions of Ubuntu use work fine with GPT disks, although they can sometimes be a bit unreliable if you don't include a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) on the disk. There are also some issues with RAID and GPT, although I don't recall the exact details on that one. Chances are your problems were either RAID/GPT issues or you didn't include a BIOS Boot Partition.

---

### Post by phylae on 2011-01-31
> **srs5694 said:**
> ...you didn't include a BIOS Boot Partition.

That is probably it. I had a separate partition on each drive for /boot. But that was on RAID1. I did not create a BIOS Boot Partition.

This is good to know. I don't think I'll switch now because I can't see any immediate benefit to GPT for me. But next time I reinstall, I will probably try GPT again (and create a BIOS Boot Partition).

Thanks!

---

