---
title: "What's the safest way to put Ubuntu on a 2nd hdd?"
date: 2009-01-16
forum: General Help
---

### Post by notesetter on 2009-01-16
I have XP SP3 installed on my primary (master) hdd. I also have a secondary (slave) hdd which is empty or had data I don't care about. It's around 40 gb and I'd like to put Ubuntu 8.10 on it.

The computer is old and I've had trouble setting up dual-boot on one hdd in the past. I'd really like to set this up without running into problems with the XP hdd or messing up the MBR in any way.

Feel free to post links if this has been addressed somewhere on the forum. I've searched and seen some methods in the archive, but my search probably wasn't exhaustive.

Thanks,

D

---

### Post by redilyn on 2009-01-16
You should be able to boot from the livecd and choose install

When you reach the partitioning section choose manual.

Create 3 partitions on the second hdd as follows.

10GB ext3 mount point /
1GB swap
39GB ext3 mount point /home

Then continue with the install. If you have problems let us know.

When the install is finished the next time you boot you should get a grub menu with options for ubuntu, memtest, and windows xp. If for whatever reason windows xp is not listed I can give you steps to add it to the bootloader.

This should be safe as long as you do not make any changes to the first hdd

---

### Post by JSorrell on 2009-01-16
> **notesetter said:**
> I have XP SP3 installed on my primary (master) hdd. I also have a secondary (slave) hdd which is empty or had data I don't care about. It's around 40 gb and I'd like to put Ubuntu 8.10 on it.

The computer is old and I've had trouble setting up dual-boot on one hdd in the past. I'd really like to set this up without running into problems with the XP hdd or messing up the MBR in any way.

Feel free to post links if this has been addressed somewhere on the forum. I've searched and seen some methods in the archive, but my search probably wasn't exhaustive.

Thanks,

D

I did something similar on my desktop. An easy method is:

Remove the HD you have XP installed on. Switch the second one you want Ubuntu on to the main driver. Boot up and install Ubuntu. Then shutdown, replace the XP HD as either the secondary drive or replace it as the main drive. 

If you left the Ubuntu drive as the primary drive, add an XP entry to /boot/grub/menu.lst but if you put the XP drive back as the main HD, install grub on it. It won't effect your ability to boot XP as it installs to the MBR.

Or, you can do it all through the Ubuntu install disc without removing anything. Just select the second drive as the Ubuntu install path. 

Either way works just fine, but it made me a little nervous to use the second method when I set my desktop up when I was new to Ubuntu.

---

### Post by bodhi.zazen on 2009-01-16
I disagree.

The easiest way is to install Ubuntu and use the default settings, including installing grub to the MBR of the first HD.

This is non-destructive to Windows and is easily undone if needed.

