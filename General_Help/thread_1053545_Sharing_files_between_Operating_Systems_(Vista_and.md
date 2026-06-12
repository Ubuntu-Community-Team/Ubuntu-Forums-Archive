---
title: "Sharing files between Operating Systems (Vista and Ununtu)"
date: 2009-01-28
forum: General Help
---

### Post by GoldenfrankO on 2009-01-28
Alright, I've got a Dell Vostro 1000 laptop. I'm currently using Windows Vista. I, Unlike a lot of other people, like vista. I have a ubuntu 8.10 CD that came in the mail today. I installed it and was very disappointing in the fact that it doesn't share files. Okay so my question is...

Is there a way to share files with a different OS?

Example would be... Say I'm on vista and I save a file called "Speech Essay" and I want to access it from the Ununtu OS. Is there a way to do this easily with all of my files. I'd like it where It's not just copying the files, it's actually sharing, where you can view and edit anything from one OS, and view it from the other exactly as it was on the other OS. Thank you...

---

### Post by tigshadorakie on 2009-01-28
I don't know but you can always use a usb mem stick. That is all the help I can give since I am a total noob with this as well. I have 2 hard drives and I am able to get to the XP drive from Ubuntu but not the other way around. Another install I did I cant see the partition at all.

---

### Post by Gizenshya on 2009-01-28
yes.  there are several ways to do it.

one quick way is to right-click on the top panel and then click "add to panel."  Then find "Disk Mounter."  just add it, then click on the hard drive button and click open, or mount (then open).  and there ya go.

if Disk Mounter isn't there, add it through the synaptic installer, then do the above.

This is just an easy simple GUI for mounting.  you can also edit your fstab, or run a command in the terminal (that will probably all be posted later).

---

### Post by mb_webguy on 2009-01-28
Most people who dual-boot keep their data on a separate partition that is accessible by both operating systems.  For example, I'm dual-booting Vista and Ubuntu.  I have Vista on a 25GB partition that just contains Vista and its applications.  I have Ubuntu on a 12GB partition that just contains Ubuntu and its applications.  I have a separate 2GB /home partition to keep my user settings separate from Ubuntu in case I want to reinstall, but to also hide them from Vista so I don't accidentally break something in Ubuntu while using Vista.  I have a 2GB swap partition for Ubuntu.  And then the rest of the drive is used for my files, and is mounted in both Vista and Ubuntu.

My Documents, Pictures, Video, and other data folders are located on this partition.  In Vista, I went to the Properties dialog to change the location of each of these folders to the corresponding folder on the shared partition.  In Ubuntu, I'm using soft links to point to the same folder.  That way, if I put a photo in my Pictures folder in Vista, it's also there when I boot into Ubuntu.

You *can* just mount your Vista partition in Ubuntu and your Ubuntu partition in Vista (using the [ext2ifs driver]("http://www.fs-driver.org/")), but this is very risky, as it exposes each operating system to the other, and makes it very easy to break one OS from the other.

But otherwise, you'll have to use external storage to exchange files between OSes.

---

### Post by Yashiro on 2009-01-28
It should appear in your places menu in ubuntu.

If not, in Ubuntu. Enter.
> sudo mkdir -p /media/Windows
> sudo mount -t ntfs-3g /dev/sda1 /media/Windows

/dev/sda1 being the Linux reference to your Windows partition.
Which you can dfind out with > sudo fdisk -l

---

### Post by tigshadorakie on 2009-01-28
Why when I go to mount my other hard drive which contains XP it says it Can Not Mount but then when I click on the drive again, it allows me access?

---

### Post by tigshadorakie on 2009-01-28
Actually I just noticed the error information. It complains about XP not being shut down correctly. does that stop you from accessing Windows and causes this problem?

---

### Post by Gizenshya on 2009-01-28
Yes, it does.  It annoys me to no end... I have to reboot into windows (or plug it into another windows computer to automount and 'safely remove' if its an external drive), and then shutdown 'properly' in order for ubuntu to access it again.  Or,you can add "-o force" to the command, like below

```
mount -t ntfs-3g /dev/sda1 /media/Windows -o force
```

"Do this at your own risk."  apparently it can be dangerous.  I don't know why, but perhaps someone with a bit more knowledge about the subject can explain the hazards?

I did that manually for a while, until I found out about Disk Mounter, which apparently ignores the ntfs logfile (which is whats blocking the drive atm).

An alternative is to shutdown Windows cleanly whenever possible.  Something I sometimes care to ignore (which I don't recommend)...

---

### Post by mb_webguy on 2009-01-28
This is an issue with journaling on the ntfs file system.  If Windows is not shut down properly, it doesn't close out the journal.  If you then try to access the partition with Ubuntu (or any OS other than the version of Windows that didn't properly shut down), the system recognizes that the journal was not closed, and prevents access so as to not risk corrupting the partition.  The solution is to reboot into Windows and then shut down or reboot properly.

---

### Post by tigshadorakie on 2009-01-28
That makes sense. I knew there had to be some way that Ubuntu knew that XP didn't shut down right. I am actually very experienced with hardware and Windows OS and never heard of Journaling. I'll look more into it. Thanks everyone for the info. 

P.S Disk mounter still complains about XP.

---

### Post by 00Davo on 2009-01-29
Another way to fix the "unclean shutdown" error (apart from rebooting into Windows) is to use the ntfsfix command:
```
ntfsfix /dev/drive
```
Among other fixes, it clears the journal, allowing a proper mount.

To access your ext3 in Vista, I recommend the ext2ifs driver, although exposing your root directory to a Windows OS may not be a brilliant idea.

---

### Post by tigshadorakie on 2009-01-29
I agree. One of the main reasons I am giving Linux a go is so I really don't have to worry about viruses or security. Allowing someone access to linux files through windows defeats the purpose.

---

### Post by -kg- on 2009-01-29
Really, the best way I can come up with to share files between Windows and Ubuntu is to create a separate ntfs partition and store files there.  That way, you don't have to expose Ubuntu to Windows by installing a driver in Windows to access ext2/3 partitions, and Ubuntu will access an ntfs fine, once it's set up properly.

I can access any of my ntfs partitions from Ubuntu on this laptop by clicking on them and mounting them...read and write.

---

### Post by GoldenfrankO on 2009-01-29
> **Gizenshya said:**
> yes.  there are several ways to do it.

one quick way is to right-click on the top panel and then click "add to panel."  Then find "Disk Mounter."  just add it, then click on the hard drive button and click open, or mount (then open).  and there ya go.

if Disk Mounter isn't there, add it through the synaptic installer, then do the above.

This is just an easy simple GUI for mounting.  you can also edit your fstab, or run a command in the terminal (that will probably all be posted later).

Is this risky?

---

### Post by jeremyj on 2009-01-30
> **mb_webguy said:**
> Most people who dual-boot keep their data on a separate partition that is accessible by both operating systems.  For example, I'm dual-booting Vista and Ubuntu.  I have Vista on a 25GB partition that just contains Vista and its applications.  I have Ubuntu on a 12GB partition that just contains Ubuntu and its applications.  I have a separate 2GB /home partition to keep my user settings separate from Ubuntu in case I want to reinstall, but to also hide them from Vista so I don't accidentally break something in Ubuntu while using Vista.  I have a 2GB swap partition for Ubuntu.  And then the rest of the drive is used for my files, and is mounted in both Vista and Ubuntu.

My Documents, Pictures, Video, and other data folders are located on this partition.  In Vista, I went to the Properties dialog to change the location of each of these folders to the corresponding folder on the shared partition.  In Ubuntu, I'm using soft links to point to the same folder.  That way, if I put a photo in my Pictures folder in Vista, it's also there when I boot into Ubuntu.

mb_webguy, I'm interested in doing this as well.  As of this moment, I have my Vista partition mounted in Ubuntu so I can access my music, movies, and documents in Linux, but I would like to set up a shared partition so both Vista and Ubuntu can read the same files without having to reach into Vista's partition to access a file from Ubuntu.

How do I judge the amount of space to give both Vista and Ubuntu as partitions, then set both read from the shared partition with my stored documents?  Also, how did you set up a system settings partition for Ubuntu so Vista couldn't access it?  Is this possible for Vista as well?

Hopefully, this will help the original poster as well.

---

### Post by mb_webguy on 2009-01-30
You asked, and I deliver.  This post is going to be dreadfully long, but since I'm copying and pasting a lot from a post I wrote a while back on another forum, it's not as bad for me to write it as it will be for you to read it. ;)

