---
title: "Dapper formatted my NTFS partition!?"
date: 2006-06-01
forum: Desktop Environments
---

### Post by u_ben_tu on 2006-06-01
I knew the risk, but I carefully read and followed the instructions when installing Ubuntu 6.06 to my hard drive.  

I had two existing Windows Partitions: C (5GB) and D (60GB).  I also had an Acronis True Image Recovery Partition.  The Ubuntu installer if I remember correctly offered to resize my large partition from 60gb to about 50gb and install Ubuntu on the free space.  Sounded good so I did that.  Ubuntu works fine, use it for a while, want to play a game and see how windows is doing...

I went back into XP which is running fine from my C drive, but Windows says my D drive is unformatted and RAW.  I did make a backup of some things on there before messing with Ubuntu, but I still have some stuff I would like back.  

Any idea what happened and how I can get my D partition back? ](*,)

---

### Post by BoyOfDestiny on 2006-06-01
[QUOTE=u_ben_tu]I knew the risk, but I carefully read and followed the instructions when installing Ubuntu 6.06 to my hard drive.  

I had two existing Windows Partitions: C (5GB) and D (60GB).  I also had an Acronis True Image Recovery Partition.  The Ubuntu installer if I remember correctly offered to resize my large partition from 60gb to about 50gb and install Ubuntu on the free space.  Sounded good so I did that.  Ubuntu works fine, use it for a while, want to play a game and see how windows is doing...

I went back into XP which is running fine from my C drive, but Windows says my D drive is unformatted and RAW.  I did make a backup of some things on there before messing with Ubuntu, but I still have some stuff I would like back.  

Any idea what happened and how I can get my D partition back? ](*,)[/QUOTE]

Well I'm not quite sure from the windows end...

However, from Ubuntu, go to System -> Administration -> Disks.

From there you can "mount" your drive to a folder. For example, if you make a folder on the Desktop called D.

iset the access path /home/yourusername/Desktop/D

From there, you will at least have read-only access. So you could copy to a usb stick or burn to CD just fine...

Trust me, it's easy, I made it sound sort of hard, but here is a sample screen shot.

You just pick the drive and partition, then choose a folder.

---

### Post by Enigmatic on 2006-06-01
Wow, almost the same thing happened to me.

I have 2 HDDs, three partitions on the one and just one on the other.

I said to resize my Windows parition by about 5GB less, and use the remaining space for the Linux install (4.5GB ext3 and 500mb linux-swap).

Somehow it failed, and says that the status of the Windows partition is unknown. (!), and says it is unformatted. 

I can no longer boot into XP either, it says "error loading operating system".

In the disks manager, it shows my other paritions with correct free space, and says they are accessible, but this one is inaccessible and unformatted.

I am really hoping I didn't just lose everything on that partition.

---

### Post by u_ben_tu on 2006-06-01
well the good news so far is I tried a couple of recovery utilties in windows, and the first two could not even read the RAW format but GetDataBack for NTFS after about 40 minutes of scanning and indexing shows all my files and is letting me recover them (I tested a few and they appear 100% original).  problem is I dont have a spare hard drive (its a shuttle xpc anyways - hard to hookup a second hdd), and I only have 2GB free on C so it would be alot of work.

I am just trying to decide if I should try restoring the MBR with True Image first (that would mess up grub i think) or try mounting the partition as boyofdestiny suggested and then burning everything to DVD+RW to save time.... hmm.

at least its there. :)

---

### Post by c0njur on 2006-06-01
OMG the same thing just happend to me!

I tried to create an ext3 partition out of the free space on my NTFS, and now it says that the partition is unformatted and inaccesible. It won't allow me to mount it to a folder or do anything!

Somebody please tell me all my Windows files are not gone!

---

