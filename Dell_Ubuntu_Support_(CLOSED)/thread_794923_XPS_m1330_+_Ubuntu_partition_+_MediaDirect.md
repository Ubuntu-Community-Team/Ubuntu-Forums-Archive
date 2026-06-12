---
title: "XPS m1330 + Ubuntu partition + MediaDirect"
date: 2008-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rafalr on 2008-05-15
Dell XPS M1330 2 GHz/2GB/160GB Nvidia Ge8400GS 

I spend the whole day reading through what is available on internet and it seems that there are mixed/contradictory solutions for problem:
> The Dell Direct button will trash your partition table and make the system unbootable even if you get rid of the extra partitions. The answer is that MediaDirect hides a small chunk of boot code in a hidden partition called a "Host Protected Area" or HPA, which most partition editors (included gparted) cannot see or touch. The button apparently enables this partition for booting, and whatever sloppy code is in there trashes your partition table and/or MBR if it does not find things the way it expects them.

Apart from messing around with 
```
E:\dellkit\rmbr.exe DELL X Z
```
which apparently renders only 50% success, the simplest solution seems to be installing Ubuntu & grub on one of primary partitions and not to change the way that (1) power and (2) MediaDirect buttons are prescribed to (2) Vista and (2) MediaDirect/XP systems.

Actually as you may know "simplest" is not simple, because Dell very wisely has stripped us from possibility of using primary partition - again "simply" they took from us all available primary partitions leaving us with (again simple) decision which primary partition we should delete.

My partitions look like below:

sda1 (fat16) 117,6 MB - EISA/config Dell
plus small (0,4 MB) hidden/free partition
sda2 (NTFS) 10 GB - Recovery (D:/)
sda3 (NTFS) 136 GB - Vista (C:/
plus zero size hidden/free partition
sda4 (extended) 2,5 GB
sda5 (logical, fat32) 2,5 G - probably Media Direct

The question is:
- can MediaDirect partition be safely deleted ? (safely means that MediaDirect button is DEAD and harmless)
- if not, can the recovery partition be safely deleted ? (safely = withou affecting other partitions / systems behaviour).

I have not yeat touched any partition or installed/re-installed any of the systems/components. Wiping disk and reinstalling is not an option for me - I have to do it the right/clean way for the first time and can not afford multiple re-installations I know some people had to go through.

Your thoughts very much appreciated.
Rafal

---

### Post by sdennie on 2008-05-15
I have an XPS m1330 (Vista edition) and, upon pushing the power button for the first time, I stuck in an Ubuntu install CD and immediatly deleted all Vista/Dell partitions and installed Ubuntu across the entire drive.  No adverse effects at all.

---

### Post by OffHand on 2008-05-15
The keywords are 'logical partitions'

---

### Post by OffHand on 2008-05-15
> **rafalr said:**
> 
The question is:
- can MediaDirect partition be safely deleted ? (safely means that MediaDirect button is DEAD and harmless)It can be deleted. I did delete it. I am not sure if it will disable the button but it seems rather logical to me that it does.
> **rafalr said:**
> 
- if not, can the recovery partition be safely deleted ? (safely = withou affecting other partitions / systems behaviour). Why would you? Just make a few logical partitions. Like /home and swap. You cannot have a logical partition inbetween 2 primaries though iirc.

---

### Post by rafalr on 2008-05-15
Hi,

It is not that simple - have you tried (after deleting the MD partitiuon) to push the MD button while the laptof is off ?

If you Linux partition survives it, then I take it for granted MD partition can be delated safely. 

Many warnings I rad say that there is some HD area where a scriupt is residing that upon hitting MD button will attempt to re-construct the initial partition - of course damaging you Ubuntu installation. That is my major concern.

Rafal

edit: there is an interesting thread with quite enlighted explanation/advise of "dg1261" also here
[http://www.dellcommunity.com/supportforums/board/message?board.id=vista&message.id=57903&query.id=163660#M57903](http://www.dellcommunity.com/supportforums/board/message?board.id=vista&message.id=57903&query.id=163660#M57903)

---

### Post by thorcik on 2008-05-15
> **rafalr said:**
> It is not that simple - have you tried (after deleting the MD partitiuon) to push the MD button while the laptof is off?
I did try this, as You can see it works fine up to now :o)

---

### Post by rafalr on 2008-05-15
OK, man my life is in your hands

can you specify what was the setup of your partitions before (that is a brand/factory new laptop) and after (that is after repartitioning and installing Ubuntu) ?

Like number of partition, space, name/purpose and type ?

And what specific path you followed while repartitioning ?

I plann the following operation:
- removing the 10 GB recovery partition
- making new 5-7 GB primary as ext3 to be mounted at /
- shrinking the Vista primary to free around 100 GB
- combining the released 103 GB under extended, by
- making another two logica partitions:
swap 2 GB, and
/home 101 GB as reiserFS

Grub to be installed on the 5-7 GB primary together with /

 
so the status before:

   1. primary: 118MB "EISA" (actually, a FAT16 Dell Utility partition)
   2. primary: 10 GB "Recovery" (the Vista recovery partition)
   3. primary: 140 GB partition for Vista
   4. extended: 2.5 GB container encompassing:

    * 2.5 GB NTFS partition for MediaDirect 3.

and planned status after

   1. primary: 118MB "EISA" (actually, a FAT16 Dell Utility partition)
   2. primary: 7 GB Ubuntu ext3 at /
   3. primary: 40 GB partition for Vista (resized)
   4. extended: 2.5 GB container encompassing:

    * 2.5 GB NTFS partition for MediaDirect 3.
    * 2 GB swap
    * 101 GB Ubuntu reiserFS at /home

I wonder if this is going to work and if you did it similar way (except deleting MediaDirect primary parition) ?

rafal

---

### Post by OffHand on 2008-05-15
> **thorcik said:**
> I did try this, as You can see it works fine up to now :o)