**OS partition sizes:**

Ubuntu can live happily on an 8-12GB partition.  I have Ubuntu installed on a 12GB partition, but I'm only using 4.7GB, even though I have a considerable number of programs installed.

For Windows XP, Microsoft recommends a minimum partition size of 6GB, but considering how large Windows applications can be, doubling this is probably a good idea.  I'd say a good partition size for XP is in the 10-15GB range.

Vista is simply huge.  I have Vista installed on a 25GB partition with little more than Office and Visual Studio, and I'm using 18GB.  I certainly wouldn't go much smaller than 25GB with Vista if you're planning on installing much software at all.


**Other considerations:**

Some people don't see much point, but I personally like having a small separate /home partition.  It doesn't need to be very big, since it's primarily just to store your user configuration files, which (being plain text files) are tiny.  Mine is 2GB, of which I'm using about 1.25GB -- primarily because I have Wine installed, and I don't clean out the Wine/Windows temp folder often enough.  The point of having a separate /home partition is so that if you feel the need to reinstall Ubuntu (such as to do a clean installation of a new release), you won't lose any of your settings.  And you don't want to just use the shared partition as your /home directory, because that would expose your Ubuntu user configuration files to Windows.

Another thing you should think about before you partition is swap.  If there's a possibility that you'll ever want to put your computer into hibernation mode, you need at least as much swap as you have memory.  Technically, a swap *partition* isn't required.  You can use a swap *file* instead, but it will use up space on whatever partition you put it on.  Since it's going to take up essentially the same amount of drive space wherever you put it, I think the simplest solution is to create a swap partition during installation.