### Post by u_ben_tu on 2006-06-01
I decided to take the safe and slow route and backup my files with GetDataBack (NTFS) across my home network.  However I have a large program files directory with alot of programs installed, that I am not going to backup due to the size.  Worst is I will just have to reinstall them, but I will try to restore the MBR using True Image (lucky it makes a backup of that when installing the "Startup Recovery Manager").  Sad to see others are experiencing this, I expect more will.  I know I carefully read and followed the installer.  Seems the resize and use free space option is dangerous for windows partitions!

---

### Post by Horizon on 2006-06-02
Someone really needs to write a disclaimer advising people that if they're dual booting they should resize their partitions in Windows first. 

Gparted seems to only work when it feels like and just _loves_ failing to say...resize a drive but still decides it's necessary to carry on with the next actions, although i heard they fixed it i'd never trust it with a drive that has data on it. 

The same goes to whatever the text installer uses, windows partitioning software is always much more reliable/just plain better unless dealing with ext2/3...And even then partition magic is probably better at handling linux drives as well.

---

### Post by beameup on 2006-06-02
I had originally set up this machine with Xandros/XP and it wouldn't partition the drive. Someone recommended I use the System Rescue CD (or a Knoppix live disk) to run QTParted to setup my partitions before setting up a dual boot. That has worked fine. 

Have you tried the FIXMBR Repair option in XP?