You wiped the MD partition (like me) and nothing happened when you pressed the MD button?

---

### Post by OffHand on 2008-05-15
Just keep in mind that you can only have 4 primary partitions (dell diagnostics is taking up one primary slot). Logical partitions should come after the primary partitions, not in between them.

P.S. Install Vista first. Ubuntu will see Vista but not the other way around.

P.S. 2 Ubuntu (OS partition) should be on a primary. In general bootable partitions should be on a primary partition.

---

### Post by jespdj on 2008-05-15
I have an XPS M1530 with Windows Vista and Ubuntu 8.04 on it. I deleted the Media Direct partition, because I figured that Media Direct is a gimmick that I don't need.

When I start my laptop by pressing the Media Direct button, it displays the Media Direct screen, and on top of that I see GRUB (it looks messy), and then my laptop boots into Ubuntu normally.

So, pressing the Media Direct button does not mess up the partition table.

Note that there have been different versions of Media Direct in the past. As far as I remember, the "host protected area" was only used with older versions of Media Direct. MD3, which is on the M1330 and M1530, uses a different scheme. See this: [Understanding the Dell MediaDirect Partition](http://www.goodells.net/dellrestore/mediadirect.htm) - it says:

> Introduction to the HPA

(Update: The HPA is used only for MediaDirect versions 1 and 2. With MediaDirect 3, Dell has switched to installing MediaDirect in a logical partition instead. The information that follows applies to MediaDirect 1 and 2.)

---

### Post by thorcik on 2008-05-15
> **rafalr said:**
> OK, man my life is in your hands

can you specify what was the setup of your partitions before (that is a brand/factory new laptop) and after (that is after repartitioning and installing Ubuntu) ?

Like number of partition, space, name/purpose and type ?

And what specific path you followed while repartitioning ?

I don't remember how big were the installed partitions, anyway the big one was Vista, about 10 gigs took the recovery partition and media direct another 2 gigs, I suppose. And I think there was a tiny, empty one too. The whole disk is 120gb.

Now I have:
sda1: 9.6gb, "/"
sda5: 40gb, "/home"
sda6: 4gb, swap
sda7: 40gb, "/media/sda7"
sda8: 21gb, "/media/sda8"
all except swap are ext2

As for what I did it was simple - removed all partitions and made new ones. easy, isn't it? ;o)

---

### Post by rafalr on 2008-05-16
hello all,

So I did a great job preparing really neat, ideal partitioning:

1. primary: 118MB "EISA" (FAT16 Dell Utility partition)
2. primary: 7 GB (ext3)
3. primary: 40 GB (NTFS) shrinked Vista partition
4. extended: 103,5 GB containing:
* 2 GB swap
* 99 GB reiserFS
* 2.5 GB NTFS partition for MediaDirect 3.

The first one and the last has been neither resised nor moved - just left absolutely intact. Vista partition and former Recovery partition have both been resized and moved slightly.

After that having completed (from a Hardy Live CD) I exites Live CD system and rebooted woth power button. Vista is dead - laptop reports that no bootable disks found, but I though this was not a disaster, as grub will find the Windows installation and list it.

Then MediaDirect button - a short MD logo screen and then all dead: no bootable disks found. I then thought to hell with MD - I will just wipe out the last small partition and enlarge the /home partition.

But then back booting Hardy Live CD I was astonished that the while 149,5 GB space (strangely on a 160 GB disc) is an "unallocated", raw space !

So it seems that each attempt to change partitioning and hitting MD button afterwards will ruin whatever you did with partitioins and any data in it.

Now, I am REALLY set to anihhilate that bloody MediaDirect remnants (anything that was on HD evaporated anyway), and I guess the missing 11,5 GB on my HD has something to do with 
it. I just need to find a good way to nuke the hidden thing and make whole HD as raw and deleted as possible ... I actually consider placing the laptop in an oven for 10 minutes :guitar:

.. well, it could actually be a slight overkill.

if any of you geeks know how to find whatever is hidden and have it wiped/nuked - I am here to test it.

rafal

---

### Post by nrayever on 2008-05-16
hi guys:

i have a better challenge for you. is there a way to boot 2 different linux flavors, the 1st one with the power button and the other one with the media direct button?

i would like to do this to have install in the md partition a linux media center type distro and use as that, no instant messaging, no office related apps, etc.. just the essential to run elisa or mythTV.

i believe that should be possible. and i believe that the answer is on the mbr. well i guess...

if someone had any better idea, any suggestion or guide to do it would be appreciated.

nrayever

---

### Post by rafalr on 2008-05-18
Hi all,

So I effectively nuked the thing using live Knoppix CD, and entering as root

```
 dd if=/dev/zero of=/dev/sda
```

I read this is a really bad, nasty command, capable of smoking anything on HD and that is what I needed and that is what worked ... almost.

Of course it also wiped the partition table, so Hardy Install CD was even not able to build any new partitions - it first had to bild a new/fresh MBR/partition table.

Although pressing both power and MD button simply starts Grub now, when I do it via MD button then still the hated Media Direct screen/logo appears for a moment, so it indicates that some remnants of this code or simply a jpg file with the screen stays embedded on the HD.

Ah, and I did not recover the full 160 GB - only 149,5 could be partitioned, which shows that Dell really messed up the disk with their rubbish-windows-media junk.

For those of you who are perfectionists there is supposed to be Seagate Disc Utility CD, but this was too ambitious for me ...

Rafal

---

### Post by nrayever on 2008-05-20
> **rafalr said:**
> Hi all,

So I effectively nuked the thing using live Knoppix CD, and entering as root

```
 dd if=/dev/zero of=/dev/sda
```

I read this is a really bad, nasty command, capable of smoking anything on HD and that is what I needed and that is what worked ... almost.

Of course it also wiped the partition table, so Hardy Install CD was even not able to build any new partitions - it first had to bild a new/fresh MBR/partition table.

Although pressing both power and MD button simply starts Grub now, when I do it via MD button then still the hated Media Direct screen/logo appears for a moment, so it indicates that some remnants of this code or simply a jpg file with the screen stays embedded on the HD.

Ah, and I did not recover the full 160 GB - only 149,5 could be partitioned, which shows that Dell really messed up the disk with their rubbish-windows-media junk.

For those of you who are perfectionists there is supposed to be Seagate Disc Utility CD, but this was too ambitious for me ...

Rafal

hi rafal:

that logo isn't embedded on the hd. i firmly believe that it's embedded on the bios. because when you press the md button, the normal dell screen is not showed. this means (at least to me) that the bios is managed from 2 different signals that shows 2 lightly different bios. so when you press the normal power button it calls the first part of the bios code (the one that lets you change stuff on it, as password, etc..) and when the md button is pressed a second part of the bios is called (the one that boots the md partition.) the bios surely checks somehow that the partition is there. and if not, it boots kind of normal mode.

there are several threads in other forums that discuss about dual booting Linux using the md button. some of the had succeeded.

and as i had commented on my first post, i would like to make a dual Linux-Linux boot with the md button to boot a light media center using Elisa or myth TV. that would be more useful to me than booting windows-Linux or vice versa.

well on the other hand. you don't need a proprietary software to wipe your hd. i can suggest you to download UBCD (Ultimate boot CD). it has a lot of great hd partitioning utilities. 

i don't know why you are telling that hardy was not able to set the mbr. seem strange. but if you're installing from a live cd use gparted or install qt-parted to create a valid mbr and partitions.

hope this helps you.

nrayever

---

### Post by rafalr on 2008-05-21
Hi,

By saying
> Of course it also wiped the partition table, so Hardy Install CD was even not able to build any new partitions - it first had to bild a new/fresh MBR/partition table.

I did not make myself clear enough. It should read:

Of course it also wiped the partition table, so Hardy Install CD was even not able to build any new partitions RIGHT AWAY - it (= Hardy Live CD, with GParted on it) first had to build a new/fresh MBR/partition table.

So of course, Hardy was capable of building new MBR.

I used Knoppix to issue the dd if= ... command simply because that is what was inserted the CD drive at that moment :)