And then you need to think about primary versus logical (or extended) partitions, and partition order.  You can have a maximum of 4 primary partitions, but you can have any number of logical/extended partitions (which is where a primary partition is subdivided into smaller sections that are treated as separate partitions).  Windows can be finicky about where it is installed, and really needs to be on a primary partition at the beginning of the drive.  If you're going to install multiple versions of Windows, each needs to be on a primary partition.  Linux isn't as picky, though I'd still put the root directory on a primary partition.  Everything else can be on a logical partition.

At this point, partitioning becomes more of an art than a science, and depends a lot on personal preference.  For example, if you have multiple drives, you may get a small performance boost from putting your OSes on one and your data (and possibly swap as well) on another.  If you have only a single disk, you can get some minor differences in performance depending on partition order -- generally, you want areas that are read most often located close together.  Also, you need to decide whether you want to format your shared partition as ntfs or ext3.  I would personally format the shared partition as ext3 and install the ext2ifs driver for Windows, since ntfs can't handle Linux-style file permissions -- the entire partition would have to be mounted with the same user, group, and set of permissions, which other than making any kind of separation of data impossible if you want to set up more than one account, it can cause problems with some Linux applications.  File permissions are less important in the Windows world, and as long as Windows can read and write to the partition, everything's fine.

**A couple of sample partitioning schemes:**

The simplest way to format a dual-boot system is simply to have three partitions: a primary partition for Windows at the beginning of the drive, a primary partition for Linux at the end of the drive, and a primary partition in the middle for your shared data.  (As I'll mention in the next example, you probably want to place them in this order so you'll have roughly equal performance as far as drive access in each OS.)  All you have to do is figure out how much room you think you'll need for each OS and it's applications.  The numbers I suggested at the beginning of the post are a good place to start, but these partition sizes should be also based on how you're going to use your system.  If you're dual-booting so you can use Windows for gaming, you probably need to increase the size of the Windows partition by 5 or 10GB so you have plenty of room to install games.  