You MUST understand partitions and how both grub and Linux refer to partitions.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by notesetter on 2009-01-18
The reason I'm skittish about modifying the master hdd is that I originally intended to set up a dual-boot system on this drive with XP and Ubuntu. The drive is about 250 gb. Turns out that the computer is old enough (ca. 2002) that the BIOS won't address the full capacity of the drive (I don't fully understand this). Anyway, when I went through the steps of partitioning the drive to install Ubuntu, the MBR was changed (I guess to include GRUB) and I lost the ability to boot into XP (or Ubuntu). After attempting to fix the MBR for about 1.5 days, I finally just scrapped the whole thing and started over with XP (My laptop, which is only about a year newer was able to set up as a dual-boot XP/Ubuntu with no problems, which encouraged me to try it with the Desktop in the first place).

I've thought about setting up a /boot partition on the drive to solve the problem and set up the dual boot, as I would really like the 2nd hard drive to be a data drive or a place to try out other distros. Is this possible with older motherboards that weren't initially supposed to be able to address such large capacity hdd's?

---

### Post by mssever on 2009-01-18
> **notesetter said:**
> I've thought about setting up a /boot partition on the drive to solve the problem and set up the dual boot, as I would really like the 2nd hard drive to be a data drive or a place to try out other distros. Is this possible with older motherboards that weren't initially supposed to be able to address such large capacity hdd's?
That's really the only use for a separate /boot partition, which should ideally be sda1.

---

### Post by bodhi.zazen on 2009-01-18
> **mssever said:**
> That's really the only use for a separate /boot partition, which should ideally be sda1.

:lolflag:

A separate /boot is needed (with grub) to boot an XFS (root) file system as well as encryption. LVM, and RAID.

a /grub partition can be made and mounted (in fstab) to /boot/grub to multiboot.

---

### Post by mssever on 2009-01-18
> **bodhi.zazen said:**
> :lolflag:

A separate /boot is needed (with grub) to boot an XFS (root) file system as well as encryption. LVM, and RAID.

a /grub partition can be made and mounted (in fstab) to /boot/grub to multiboot.
I stand corrected. I've never used any of the things you've mentioned.

---

### Post by notesetter on 2009-01-18
Since we're on the subject, does anyone know of a reliable, competent online howto addressing how to create a /boot partition on a system like mine (with an old BIOS)? I already have XP installed and running and I'd like to preserve that installation. That said, I'll probably have to nudge that partition to make room for a /boot partition. Is GParted up to this job?

---

### Post by bodhi.zazen on 2009-01-18
> **notesetter said:**
> Since we're on the subject, does anyone know of a reliable, competent online howto addressing how to create a /boot partition on a system like mine (with an old BIOS)? I already have XP installed and running and I'd like to preserve that installation. That said, I'll probably have to nudge that partition to make room for a /boot partition. Is GParted up to this job?

You have two options :

1. Update your BIOS.

2. Make a boot partition. When you install , use manual partitioning.

Make a 512 or 1 Gb partition, format it to ext2, and mount it to /boot

All of these are options under manual partitioning on both the desktop install and alternate install.

---

### Post by notesetter on 2009-01-18
I've already updated the BIOS to the most recent available and it doesn't have support for the larger disks. If I decide to put XP and Ubuntu on the same disk, I'll have to do it with a /boot partition. I'll spend some time reading and searching the forum.

Thanks for the insights.

Dave

---

### Post by bodhi.zazen on 2009-01-18
It is very easy, there is not much to "read"

As i said, make a boot partition. The only "trick" is that it must be your first partition on the hard drive.

So ...

partition 1 (primary partition) = first 500 Mb = /boot
partition 2 (primary partition) = second partition, for Windows
Partition 3 (primary partition) = ntfs partition = shared data partition

Partition 4 = Extended partition
Partition 5 = logical partition = swap
Partition 6 = logical partition = / (root for ubuntu)

---

### Post by notesetter on 2009-01-18
I don't want to overwrite my current XP partition. Using GParted, should I resize and move the XP partition in order to make the /boot partition at the front of the disk? Won't this render XP (at least temporarily) unbootable?

---

### Post by bodhi.zazen on 2009-01-18
> **notesetter said:**
> I don't want to overwrite my current XP partition. Using GParted, should I resize and move the XP partition in order to make the /boot partition at the front of the disk? Won't this render XP (at least temporarily) unbootable?

Yes, you will need to resize.

Yes you may have problems booting windows as you are configuring your hard drive.

Ubuntu *should* take care of the rest automatically when you install it.

If not, it should be very simple to fix, but you may wish to start a new thread if you run into issues.

---

### Post by notesetter on 2009-01-18
Many thanks. I will most likely try again with a dual-boot and post new questions as they arise (if needed).

---

### Post by theWrkncacnter on 2009-01-18
> **bodhi.zazen said:**
> 
As i said, make a boot partition. The only "trick" is that it must be your first partition on the hard drive.

Just to be curious and not wanting to start a new thread, why is the boot partition ideally put first? Mine is /dev/sda7 -- will I run into problems?

---

### Post by notesetter on 2009-01-18
The problem is with my older machine's BIOS, which can't read anything past the first 8.5 GB of the disk. Once the OS is booted, I have access to the whole disk.

---

### Post by theWrkncacnter on 2009-01-18
Ah, that makes sense :)
Thanks

---

### Post by BuZZeM on 2009-06-15
A slight Hijack, so if its inappropriate please let me know. Fairly new user here.

The reason i'm putting my question here because it's halfway the same.
Any feedback is greatly appreciated.