rafal

---

### Post by VayHow on 2008-05-22
Maybe I'm the person you're looking for, coz I've looked deeply into this issue and tried almost every possibility with re-installation again and again(That's really exhausting). Anyway, I've figured it out. Now I have MD3.3, Vista Home Premium & Hardy on the same disk, no function missing. While my laptop(XPS M1530, similar to yours) is off, it will boot to MD(actually an embedded xp)if I press the MD button, or display grub menu and let me choose if I press the power button. Furthermore, while in Vista, if I press MD button again, I can use MD inside windows normally. If in ubuntu, nothing happens. And all these above operations will make no change to partions, in a word, everything's absolutely fine.

I just read the posts on first page of this thread, and there seems 2 mistakes according to my experience: 1. Hardy doesn't need to be installed on a primary partition. I guarantee you. 2. If you only use the Vista DVD to divide partitions on the whole hard disk and installed Vista(Ubuntu doesn't affect), no MD, you'll lose all your data and partitions and can't boot to OS if you press MD button while the laptop is off, coz the MD will modify your partition table. I've tried this. The reason is that MD button connects to something in the firmware, so if there's no MD partition to "match" it, then the partition will be destryed. But if you use Hardy to devide hard disk space, and install ONLY ubuntu to the whole disk, then do the same operation, I think nothing harmful would happen and it will boot to your Hardy, though I havn't tried this way.