As a slightly more complex example, I'll use my own system.  I have two internal hard drives of 160GB each.
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26214396    7  HPFS/NTFS
/dev/sda2            3264        4831    12582912   83  Linux
/dev/sda3            4831        5124     2359296   82  Linux swap / Solaris
/dev/sda4            5125       19457   115129822+   f  W95 Ext'd (LBA)
/dev/sda5            5125        5353     1835008   83  Linux
/dev/sda6            5354       19457   113290348+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3901c8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  Linux

```
sda1 is a 25GB partition, formatted as ntfs for Vista.

sda2 is 12GB partition, formatted as ext3 for the Linux root directory.  Since I'm only using a bit over half of this, I could have made is slightly smaller.  But Ubuntu is my primary OS, and I wanted to make sure I had room to grow.

sda3 is a 2GB swap partition.  Notice that I put it right after the root partition.  If I were to repartition this drive right now, I'd most likely put it at the end of the drive, but  I'll get back to this point a bit later...

sda4, if you'll notice from the Start and End numbers, is actually the combination of sda5 and sda6.  This is because these last two are logical partitions -- subsections of the 4th primary partition.

sda5 is my 2GB Linux /home partition.

sda6 is a (relatively) small data partition, formatted as ext3.  It's just a bit less than 100GB.  This is shared between Linux and Windows.  In Vista, it's mounted as something like drive E.  In Ubuntu, I have it mounted as /mnt/Little.

sdb1 is my main shared partition.  I have it mounted as drive D in Vista, and as /mnt/Big in Ubuntu.  (Yes, I know the naming convention isn't very imaginitive, but I access these drives through symlinks, so I don't actually see the names much.)  My Documents, Pictures, Videos, Downloads, and other user folders are located on this drive.  In Linux, I have symlinks in my user home directory pointing to these locations.  In Vista, I moved the location of these user folders from the usual location on the C drive to this drive.  So if I click on Documents in either OS, I'm going to the same place.

Ok, so I mentioned earlier that I'd move the swap partition if I repartitioned my drive right now.  Here's why.  I knew that I was going to use sdb1 as my primary shared partition.  In the back of my head, I was thinking of sda6 as more long-term storage.  Since sda6 is still fairly large, and I wasn't planning on doing much I/O to this partition, I decided that it would be better to put swap and the /home partition close to the root partition, to shorten the distance the drive head would have to move to read or write to those three partitions.  However, since I first installed, I lowered the swappiness setting to increase performance (so swap is barely used unless I go into hibernation), and I've put my mySQL databases on sda6.  So given my change in user behavior, I'm not getting optimal performance from this drive.  I would get a small -- to be honest, likely unnoticeable -- boost in performance if the swap partition were at the end of the drive, so the drive head wouldn't have to move so far to get from the root partition to the smaller shared partition.  

I only mention that to demonstrate that partitioning is all about planning.  You need to consider how you're going to use your computer in order to plan the best way to partition your drive.


**A few final tips:**

BACK UP EVERYTHING BEFORE YOU EVEN THINK ABOUT STARTING TO PARTITION YOUR DRIVE!!!  Partitioning your drive will erase everything on it, so if there's anything you want to keep, you need to back it up now!

Always install Windows first.  The Windows bootloader doesn't recognize non-Windows operating systems, so if you install Linux first, you'll have to reinstall your bootloader in order to regain access to Linux.  If you install Windows first, the Windows bootloader gets replaced by GRUB when you install Ubuntu, so there's no extra work involved.

Different partitioners may use different definitions of a GB.  Some use GigaBytes (where 1GB = 1000^3 Bytes), some use Gi*bi*Bytes (where 1GB = 1024^3 Bytes), and others use an odd hybrid of the two (where 1GB = 1000^2 KB = 1000^2 * 1024 Bytes).  So you may have to do some math to convert from the size you want a partition to what the partitioner needs to make it that size.


That's about all I have.  I hope it helps somewhat.  Good luck!

---

### Post by jeremyj on 2009-02-06
> **mb_webguy said:**
> You asked, and I deliver.

Sorry for my late reply; I've been tied up the past several days, but thank you so much for the detailed steps!  I appreciate it!

---