Before:
a laptop with 1 HD and 4 partitions.
- 1 factory standard recovery - fat 32
- 3 partitions for user windows XP - NTFS
- boot encryption was applied with truecrypt 6.1(a) - worked like a charm (data partitions to be mounted separately after booting into windows)

after:
installed ubuntu 9.04 on a separate harddrive
made a boot partition and a swap partition
as well as leaving a data partition

ubuntu installs and boots fine, but when I try to access my windows it boots into the recovery partition, with only an option to restore factory standard (which I obviously dont want)

What it should show is the truecrypt boot screen where is should type my password to boot into windows.

I had a look wiht the partition editor - it shows the 4 partitions intact on the primary hd. hd0 0 is the fat32 recovery partition. the other 3 are recognized but not as NTFS.

I tried adding lines to the grub to boot to hd0 1 which I suspect is the system drive. It doenst.

Disconnecting the usb hard drive (with the ubuntu install) generates a 21 error (which makes sense, since during install I made the choice to put the boot menu on the usb hd), ending possibilities there.

thoughts so far:
Probably Grub interfered with the tryecrypt bootloader in MBR?

so the question (finally ;) )
Is there any way to get back into my truecrypted windows (get to the truecrypt system encryption boot screen)?
What do I do to do so?


(in over my head for a start-up linux user :/)

BuZZeM

---

### Post by mixmaster on 2009-06-15
> **BuZZeM said:**
> ubuntu installs and boots fine, but when I try to access my windows it boots into the recovery partition, with only an option to restore factory standard (which I obviously dont want)

BuZZeM
I had this happen to me once.  
Basically, the grub script which generates the boot options has got its hard disk partition identifiers wrong.  The file is /boot/grub/menu.lst and is a plain text file which you can edit.  From memory the change was fairly obvious (just keep a backup of the original file if case you get it wrong).  If you are nervous about making the change post the contents of menu.lst here and I'm sure someone will be able to tell you exactly what to change.

---

### Post by BuZZeM on 2009-06-17
I am a bit apprehensive :)

Right now at least I have a working ubuntu...dont want to lock myself out completely :)

posting the relevant part here (as far as I can determine....if you're missing something just shout)

The first one is the regular ubuntu start up one.
The last one is the one that should boot windows (and therefore the truecrypt bootloader first)

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7e4da919-59d1-425f-8541-0d45ce01c6f4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7e4da919-59d1-425f-8541-0d45ce01c6f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7e4da919-59d1-425f-8541-0d45ce01c6f4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7e4da919-59d1-425f-8541-0d45ce01c6f4 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7e4da919-59d1-425f-8541-0d45ce01c6f4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


So basically what i'm looking for is how to change this last entry so it "boots" the truecrypt bootloader instead of the recovery partition.

edit: like stated ^^. I already tried adapting this one to hd0,1 which I believe should be the windows system disk but that didnt work (probably because the truecrypt bootloader is in MBR instead?)
cheers

---

### Post by bodhi.zazen on 2009-06-17
we can not help you if we do not know your partitions.

What is your windows partition ? your grub menu.lst looks fine if windows in on (in grub speak) (hd0,0).

If you do not know how to identify partitions see :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by BuZZeM on 2009-06-20
Been away for a bit. Mmm...I though I made that clear in my earlier posts.
I'm not sure what you are looking for then.
I will post more info later tonight or tomorrow in the direction I think you might be looking.
thx for the replies so far.

ubuntu is on sdb2
dedicated swap on sbd5
data partition (from before ubuntu) on sbd1
and there is an sbd3 (not sure what its used for)
Don't know what happened to sdb4 - never existed as far as I know.

Windows partitions (from before ubuntu - can now be seen but not approached)
sda1 factory restore partition fat32 (which would be HD0,0 - not the one im looking to boot)
sda2 most likely the system drive under XP - fs not recognized under linux (which isnt strange since it was truecrypted?) - but it IS ntfs - all partitions were (before ubuntu isntall)
sda3 most likely data partition  - NTFS - not recognised - see above
sda4 most likely 2nd data partition - NTFS - not recognised - see above

I did reconstruct with certainty what went wrong with the jaunty install.
I chose to do partitions manually - since i wanted to be sure what ended up where.
made a nice new ext 2 partition for the fs (sbd2)
made a dedicated swap (sbd5)
clicked on through the install screens.

what I missed was the ADVANCED tab on the 7th page 
where I would have been informed that grub would be written to HD0 (sbda) and where i *would/could* have changed it to sbdb
as I intended. So grub overwrote my truecrypt bootloader in MBR of sdba (I think)

- not very newby friendly; everything to keyboard layout ind something as insignificant as timezone is covered into tiny detail and then a possibly system cripling choice is hidden behind an advance tab - bad form imho.

anyway...hope this provides the info you need

---

### Post by BuZZeM on 2009-06-29
Too bad...no more answers.

Dug up an oldish backup, extracted the mbr from there and pushed it back on the laptop. 

That got me the truecrypt bootloader back.

Still booted into the recovery, partition was unfixable while encrypted, so I decrypted the whole disk.

Reset the windows bootloader after decryption.

Got everything back. Ubuntu died in the processm which is ok since my ati x1600 wouldn't properly function due to x-server incompatability under Jaunty.

Will be going back to 8.10...eventually.

---

### Post by Nick Brohman on 2009-09-07
> **bodhi.zazen said:**
> I disagree.

The easiest way is to install Ubuntu and use the default settings, including installing grub to the MBR of the first HD.

This is non-destructive to Windows and is easily undone if needed.

You MUST understand partitions and how both grub and Linux refer to partitions.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

[COLOR=Red]Have worked out ? for all this  post-- want HDD1 (/dev/sda1)
 & HDD2 to be  same path

Can this be done?

How is it done?
[/COLOR] 
I have same/different problem. A search led me here & I've found replies that could help, if I understood the process.

Have just added 2nd HDD & want to use it just as an extesion of 1st HDD.

Not sure how to phrase ? Ideally 2nd HDD to be set up so that instead of 160Gb HDD, I have 1,160Gb HDD. In my vernacular, adding a 'walk-in pantry' (storage - 2nd HDD)) to my 'kitchen' (working area - 1st HDD).