---

### Post by walker9010 on 2008-05-22
did you resize your partitions at all? I also struggled with this issue for a while, and finally decided to hell with it and wipped the partitions and did a clean install.

---

### Post by Aurorion on 2008-05-24
> **VayHow said:**
> Maybe I'm the person you're looking for, coz I've looked deeply into this issue and tried almost every possibility with re-installation again and again(That's really exhausting). Anyway, I've figured it out. Now I have MD3.3, Vista Home Premium & Hardy on the same disk, no function missing. While my laptop(XPS M1530, similar to yours) is off, it will boot to MD(actually an embedded xp)if I press the MD button, or display grub menu and let me choose if I press the power button. Furthermore, while in Vista, if I press MD button again, I can use MD inside windows normally. If in ubuntu, nothing happens. And all these above operations will make no change to partions, in a word, everything's absolutely fine.

I just read the posts on first page of this thread, and there seems 2 mistakes according to my experience: 1. Hardy doesn't need to be installed on a primary partition. I guarantee you. 2. If you only use the Vista DVD to divide partitions on the whole hard disk and installed Vista(Ubuntu doesn't affect), no MD, you'll lose all your data and partitions and can't boot to OS if you press MD button while the laptop is off, coz the MD will modify your partition table. I've tried this. The reason is that MD button connects to something in the firmware, so if there's no MD partition to "match" it, then the partition will be destryed. But if you use Hardy to devide hard disk space, and install ONLY ubuntu to the whole disk, then do the same operation, I think nothing harmful would happen and it will boot to your Hardy, though I havn't tried this way.