[http://www.sysresccd.org](http://www.sysresccd.org)

---

### Post by GuyveR800 on 2006-06-02
I used the Live CD installer and manually created some new partitions for ubuntu in unused space, but the next step (formatting the filesystems) tried to reformat my NTFS partitions in stead!

I used the back button to take note of the right partition numbers and then edited them manually to make sure the installer didn't overwrite any windows partitions.

In the old text installer partitioning and filesystem formatting went in 1 step, it was very convenient.. This new way seems to be error prone.

---

### Post by Zdravko on 2006-06-02
> 
In the old text installer partitioning and filesystem formatting went in 1 step, it was very convenient.. This new way seems to be error prone.
 

I agree with you! Although I managed dual-boot without ever touching windows partitions. I just used the forums here!

---

### Post by PriceChild on 2006-06-02
Yeah... i always use the old 5.10 text installer to partition my drives, Even gparted inside my running ubuntu throws up errors.

---

### Post by steve.horsley on 2006-06-02
I don't trust that new installer. I repartitoned to install Dapper, but I used a live CD to back up my partition table, then used the gparted live CD to do repartition and reformat, and then took another backup of the partition table before letting the installer have its turn. As it happens, gparted and the Dapper installer both behaved themselves, but I have seen a prerelease of the Dapper installer change the **starting** cyinder of NTFS even when not told to resize anything, and my bug report doesn't say that it's been fixed.

---

### Post by dglock on 2006-06-02
The new partitioner is more flexable but you have to watch the right hand colloum where is says format. If there is a check in the box beside a partition it will be formated! 

  If you don't want that partition formated, remove the check mark.

don

---

### Post by cjwatson on 2006-06-02
In order to investigate this, I need bug reports on the 'ubiquity' package; after filing the bug report, please use the "Add Attachment" link to attach /var/log/installer/syslog and /var/log/partman (or /var/log/installer/partman if you've rebooted into the completed installation).

---

### Post by u_ben_tu on 2006-06-02
The installer only said it would resize my D partition and take the free spacefrom it.  It never said anything about formatting it.  
It doesnt appear to have formatted my D partition, or converted its filesystem because I was able to recover all my data 100%.  I am not exactly sure what happened.  I had no problems back when I installed Fedora Core 5 and let it re-partition...
I have always used Acronis Disk Director for things like this, but I wanted to give Ubuntu a chance, because I always hear how easy its supposed to be, and how it "just works".  I don't think those people are being completely honest.  This is a major bug imo.

No hard feelings, but I am not going to retry this - or Ubuntu for another 6 months. [-(

[edit] I see cjwatson just posted, I wish I could get those logs, but I had to delete the ext3 partition to make a free space drive to recover my files from my D (ntfs) partition. :(

---

### Post by mannheim on 2006-06-02
[QUOTE=steve.horsley]I don't trust that new installer. I repartitoned to install Dapper, but I used a live CD to back up my partition table, then used the gparted live CD to do repartition and reformat, and then took another backup of the partition table before letting the installer have its turn. As it happens, gparted and the Dapper installer both behaved themselves, but I have seen a prerelease of the Dapper installer change the **starting** cyinder of NTFS even when not told to resize anything, and my bug report doesn't say that it's been fixed.[/QUOTE]

I added a comment to [your bug report.]("https://launchpad.net/distros/ubuntu/+source/parted/+bug/32529") It sems pretty bad to me, that Dapper goes final with a **confirmed** bug titled "Installer Corrupting Partition Table", and there's not a word of warning. It does seem that the Dapper download page needs a prominent link to a "Known issues" readme file.

---

### Post by u_ben_tu on 2006-06-02
[QUOTE=mannheim]I added a comment to [your bug report.]("https://launchpad.net/distros/ubuntu/+source/parted/+bug/32529") It sems pretty bad to me, that Dapper goes final with a **confirmed** bug titled "Installer Corrupting Partition Table", and there's not a word of warning. It does seem that the Dapper download page needs a prominent link to a "Known issues" readme file.[/QUOTE]

thanks I hope this gets fixed.  
i neglected to mention that restoring the MBR with True Image did not help.  
+ my C partition was a primary ntfs and my D was a logical ntfs partition.

---

### Post by buffalobum on 2006-06-02
i had a similar experience, and now i have a yellow caution symbol next to my partitions in the installer, and when i close out and boot XP, the drive isn't even recognized in windows explorer.  anyone have any idea what i can do to get my files back?

---

### Post by garba on 2006-06-02
Yes, we definitively need a disclaimer somewhere, resizing ntfs partitions is way too risky.

---

### Post by percy1 on 2006-06-06
[QUOTE=garba]Yes, we definitively need a disclaimer somewhere, resizing ntfs partitions is way too risky.[/QUOTE]

Not to mention Fat32 partitions!

The same thing happened to my Fat32 XP install. Luckily I was able to recover all of my files with a windows undelete utility.

---

### Post by srunni on 2006-06-06
Similart thing happened to me about 6 months ago with Breezy. I just upgraded to Dapper (up until 3 last night setting it up), but I don't dual boot - I run it as a guest OS in XP, which works out AWESOME and I don't have any problems with Linux screwing with my XP. :p

[[IMG]http://img120.imageshack.us/img120/7365/dapperdrakeinvmware1xc.th.jpg[/IMG]](http://img120.imageshack.us/my.php?image=dapperdrakeinvmware1xc.jpg)

---

### Post by Dertiger on 2006-06-06
I resized my NTFS to install Dapper, and now Windows won't boot.  It gets to the Win XP splash screen, dumps to a bluescreen for a fraction of a second, then reboots.  Is my windows installation recoverable?  What tools can I try using?

I can access the files from within Ubuntu, so I know all is not lost.  But how can I detect what files were corrupted?

---

### Post by jz32300 on 2006-06-06
Hi Everybody,

I'm glad a found this thread - I was just about to install Ubuntu 6.06 as a dual boot on a Windows XP machine.

I was going to use Partition Magic first to create a fresh and empty / unformatted partition before attempting an install - maybe I should wait?

Any advice?

> 
I run it as a guest OS in XP

srunni - what does that mean and how does it work?

Thanks

---

### Post by msandersen on 2006-06-15
[QUOTE=jz32300]I was going to use Partition Magic first to create a fresh and empty / unformatted partition before attempting an install - maybe I should wait?

Any advice?

srunni - what does that mean and how does it work?[/QUOTE]
Always good to back up your data before messing with your hard drive. One of those things we know we should but don't always get around to doing.
I never trusted Linux with partitioning, I've read too manyu horror stories on support forums in the past, like a rounding bug that affected all Linux distros using Parted when moving to the 2.6 kernel. Totally messed up the partition tables. 
I've always used Partition Magic. I don't partition unless I have to, though. Always risky. But PM has never messed up for me.
You could also try the Alternate CD, I've read others in this forum recommending that due to some people having trouble with the new graphical one on the main CD. I think the Alternate's got the old text installer. I upgraded from it, so don't know exactly.
It goes without saying, but it also pays to pay particular attention at the partitioning/formatting stage, don't click forward too quickly.

Srunni is using [VMware]("http://en.wikipedia.org/wiki/VMWare") Workstation, a virtualisation program, running on Windows Vista it seems. It installs a guest OS as a large file and runs it inside a window, so if you mess up, you can trash it and revert or reinstall. If you run a server in it and someone hacks it, they can't get to your main system, and you can simply trash it and restore a backup.

---

### Post by Agent86 on 2006-06-15
Prior to installing Xubuntu Dapper, I used the Gparted LiveCD 0.2.5 to resize an NTFS partition and create FAT32, ext3, and Linux swap partitions in the unallocated space, with no problems at all. I used the LiveCD because the Gparted version on that was more recent than the one on the Dapper release.

Before using Gparted to resize the NTFS partition, however, I used Windows 2000 to defrag the drive.

I agree that you have to watch the "Format?" checkboxes carefully on the Dapper partitioner, though I'm sure it defaults to just partitioning the swap and / partitions.

---

### Post by Dertiger on 2006-06-15
Thanks for the reality-check.  I came unto this assuming the Linux tools would be more stable and reliable than their Windows counterparts.  I've learned a lot about OS's through this process - it seems that desktop linux is a relatively new concept, so while Linux is stable as a kernel and server, maybe the desktop side still has some work to do.  It's great to see the speed at which progress is being made, though!

Regarding my problem not being able to boot XP, I think this has a simple fix, I just don't know how to fix it.  From Linux, I can mount the NTFS partition and access the files so I know they are not lost (the important ones are are backed up, anyway).  I think it is just recoverable corruption in the boot record - but how do I go about finding out, and what tools are out there to fix it?

---

### Post by xenomorph99 on 2006-06-15
[QUOTE=GuyveR800]I used the Live CD installer and manually created some new partitions for ubuntu in unused space, but the next step (formatting the filesystems) tried to reformat my NTFS partitions in stead!

I used the back button to take note of the right partition numbers and then edited them manually to make sure the installer didn't overwrite any windows partitions.

In the old text installer partitioning and filesystem formatting went in 1 step, it was very convenient.. This new way seems to be error prone.[/QUOTE]

Well, if they can't even get updating an Nvdia driver correct, I'm not surprised if people are losing their partitions so readily.

---

### Post by TheMono on 2006-06-17
Acronis Disc Director Suite! Saved my *** numerous times during the attempt to setup dualboot - not that I ever had any issues, but that was as a direct result of that software. Also includes an OS selector, so you will boot to an acronis screen which will let you select and OS from there - it automatically picked up both Ubuntu and XP.

---

### Post by Acesomeone on 2006-06-17
Hi,
I've had the exact same thing happen to me and I'm still stuck. I've tried just about anything, but I can't get anything to work except for Ubuntu, which is fine in itself, but I'd like Windows working again for several reasons. I had two disks, and during the install of Dapper, they were both screwed up due to the resizing-while-it-should-resize-issue. Numerous tools tried to recover the MBR or fix cylinders, but nothing really works. Windows installation starts, but hangs after the first stage (going from text to graphical) - and by that time my linux partition will have been ruined too.

Does anyone know a fix for my harddrives? I think one's completely lost already, the other one, I've still got hope for...

Greetings,
Glad to see I'm not the only one :)

---

### Post by guyg on 2006-06-23
Almost exactly same thing happened to me. Now I have to restore my Windows to factory settings. Luckily it's new machine so no data was lost...

This resize feature seems to be unstable. The installer should either include a warning to that effect, or it should be completely removed.

---

### Post by Acesomeone on 2006-06-24
Yeah, but it seems my hard drive is now corrupted. No way to get partitions removed or changed, nor boot up, let alone install Windows.. :-s

---

### Post by The Raven on 2006-06-27
[QUOTE=Acesomeone]Yeah, but it seems my hard drive is now corrupted. No way to get partitions removed or changed, nor boot up, let alone install Windows.. :-s[/QUOTE]

Third party disk partitioning software is a must for everybody that keeps anything important on their system.

I use Partition Commander and have been using the same disc for the last four years and it rules. P.Comm. handles NTFS and Fat (16, 32; etc.) file systems. It will optimize your MBR, MFT's, and allow you to determine disk compression, independent volume sizing...all the goodies!

You can reformat and configure partitions before the O.S. install and name the partition for easy identification when assigning your O.S. install a partition to nest.

I have seen your problem before, your MFT got corrupted. Your data is still there, it's just that all the address assignments got moved/shifted. Get a third party recovery cd/ P.C. Rescue disk and go into re-aligning your Windows MFT and  addresses.

MBR=Master Boot Record (this is what GRUB and LILO read regarding present O.S.'s)
MFT= is a Master File Table (like a phonebook with all of the numbers to your O.S. system files and installed software.)

If you haven't already reformatted your HDD, don't do it, get a Rescue Disk at Staples, or Office Max or some place similar with tech.'s that might be able to assist you in your purchase requirements.

---

### Post by The Raven on 2006-06-27
I recently installed UBUNTU, about a week ago, and I am not sure if it was a glitch in the disc ISO image or the install was operationally corrupted.

 I installed UBUNTU once, only to wind up having two MFT entries for UBUNTU and both have their own diagnostic start up routine entries in GRUB. The present O.S. options are: one for Kernel make 25 and make 23 colocated but independently operational, and of coarse Windows XP Home. I got UBUNTU siamese twins joined at the Kernel. What's that all about anyway...weird.

 UBUNTU needs to handle I.E. v.6 desktop web page shortcuts a little better than a text file with a base URL. That could be resolved with a simple script addition to UBUNTU. Not exactly worthy of the Nobel Peace Prize but convenient, extremely convenient. What do they call that...transition, uhh, they call that migration in IT circles. Suite, I mean sweet!8)

Do youbuntu?

---

### Post by Agent86 on 2006-06-28
[QUOTE=The Raven] I installed UBUNTU once, only to wind up having two MFT entries for UBUNTU and both have their own diagnostic start up routine entries in GRUB. The present O.S. options are: one for Kernel make 25 and make 23 colocated but independently operational, and of coarse Windows XP Home. I got UBUNTU siamese twins joined at the Kernel. What's that all about anyway...weird.[/QUOTE]This is normal if your kernel is upgraded - you'll get the option to boot either kernel at the GRUB menu. Default boot should be the new kernel (-25), but you have a chance to boot the older (-23) kernel (because you've compiled drivers/programs against that older kernel, for example).

---

### Post by Dertiger on 2006-07-01
To anyone with a corrupted windows partition after installing Dapper - I'm writing this from my recovered XP partition!

Solution was simple.  Run the Recovery Console from the bootable XP disk.  Run CHKDSK /R and in about 10 minutes it will complete.  Reboot, and hopefully you'll have a working Windows parition, like mine.

Of course, I've been forced to spend so much time in Ubuntu I think I am going to go with it full time...

---

### Post by ss0007 on 2006-07-02
hey thx man , 
why cant u post it in a seperate thread or in a "How to's" guide section ?

This is a crucial bug in grub and ppls can know the solution easily in a single search  !!!!

---

### Post by Acesomeone on 2006-07-02
I don't understand how a hard disk can get so messed up by just installing Dapper... :-s What kind of a bug is this anyway...

---

### Post by mejohnsn on 2006-07-27
After reading many of the posts in this thread, I have decided not to use
GParted when I finally do move partitions around, creating new partitions for Ubuntu. I think I will use parted instead, maybe qtparted.

But I do know one thing for sure: we will never understand "how a hard disk can get so messed up by just installing Dapper" as long as people tell us so _little_ about their setup and what they did before having the problem!

Please, _please_ tell us more: those of you whose partitions went away (or appeared unformatted), what options did you choose during the install process? Can you give us the output of parted and mount before and after the problem? At what point did you notice that the partition appeared unformatted? Did Windows report this? Did it report it while trying to boot? Did it report it in Windows Administrative Tools?

Please recall that 'sudo parted /dev/hda print' will display the Linux view of the partitions on /dev/hda, which as 'man MAKEDEV' explains, is the first whole disk controlled by the primary IDE controller. On a typical WinXP installation (and quite a few non-typical) your C: and D: (if applicable) drives are under this controller (usually hda1 and hda2 resp.).

BTW: this is a handy hint. If you want to know what all those mysterious device names under '/dev/' mean, look at 'man MAKEDEV'.

---

### Post by shazbot on 2006-07-28
My first and second install using Dapper over wrote most of Wiindow XP partion, leaving me with a MBR which tried to boot windows but then crashed, as it was a new machine it was not a worry, but am fairly sure that it was du to modify the suggested partion size

Third attempt I left the suggested partion size and had both boot A Ok

So I do agree with an earlier post the resize partion seems unstable

anyway Ubuntu is great, can't as yest remplace Window because of ceratin programs and games that I need, but maybe one day :)

---

### Post by it.henrik on 2006-07-28
After many years of dualbooting and installing linux every now and then here and ther I never does anything to a harddrive that I cant entirly wipe if I cant set it up wit partition magic first. 

So many lost backups and so much frustration. ahh .. I feel like crying just by thinking of it ...

Partition Magic is a must (atleast until GParted gets to 1.0).

---

### Post by Jhongy on 2006-07-28
I agree. I initially installed Dapper on an 80gb IDE disk... it played nice with the WinXP partition, but I nixed then recreatd an existing partition to perform the install.

Then, having been bitten by the Dapper Bug (TM), I reinstalled Dapper on a (pre-created) partition on a brand spanking new SATA drive. I tried initially creating the new partitioning scheme using fdisk, but in the end resorted to using Partition Magic from Windows when it wouldn't work. I also notice now that my IDE partition, which has long since been converted back to a FAT partition, is borked -- warnings and errors on (Linux) bootup, and a yellow exclamation mark in the installer. Something obviously went pretty horribly wrong with the partitioning in the installer.

Fortunately the data is intact and fine. In fact, I'm reluctant to try to fix the problem when all is working....

P.S. I would NEVER dare to resize a partition with data on it that I really cared about.

---

### Post by The Raven on 2007-04-04
Closing off this post it is most definitely the case where Ubuntu Dapper Drake had taken it upon itself to additionally install the kernel version 25. My largest complaint with this scenario some time ago is simply: if I didn't say put it there or in do not put it there or in. Period.

People obsessively b****h about Windows doing this same very thing for a reason and these same people use Linux like Ubuntu to get away from that kind of crap.

Now at the time of installation of Dapper the kernel was stable as of version 23 and a release candidate at version 25. Common sense would tell anyone that if I was installing Ubuntu Dapper D that I was looking for a stable version of the kernel (23) before I would consider the RC kernel (25). If I was a developer or tester I would install the kernel RC.v.25 and would be asking developer questions NOT install questions!!! Get it?

The importance of having a hard-drive partitioning tool can not be stressed enough. I myself utilize the services of Partition Commander and have done so for the last four years with the same version and it still kicks butt.

Word to the wise: the fact that you can eradicate partitions if something goes wrong is an excellent saving grace but one that should be left as a last resort. Just erasing a partition to start over from scratch is not going to teach you anything. That is what these forums are for and why everyone here is welcome whether other people think so or not.

Have a good one and I'm glad you are here with me!

---

### Post by The Raven on 2007-04-04
.(\ /)
(O.o)
(> <) You see this.

Is this a bunny or a Hamtaro?
That is cool.

---