There is no category of search available to someone in my situation,i.e., someone needing "The Compleat Idiots Guide On How To Start Your Computer Age & Stay Alive".

Trying to cram 30yrs computing know how in to a few days is a task of stupendous proportions for me at the moment but even the smallest dog can piss on the tallest tree.

In my searches, all answers are on the presumption of prior knowledge of PC/OS.

I don't have that experience & only got interested in owning a PC after reading about Linus In the late 90s. Had this PC since Dec. last & it has only ever had a Linux OS as its platform. I don't want this PC to be corrupted by MS. Both computers that I own were bought as bare boxes! (See Failure To Launch New Thread for some of my views of MS)

Have had Net since Sept. 08 & email address for 8 wks. & only 1 wks. experience of using this Forum.

I am very green!

I get lost with any code answers as have had trouble with sudo commands, etc..

Have tried to partition but can't, yet (tried to dual boot XP with my 1st install of 7.10, thought I did as asked but kept getting errors so just got rid of XP). 

Have found that I can follow most photo replies (with good language ), they are very helpful to me. 

Back up is a worry and is one of the reasons I've never been bothered to learn anything to do with MS. A MeSser told me that everything had to be stored on CD/DVD & doing that just created problems with permissions etc., for me. My searches so far now tell me that I don't have to do that.

Have had problems with data disks, should have that fixed as writer has just been replaced but am still wary of doing compression asI seem to be able to increase file sizes but not compress!

Extra HDD is for music/photo/videotext files only. Don't game unless it's puzzle to solve. 

Want to load DVD so that can watch concerts with ease.

Approx. 110Gb music & 30Gb Photos & nothing else of importance at the moment, on 1st HDD.

Now I've just gone to a reply from bodhi.zazen referring to partitioning basics & that's part of my problem. Any reference to what MS means absolutely Zilch to me & I have to stop reading.

I know it's taken a while to get here but this has taken me longer. 

Thanks to all who reply and when this is fixed, be you in Minnesota or Timbuktu, you will hear my appreciation

Nicko:sad:

One can remember to forget
One shouldn't forget to remember

---