Can you please explain how you have managed to install Hardy and Vista dual boot on the XPS M1530, while ensuring that MediaDirect still works? I thought that was impossible. :)

I am planning to buy an XPS M1530 in 2-3 weeks, and would love to have a Hardy 64-bit + Vista + MD system.

Also, one (unrelated) doubt: Does the mini-remote that comes with the M1530 work under Ubuntu? With any multimedia softwares like VLC, for example?

---

### Post by VayHow on 2008-05-25
> **Aurorion said:**
> Can you please explain how you have managed to install Hardy and Vista dual boot on the XPS M1530, while ensuring that MediaDirect still works? I thought that was impossible. :)

I am planning to buy an XPS M1530 in 2-3 weeks, and would love to have a Hardy 64-bit + Vista + MD system.

Also, one (unrelated) doubt: Does the mini-remote that comes with the M1530 work under Ubuntu? With any multimedia softwares like VLC, for example?

Glad to help. You just follow the easy steps below:

1. Boot your system using your MD disk, and make partitions.
2. Insert your Vista disk, install Vista onto C drive you created in last step.
3. Reboot system and login to Vista(from HD now), install drivers.
4. After all drivers are ready, insert your MD disk again and it will automatically start installation.
5. After that, reboot your system, and logon to Vista again. You can check if drivers OK now, or just listen to some music. The point is that you start Vista(not MD) after MD's 1st installtion complete.(If you don't do this, or you press MD button for a cool boot, MD maybe fail and cause other unexpected problems. I've tried that.)
6. OK. Now you can open your computer management console. You'll see a big extended partition. Now you can create logic partitions as you like in that. All these logic partitions will be ready in Vista after format. Leave the unused space as they are. You'll install Ubuntu there.
7. Boot your laptop using Ubuntu disk, and install Ubuntu on the "Free Space", which is seen as unused spaces in last step. And LiveCD will automatically install Grub for you.

Now you have a same dual boot system as I do. Any more questions, pleased to help.

The mini-remote is working fine in Ubuntu, as well as those touch buttons on the right of power button(except for eject botton, I'm figuring it out.). Play, stop, next, previous, main functions are all right. I'm satisfied with that. I can use the remote control to switch songs on bed as I wish:lolflag: No more software needed.

PS: The MD I'm using is MD v3.3. What you'll get on your new 1530 will be MD v3.5 or higher. I haven't tried that so I'm not sure if those steps works. But you can have a try, I think this is still the right way.

---

