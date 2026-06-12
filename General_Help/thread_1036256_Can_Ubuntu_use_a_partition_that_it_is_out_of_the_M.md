---
title: "Can Ubuntu use a partition that it is out of the MBR for /home?"
date: 2009-01-10
forum: General Help
---

### Post by Jammanuser on 2009-01-10
Hi, I want to move my /home directory in Ubuntu 8.10 to a different partition, using the feature in System>Administration>User and Groups>Unlock>*Type password*>Select /home/*username*>Properties>Advanced>Home directory, but I have just **one** problem! :) Unfortunately, the partition that i want to move my /home folder over to is not in the MBR partition table, and can not be placed in it, without replacing something else, because the 4 primary partition limit is filled up! :P So i was wondering if this feature can even use a partition that is out of the MBR for the /home folder...?

If this is not possible, then my next question would be can the swap partition for Ubuntu 8.10 be taken out of the MBR's partition table, and the new partition for the /home folder inserted in its place, without losing the ability to use my swap? Can my Ubuntu installation use a swap partition that is not in the MBR?

Looking forward to a reply.

-Jam man

:guitar:

---

### Post by KeyserSoze93 on 2009-01-10
Maybe I'm missing something, but my laptop home folder does just fine on an extended/logical partition. You could save yourself a lot of bother doing it that way (incidentally, my swap is on a logical partition too).

---

### Post by caljohnsmith on 2009-01-10
Hi Jammanuser, so are you saying you don't have an extended partition right now? If so, you could convert one of your primary partitions into an extended partition, and within that extended partition you can make basically as many logical partitions as you want. How about first posting:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

---

### Post by meierfra. on 2009-01-10
Just as an explanation for everybody who has been trying to help:

From  a previous thread I know that Jammanuser is using BootIt. BootIt is a bootmanager which maintains its own partition table, independent from the partition table in the MBR.  BootIt lets you choose which  partitions to display in the MBR.  (so all others will be hidden and effectively unusable)

So the output of sdisk will be very misleading and  probably will not show the future home partition.

I think that BootIt lets  you have an extended partition in the regular partition table in the MBR, but I not sure. I'll do some research.

---

### Post by dcstar on 2009-01-10
> **Jammanuser said:**
> 
..........
If this is not possible, then my next question would be can the swap partition for Ubuntu 8.10 be taken out of the MBR's partition table, and the new partition for the /home folder inserted in its place, without losing the ability to use my swap? Can my Ubuntu installation use a swap partition that is not in the MBR?


Swap partitions can go anywhere. If you have used up the 4 primary partitions then the solution may be this simple:

Remove the current Primary Swap partition, create a new Extended partition and put a new Swap Partition in it, and if you make the new partition big enough you can then put many other Partitions in it.

Please not that changing any partition means changing the /etc/fstab file to reflect the new UUIDs.

---

### Post by meierfra. on 2009-01-10
I'm sure you already know, but just as a reminder:


A quote from the BootIt Manual:

> It is extremely important that you do not use any partitioning software (such as FDISK) if you are not
limiting the number of primary partitions (Limit Primaries Option). If you ignore this warning, you are taking
a serious risk of data corruption.

any partitioning software includes gparted.

---

### Post by Jammanuser on 2009-01-10
> **KeyserSoze93 said:**
> Maybe I'm missing something, but my laptop home folder does just fine on an extended/logical partition. You could save yourself a lot of bother doing it that way (incidentally, my swap is on a logical partition too).

Yes, I am aware that i could use an extended partition...but i was trying to find out if it was possible to put my /home on a partition that it is out of the MBR. That was my question, but it appears from the replies that I got that that is not possible...:(

Anyway, thank all of you for your replies, but i don't have the time right now to answer them all...i will be gone for a couple of hours, after which i will come back here, and answer all of y'all! :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-10
Ok, back now. :) Real life happened to get in the way...
> **caljohnsmith said:**
> Hi Jammanuser, so are you saying you don't have an extended partition right now? If so, you could convert one of your primary partitions into an extended partition, and within that extended partition you can make basically as many logical partitions as you want. How about first posting:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

Hello again, Caljohnsmith. :) Actually, to be completely honest, I do have an extended partition at the moment, but it is unfortunately too small for my purposes (I also want to put my XP and Vista's personal files on the same partition as well...). Of course, i know that i could simply resize it with BING (the partitioning tool that i use, which also has its own bootloader), but it seemed like to me it might be easier if i could...never mind! :) This dialogue is becoming too long, and i want to get to my point in a hurry! :guitar:

Anyhow, here is the info you requested.

sudo fdisk -lu:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c5a8d58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       556861095   618293654    30716280    c  W95 FAT32 (LBA)
/dev/sda2       547655850   556861094     4602622+  82  Linux swap / Solaris
/dev/sda3        20560325   506706164   243072920    7  HPFS/NTFS
/dev/sda4   *   506706165   547655849    20474842+  83  Linux

Partition table entries are not in disk order

```
sudo sfdisk -d:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=556861095, size= 61432560, Id= c
/dev/sda2 : start=547655850, size=  9205245, Id=82
/dev/sda3 : start= 20560325, size=486145840, Id= 7
/dev/sda4 : start=506706165, size= 40949685, Id=83, bootable



```

Hope it helps!

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-10
> **meierfra. said:**
> Just as an explanation for everybody who has been trying to help:

From  a previous thread I know that Jammanuser is using BootIt. BootIt is a bootmanager which maintains its own partition table, independent from the partition table in the MBR.  BootIt lets you choose which  partitions to display in the MBR.  (so all others will be hidden and effectively unusable)

So the output of sdisk will be very misleading and  probably will not show the future home partition.

I think that BootIt lets  you have an extended partition in the regular partition table in the MBR, but I not sure. I'll do some research.

Yes, that it is correct...I am using BootIT Next Generation (BING), which is a partitioning tool that also includes its own bootloader, and this is what i boot into at startup. From there, i can next boot into any of the 3 installed OSes that i have as a tri-boot. The partition table that BING uses in addition to the standard MBR is called EMBR (short for "Extended Master Boot Record"), which can hold more than 200 primary partitions, and enable booting from them as well! :guitar: 

Cheers! :popcorn:

-Jam man

---

### Post by Jammanuser on 2009-01-10
> **dcstar said:**
> Swap partitions can go anywhere. If you have used up the 4 primary partitions then the solution may be this simple:

Remove the current Primary Swap partition, create a new Extended partition and put a new Swap Partition in it, and if you make the new partition big enough you can then put many other Partitions in it.

Please not that changing any partition means changing the /etc/fstab file to reflect the new UUIDs.

hmm...i may actually do that if that my other idea doesn't work, or simply isn't practical! :)

Thanks for the advice! :popcorn:

-Jam man

:guitar:

---

### Post by meierfra. on 2009-01-11
> So i was wondering if this feature can even use a partition that is out of the MBR for the /home folder...?

No.  The home partition  needs be listed in the MBR.  

So you have two  options:

1) Follow dstars advice: deleted the swap partition and replace it with an extended partition. But since your swap partition is to small for an  home partition, you will have to repartition the hard drive. Make sure that you use BootIt  for all the partitioning work. If you need some help with the repartitioning,  post a screen shot from your  BootIt NG "Work with Partitions" screen.


2)  For  booting into Ubuntu neither  the XP nor the Fat32 partition need to be listed in the MBR.
So you can just use  BootIt NGs "Boot Edit" to create a new profile which contains Ubuntu, the home partition, swap and one more partition of your choice.

(For the people which don't know BootIt NG:   BootIt  lets you create various profiles. A  profile list the partitions one wants to   appear in the MBR, which partition should be active and some other choices.  At boot up  one  chooses which boot profile to use, and the information from the boot menu will be written to the partition table in the MBR.)

Be aware that both 1) and 2) might require reinstall grub, editing menu.lst  and editing fstab.

---

### Post by Jammanuser on 2009-01-11
> **meierfra. said:**
> I'm sure you already know, but just as a reminder:


A quote from the BootIt Manual:


any partitioning software includes gparted.

Thanks, Meierfra. :) I actually already **did** know about that...that is why I haven't used Gparted or any other partitioning tool after installing BING. I have used only BING for partition work. Personally, i think it is **better** than Gparted, but since I know practically everyone here uses Gparted, i will leave it at that... ;)

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-11
> **meierfra. said:**
> No.  The home partition  needs be listed in the MBR.  

So you have two  options:

1) Follow dstars advice: deleted the swap partition and replace it with an extended partition. But since your swap partition is to small for an  home partition, you will have to repartition the hard drive. [COLOR="Red"]Make sure that you use BootIt  for all the partitioning work.[/COLOR] If you need some help with the repartitioning,  post a screen shot from your  BootIt NG "Work with Partitions" screen.


Right, as i just mentioned above, BING is the only tool that i use for partition work...i have not used any other since reading that paragraph in the BING manual, which you quoted, a while ago. About the home partition...hmm, i figured as much! :( I wish there was a way for Linux to use partitions outside of the MBR for storing the /home directory...it would certainly make it much easier! :) But i guess the above is the only way to do it...i had already guessed this much before even starting this thread, but i was thinking of something more along the lines before of replacing my swap partition in the MBR partition table with my /home partition, hoping that my swap would at least be able to be used outside of the MBR! But it seems that that is not possible either! :( So i will probably go with what dstar suggested, as it seems to be my best option...
> 
2)  [COLOR="Red"]For  booting into Ubuntu neither  the XP nor the Fat32 partition need to be listed in the MBR.[/COLOR]
So you can just use  BootIt NGs "Boot Edit" to create a new boot menu which contains Ubuntu, the home partition, swap and one more partition of your choice.


True. But if XP was out of the MBR, i would not be able to boot into it any longer...at least from the Vista bootloader, which is kind of the way i would like to leave things, if you know what i mean. ;)
> 
(For the people which don't know BootIt NG:   BootIt  lets you create [COLOR="Red"]various[/COLOR] boot menu's. A boot menu list the partitions one wants to   appear in the MBR, which partition should be active and some other choices.  At boot up  one  chooses which boot menu to use, and the information from the boot menu will be written to the partition table in the MBR.)

Be aware that both 1) and 2) might require reinstall grub, editing menu.lst  and editing fstab.

I'm not sure about that...AFAIK, BING only creates **two** boot menus, which to all intents and purposes are pretty much the same. Just one is the Default Boot Menu, and the other one is the Direct Boot Menu. I haven't experimented very much yet with the Direct Boot Menu, and have only used the default boot menu, but i believe it is pretty much the same thing as the other one, only perhaps giving more options at boot.

-Jam man

:guitar:

---

### Post by meierfra. on 2009-01-11
> Personally, i think it is better than Gparted, but since I know practically everyone here uses Gparted,

????????  BootIt NG cannot even resize a ext3 filesystem

---

### Post by Jammanuser on 2009-01-11
> **meierfra. said:**
> ????????  BootIt NG cannot even resize a ext3 filesystem

huh??? :confused: what makes you think that BING can't resize an ext3 partition? admittedly, i have not tried resizing my Ubuntu partition, after creating it, but what makes you think that it wont work?!! :) It certainly creates Linux Native partitions just fine! 

-Jam man

:guitar:

---

### Post by meierfra. on 2009-01-11
> I'm not sure about that...AFAIK, BING only creates two boot menus,

I already edited my last post, before I saw your post. I shouldn't have called it "boot menu", that was too confusing. 

But you can create lots of different profiles in  the default boot menu (I just did it myself).

During boot up:
Choose "maintance" 
Click on "Boot Edit".
Click on "Add"

and  then create a new profile.

---

### Post by meierfra. on 2009-01-11
> what makes you think that BING can't resize an ext3 partition? 

I just tried it myself. If you try to resize an ext3 partition it tells you to use "resizefs" to resize the filesystem.

> it certainly creates Linux Native partitions just fine! 

Sure, but that's an easy task which only takes a few seconds.

---

### Post by Jammanuser on 2009-01-11
> **meierfra. said:**
> I already edited my last post, before I saw your post. I shouldn't have called it "boot menu", that was too confusing. 

But you can create lots of different profiles in  the default boot menu (I just did it myself).

During boot up:
Choose "maintance" 
Click on "Boot Edit".
Click on "Add"

and  then create a new profile.

Indeed. I know about that part...:)

BTW, **you** started using BING?!! i would have thought you would have stuck with Gparted, since you believe BING can't resize ext3 partitions! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-11
> **meierfra. said:**
> I just tried it myself. If you try to resize an ext3 partition it tells you to use "resizefs" to resize the filesystem.


hmm...i guess i'll have to test it myself. its strange that they wouldn't include support for resizing Linux Native partitions (which is what BING actually calls it, btw!)...:)

Perhaps i will contact the developers of the software, and ask them about it. If they don't support it now, maybe they will support it in their next version! 

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by meierfra. on 2009-01-11
> you started using BING?!!

No, I just downloaded BING and tried it out, so that I can give you qualified advice.

---

### Post by Jammanuser on 2009-01-11
> **meierfra. said:**
> 
Sure, but that's an easy task which only takes a few seconds.

Indeed. But why would they not have support for resizing filesystems that it can create? it seems odd to me...

But anyway, as mentioned [COLOR="Red"]above[/COLOR] (EDIT: or on last page! :lol:), i think i'm going to contact them, and ask 1) if BING allows resizing of an ext3 partition, and 2) if they don't, when they will implement this feature in their software, as it is **extremely **essential for Linux users to be able to resize their Linux partitions! :)

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-11
> **meierfra. said:**
> No, I just downloaded BING and tried it out, so that I can give you qualified advice.

Cool...appreciate it! :) But do you like it so far, the short time that you have been using it? somehow i have a feeling you do...:lolflag:

-Jam man

:guitar:

---

### Post by meierfra. on 2009-01-11
> But why would they not have support for resizing filesystems that it can create? 

Resizing a filesystem is a very difficult task which can take hours.

---

### Post by Jammanuser on 2009-01-11
> **meierfra. said:**
> Resizing a filesystem is a very difficult task [COLOR="Red"]which can take hours[/COLOR].

Actually, the process isn't **that** long for BING! :) I have resized partitions before, using BING, and it only took a few minutes! :P It was also not a tiny partition either...i believe it was close to 150 GBs! 

-Jam man

:guitar:

EDIT: Admittedly, i didn't resize it **quite** that much...it was considerably less, but i don't remember the exact size. I'm not sure...i think it was something like 20 GBs of space chopped off, after resizing. Again, i can't recall the exact amount right now...but my point it is, partition resizing is actually a whole lot faster than with some other partitioning tool, Gparted for instance.

---

### Post by meierfra. on 2009-01-11
> But do you like it so far, the short time that you have been using it?

Being able to create all this different profiles, is kind of fun. But  I don;t see any real use for it, and I'm certainly only going to keep it for more than a few days, since they want  $35   to register it.


> have resized partitions before, using BING, and it only took a few minutes!  It was also not a tiny partition either...i believe it was close to 150 GBs! 

Enlarging a partition only takes a few second. 

Shrinking an ext3 partition with  large amount of file, involves moving a large amount of files to the begining of the drive and  cannot to be done in a few minutes

A well-defraged ntfs filesytem will have all its files at the beginning of the drives, so  shrinking it should not take very long,

But if you have your typical  ntfs-filesytem and you don't defrag it for a few hours before resizing, shrinking will  take much longer than a few minutes.

---

### Post by Jammanuser on 2009-01-11
> **meierfra. said:**
> Being able to create all this different profiles, is kind of fun. But  I don;t see any real use for it, and I'm certainly only going to keep it for more than a few days, [COLOR="Red"]since they want  $35   to register it.[/COLOR]


$35 is a small price to pay, considering you can have more than **200** PRIMARY partitions, and boot from them as well from the BING bootloader! :) Not to mention the convenience of not having to insert a LiveCD in, and boot from it, every time you want to do some partition work...with BING, it is all right there, and you can do it before booting into any of your installed OSes, spending a hell of a lot less time! :guitar:

Cheers! :popcorn:

-Jam man

:guitar:

EDIT: And of course, there's all those other additional options as well...

---

### Post by meierfra. on 2009-01-11
What should I do with 200 primary partitions?

I can have  as many logical partitions as  I want, and grub can boot all of them for free.


Most of my partitions are Linux partitions. (In fact the only reason I still have Vista and a couple of ntfs partitions is for helping people in the forums) So BING  won't be of any use to me. 

I'll keep it for a couple of days, until  I deciphered the MPT (just so that I can teach  my  boot_info_script to read the  MPT, and I will never again have to asked people for screen shots from the  "Work with Partitions" screen)

---

### Post by Jammanuser on 2009-01-11
Ok...so one more question. :) Does the filesystem type matter for the /home partition? does it have to be ext3 format, or can it be any format...NTFS for example? 

Looking forward to a reply.

-Jam man

:guitar:

---

### Post by meierfra. on 2009-01-11
> Does the filesystem type matter for the /home partition? 

A /home partition needs to be ext3 (or some other linux type filesystem). There are various  hidden  configuration files in the home folder which need their permissions  set in certain  way, and that is not possible on an NTFS partition.

Personally, I do not have a separate /home partition. Instead,  I use  data partitions for all my documents  and stuff.   And  data partitions can be NTFS.

---

### Post by Jammanuser on 2009-01-11
> **meierfra. said:**
> A /home partition needs to be ext3 (or some other linux type filesystem). There are various  hidden  configuration files in the home folder which need their permissions  set in certain  way, and that is not possible on an NTFS partition.

Personally, I do not have a separate /home partition. [COLOR="Red"]Instead,  I use  data partitions for all my documents  and stuff.[/COLOR]   And  data partitions can be NTFS.

hmm...but can you access your files without having to navigate through several dirs? can you access them from folders in the Places menu?

maybe i will try that instead...

Thanks! :popcorn:

-Jam man

:guitar:

---

### Post by meierfra. on 2009-01-11
> but can you access your files without having to navigate through several dirs

Sure. Edit /etc/fstab to mount your the Data partition to some folder. Then bookmark that folder  and it will appear in Places->Bookmarks. Or   add the folder to your top panel by dragging the folder to your top panel. It might also be possible to edit the Places menu and have it appear directly in  Places (but I don't know how to do that).

---

### Post by Jammanuser on 2009-01-11
> **meierfra. said:**
> Sure. Edit /etc/fstab to mount your the Data partition to some folder. Then bookmark that folder  and it will appear in Places->Bookmarks. Or   add the folder to your top panel by dragging the folder to your top panel. It might also be possible to edit the Places menu and have it appear directly in  Places (but I don't know how to do that).

Thanks. :) I will try that, and if I have any more questions, i will just ask.

Thanks for all your help! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-11
AHA! :guitar: I just found something that you might find interesting, Meierfra! :D

[http://www.terabyteunlimited.com/kb/article.php?id=040](http://www.terabyteunlimited.com/kb/article.php?id=040)

> [COLOR="Red"]Can I Slide or Resize Linux Partitions?[/COLOR]
BootIt NG allows you to slide, copy, or [COLOR="Red"]resize[/COLOR] a Linux partition, but cannot resize the file system itself.  Please refer to the article "How To Resize Linux Partitions" for more information. 

[http://terabyteunlimited.com/kb/article.php?id=132](http://terabyteunlimited.com/kb/article.php?id=132)

> [COLOR="Red"]How To Resize Linux Partitions[/COLOR]

This article covers 2 methods of resizing Linux partitions, with information specific to BootIt NG users.

Warning: When resizing any partition, there is always some risk of data loss, regardless of which method is used to resize it. It is highly recommended that you have a reliable backup of the partition (such as a partition image) before proceeding with the resize operation.

Method 1: Use the GParted Live CD to resize in one step. This method is appropriate only for BootIt NG users who limit primaries, meaning that the Limit Primaries setting in the Settings dialog is checked. GParted is a graphical partitioning utility, and is available on many Linux Live CDs, as well as on many installation CDs that double as Live CDs.  The most commonly used Live CD for this purpose is probably the GParted Live CD, which is a bootable CD containing primarily the GParted program. It can be used to resize Linux partitions in one step from a graphical environment. For more information on how to use GParted, please refer to the GParted documentation.

Caution: GParted will not be appropriate for resizing partitions on systems where BootIt NG is configured to not limit primaries, meaning the Limit Primaries setting in the Settings dialog is not checked. This is because when primaries are not limited, all partitions known to BootIt NG may not be in the MBR partition table at any given time. GParted will see any partition not included in the MBR partition table as unpartitioned space, and therefore could overwrite existing partitions that it doesn't know about. This will cause data loss. For this situation, Method 2 described below is recommended.

Method 2:  Use the combination of BootIt NG and the Linux file system resizing utilities. This method is appropriate for BootIt NG users who do not limit primaries, as well as for those that do. It involves a two step process; one to resize the partition itself using BootIt NG, and the other to resize the file system contained in the partition using the appropriate Linux file system resizing utility. Using this method will require BootIt NG as well as a Live CD containing the Linux file system resizing software. The Linux file system resizing utilities are available on the IFL Boot Disk (Image for Linux), as well as on many Linux Live CDs such as Knoppix.

The two most common Linux file systems are ext2/ext3 and reiserfs. Both of these file systems have a set of utility programs associated with them, and in both cases the program set includes a file system resizing utility. For ext2/3 the resize utility is resize2fs, while for reiserfs the resize utility is resize_reiserfs. Both are strictly command line utilities, and both will resize only the file system, and not the actual partition.

The procedure for resizing a Linux partition with this method is different depending on whether you are expanding or shrinking the partition. The steps must be performed in a different order. The following are example sequences of how to expand and shrink a Linux partition using the combination of BootIt NG and the Linux resizing utilities on the IFL Boot Disk.

Expanding a partition: The Linux file system resizing utilities will not expand a file system beyond the boundaries of the existing partition. Therefore, the partition itself must be made larger first, and then the file system can be expanded to fill the larger partition. As an example, the following sequence of steps will expand an ext2/3 Linux partition from 2000 MB to 3000 MB:

1. [COLOR="Red"]In BootIt NG, highlight the 2000 MB Linux partition in Partition Work, and choose Resize.[/COLOR]

2. In the New Size dialog, enter 3000 and choose OK. The actual resulting size displayed after you choose the OK button may be be slightly less than 3000 due to partition alignment requirements.

3. Reboot the system from the IFL Boot Disk, and then exit to the Linux command prompt from the main menu.

4. You will need to know the Linux designation for the partition being resized (such as /dev/sda2 or /dev/sdb3). If unfamiliar with this, please refer to the KB article Overview of working with partitions in Linux for an explanation. For this example we will use /dev/sdb2 as the partition to resize.

5. Run the command  'e2fsck  -f  /dev/sdb2' to check for file system errors before resizing. If you skip this step, the resize2fs utility may refuse to run, and in that case it will display a message prompting you to run the e2fsck command.

6. Run the command 'resize2fs  -p  /dev/sdb2' to expand the ext2/3 file system to fill the 3000 MB partition. Note that when no size is given on the command line, the default is to expand the file system to match the size of the partition.

Shrinking a partition: When shrinking a partition, the file system must be resized first to the smaller size, and then [COLOR="Red"]BootIt NG can be used to shrink the partition to match[/COLOR]. Note that BootIt NG will not make a Linux partition smaller than the file system it contains. As an example, the following sequence of steps will shrink an ext2/3 Linux partition from 3000 MB to 2000 MB:

1. Boot the system from the IFL Boot Disk, and then exit to the Linux command prompt from the main menu.

2. You will need to know the Linux designation for the partition being resized (such as /dev/sda2 or /dev/sdb3). If unfamiliar with this, please refer to the KB article Overview of working with partitions in Linux for an explanation. For this example we will use /dev/sdb2 as the partition to resize.

3. Run the command  'e2fsck  -f  /dev/sdb2' to check for file system errors before resizing. If you skip this step, the resize2fs utility may refuse to run, and in that case it will display a message prompting you to run the e2fsck command.
4. Run the command 'resize2fs  -p  /dev/sdb2  2000M' to shrink the ext2/3 file system from 3000 MB to 2000 MB. Note that for the size parameter, the suffixes 'K' for kilobytes, 'M' for megabytes, 'G' for gigabytes, or 's' for sectors can be used. In this case we wanted 2000 MB, so 2000M was used.

5. Reboot the system into BootIt NG, highlight the Linux partition in Partition Work, and then choose Resize. Note that in the Resize dialog, BootIt NG will now display the new size of the file system as Min Size.

6. In the New Size dialog enter 2000, then choose OK. Note that in some cases, BootIt NG may not accept the value displayed as Min Size due to partition alignment. In that case, increase the new partition size in increments of 1 or 2 MB at a time until it does accept it - you shouldn't need to go any higher than 8 MB above the Min Size value displayed.

Additional Information: The 2 examples above are specific to resizing an ext2 or ext3 partition, and therefore use the resize2fs utility for resizing the file system, and the e2fsck utility to check the file system. If you are working with a reiserfs partition instead, you will need to substitute the appropriate reiserfs utilities. The following would be the equivalent commands if working with reiserfs:

Check the file system:  'reiserfsck  /dev/sdb2'

Expand file system to fill existing partition:  'resize_reiserfs  /dev/sdb2'

Shrink file system to 2000 MB:  'resize_reiserfs  -s 2000M  /dev/sdb2'

The procedures for reiserfs would otherwise be the same as for the ext2/3 examples given above.

I believe that answers the question whether BING can resize Linux partitions or not! :lolflag:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-11
As you can see from the last quote, BING can resize the Linux partition itself, but can not resize the filesystem. To resize the filesystem, one will have to use the [**resize2fs**]("http://linux.die.net/man/8/resize2fs") software which you can find on the [IFL Boot Disk (Image for Linux)]("http://www.terabyteunlimited.com/image-for-linux.htm"), as well as on many Linux Live CDs such as Knoppix. 

But at least BING can resize the partition itself! :lolflag:

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-11
EDIT: delete

---

### Post by Jammanuser on 2009-01-11
EDIT: delete

---

### Post by meierfra. on 2009-01-17
Yesterday  I used BING to shrink an NTFS partition from 16GB to 9GB and it took BING  only a couple of minutes. Very impressive.  The partition was a fresh install of Windows 7, containing 6GB of data, so it wasn't defragged at all. But still I'm sure it would have taken gparted much longer.

Jammanuser:   I have been working on my boot_info_script all week, so that it can  read BING's MPT and also  gather information from the all the partitions (not only the once in the MBR). It's working fine on my computer. But you are the only person I know who uses BING: Could you do me a favour and try out the script:

```
cd ~/Desktop &&  &wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.sh'& sudo bash boot_info_script.sh
```

and  post  the content of "RESULTS.txt"

---

### Post by Jammanuser on 2009-01-17
> **meierfra. said:**
> Yesterday, I used BING to shrink an NTFS partition from 16GB to 9GB and it took BING  only a couple of minutes. Very impressive.  The partition was a fresh install of Windows 7, containing 6GB of data, so it wasn't defragged at all. But still I'm sure it would have taken gparted much longer.

Jammanuser:   I have been working on my boot_info_script all week, so that it can  read BING's MPT and also  gather information from the all the partitions (not only the once in the MBR). It's working fine on my computer. But you are the only person I know who uses BING: Could you do me a favour and try out the script:

```
cd ~/Desktop &&  &wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.sh'& sudo bash boot_info_script.sh
```

and  post  the content of "RESULTS.txt"

Like I said, BING is much faster at resizing than Gparted! :guitar: 

Yes, I will create a new boot_info_results.txt, so you can take a look at it...but wouldn't it be possible for you to do the same thing? ;) Or have you already thrown away BING? :)

-Jam man

:guitar:

---

### Post by meierfra. on 2009-01-17
> But wouldn't it be possible for you to do the same thing?

I did. Actually  several times, and each time I found another bug, until it finally run without problems. I just would like to make sure that it also runs well on other computers.


> boot_info_[COLOR="Red"]results.txt[/COLOR]

Just to make sure. The name of the script is  boot_info_[COLOR="Red"]script.sh[/COLOR] and the file you have to post  is  "RESULTS.txt"

Thanks.

---

### Post by Jammanuser on 2009-01-17
> **meierfra. said:**
> 
Just to make sure. The name of the script is  boot_info_[COLOR="Red"]script.sh[/COLOR] and the file you have to post  is  "RESULTS.txt"


Yeah, that's what I meant. :) You changed the names on me! :guitar:
I will post it right away, once I boot into Ubuntu (as I'm in XP right now)...

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-17
You got the command wrong, so it took a bit longer than normal for me to obtain the RESULTS.txt file. It should have been:

```
cd ~/Desktop [COLOR="Red"]&& wget[/COLOR] 'http://home.comcast.net/~ubuntu_grub/boot_info_script.[COLOR="Red"]sh' && sudo[/COLOR] bash boot_info_script.sh
```

and not:

```
cd ~/Desktop [COLOR="Red"]&&  &wget[/COLOR] 'http://home.comcast.net/~ubuntu_grub/boot_info_script.[COLOR="Red"]sh'& sudo[/COLOR] bash boot_info_script.sh
```

But anyway, here's the contents of the RESULTS.txt file:

```
============================= Boot Info Summary: ==============================

 => BootIt NG is installed in the MBR of /dev/sda

EMBR: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

OS-2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/loop0': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/loop0 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/loop0 sda1 ntfs-3g force 0 0

Ubuntu-real: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of 
                       Ubuntu-real and looks at sector 527464797 of the same 
                       hard drive for the stage2 file and on partition #4 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

Linux swap: _________________________________________________________________________

    File system:       swap

WinXP: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

Recovery: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

Random-1: _________________________________________________________________________

    File system:       Extended Partition

BootIT NG: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BootIt: Fat16
    Boot sector info:  According to the info in the boot sector, BootIT NG 
                       has 0 sectors, but according to the info from fdisk, 
                       it has 618293655 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

    Ind  Label                  Start         End  Type   ?
      1  EMBR                      63       80324    16   0
      3  OS-2                20560325   506706164     7   0
      4  Ubuntu-real        506706165   547655849    83   0
      2  Linux swap         547655850   556861094    82   0
    151  WinXP              556861095   618293654     c  20
     29  Recovery               80325    20547134    17  20
    223  Random-1           618309720   625137344     f  20

	Partition     Boot       Start         End        Size  Type

    180  BootIT NG          618293655   618309719    df  60

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="WINXP-OS" UUID="5BE6-0200" TYPE="vfat" 
/dev/sda2: UUID="94cd6bbb-4b8c-437e-abef-fb744053d906" TYPE="swap" 
/dev/sda3: UUID="2C6EDB496EDB0B0A" LABEL="OS" TYPE="ntfs" 
/dev/sda4: LABEL="Ubuntu-real" UUID="dd4f326a-2165-40f6-aed4-2b44b15b71a5" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gorilla/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gorilla)

======================= Ubuntu-real/boot/grub/menu.lst: =======================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. k

```

---

### Post by meierfra. on 2009-01-17
> &&  &wget 

Sorry about that.


I seems that my script worked just fine, but it looks like you did not post the whole  RESULTS.txt  file. Is that true?  Could you post the rest?

Thanks.

---

### Post by Jammanuser on 2009-01-17
> **meierfra. said:**
> 
I seems that my script worked just fine, but it looks you did not post the whole  RESULTS.txt  file. Is that true?  Could you post the rest?

Thanks.

HUH? :shock: I could have sworn I selected the whole thing, before copying...but just to make sure, I will copy it again, this time using **ctrl** and **a** to grab the whole thing. :-k

Standby.

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-18
Here it is. I guess you were right. Part of the text must have got chopped off the first time I posted it, somehow, but I didn't notice it...

Anyhow, here it is (Let me know if the script is working alright...I would certainly like to know):

```
============================= Boot Info Summary: ==============================

 => BootIt NG is installed in the MBR of /dev/sda

EMBR: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

OS-2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/loop0': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/loop0 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/loop0 sda1 ntfs-3g force 0 0

Ubuntu-real: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of 
                       Ubuntu-real and looks at sector 527464797 of the same 
                       hard drive for the stage2 file and on partition #4 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

Linux swap: _________________________________________________________________________

    File system:       swap

WinXP: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

Recovery: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

Random-1: _________________________________________________________________________

    File system:       Extended Partition

BootIT NG: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BootIt: Fat16
    Boot sector info:  According to the info in the boot sector, BootIT NG 
                       has 0 sectors, but according to the info from fdisk, 
                       it has 618293655 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

    Ind  Label                  Start         End  Type   ?
      1  EMBR                      63       80324    16   0
      3  OS-2                20560325   506706164     7   0
      4  Ubuntu-real        506706165   547655849    83   0
      2  Linux swap         547655850   556861094    82   0
    151  WinXP              556861095   618293654     c  20
     29  Recovery               80325    20547134    17  20
    223  Random-1           618309720   625137344     f  20

	Partition     Boot       Start         End        Size  Type

    180  BootIT NG          618293655   618309719    df  60

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="WINXP-OS" UUID="5BE6-0200" TYPE="vfat" 
/dev/sda2: UUID="94cd6bbb-4b8c-437e-abef-fb744053d906" TYPE="swap" 
/dev/sda3: UUID="2C6EDB496EDB0B0A" LABEL="OS" TYPE="ntfs" 
/dev/sda4: LABEL="Ubuntu-real" UUID="dd4f326a-2165-40f6-aed4-2b44b15b71a5" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gorilla/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gorilla)

======================= Ubuntu-real/boot/grub/menu.lst: =======================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows XP
root (hd0,0)
chainloader +1


title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1

============================ Ubuntu-real/etc/fstab: ============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda4
UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda3
UUID=2C6EDB496EDB0B0A       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda2
UUID=94cd6bbb-4b8c-437e-abef-fb744053d906      none            swap        sw          0   0


============================== Ubuntu-real/boot: ==============================

total 38232
drwxr-xr-x  3 root root    4096 2009-01-11 20:05 .
drwxr-xr-x 22 root root    4096 2009-01-11 22:03 ..
-rw-r--r--  1 root root  504280 2009-01-08 03:01 abi-2.6.27-11-generic
-rwxr-xr-x  1 root root  503560 2008-12-15 18:23 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 16:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85310 2009-01-08 03:01 config-2.6.27-11-generic
-rwxr-xr-x  1 root root   85316 2008-12-15 18:23 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 16:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-17 15:13 grub
-rw-r--r--  1 root root 8674428 2009-01-11 20:05 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8668699 2008-12-21 01:39 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8671708 2008-12-21 16:10 initrd.img-2.6.27-9-generic
-rwxr-xr-x  1 root root  124152 2008-12-15 18:23 memtest86+.bin
-rw-r--r--  1 root root 1354843 2009-01-08 03:01 System.map-2.6.27-11-generic
-rwxr-xr-x  1 root root 1352144 2008-12-15 18:23 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 16:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1131 2009-01-08 03:05 vmcoreinfo-2.6.27-11-generic
-rwxr-xr-x  1 root root    1130 2008-12-15 18:23 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 16:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2344000 2009-01-08 03:01 vmlinuz-2.6.27-11-generic
-rwxr-xr-x  1 root root 2339712 2008-12-15 18:23 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 16:30 vmlinuz-2.6.27-9-generic

============================ Ubuntu-real/boot/grub: ============================

total 344
drwxr-xr-x 2 root root   4096 2009-01-17 15:13 .
drwxr-xr-x 3 root root   4096 2009-01-11 20:05 ..
-rwxr-xr-x 1 root root    191 2008-12-15 18:23 default
-rwxr-xr-x 1 root root     30 2008-12-15 18:23 device.map
-rwxr-xr-x 1 root root   8108 2008-12-15 18:24 e2fs_stage1_5
-rwxr-xr-x 1 root root   7856 2008-12-15 18:24 fat_stage1_5
-rwxr-xr-x 1 root root   8712 2008-12-15 18:24 jfs_stage1_5
-rwxr-xr-x 1 root root   4632 2009-01-17 15:13 menu.lst
-rw-r--r-- 1 root root   4427 2009-01-16 13:54 menu.lst~
-rwxr-xr-x 1 root root   7352 2008-12-15 18:24 minix_stage1_5
-rwxr-xr-x 1 root root   9756 2008-12-15 18:24 reiserfs_stage1_5
-rwxr-xr-x 1 root root    512 2008-12-15 18:24 stage1
-rwxr-xr-x 1 root root 121460 2008-12-15 18:24 stage2
-rwxr-xr-x 1 root root 121460 2008-12-15 18:24 stage2_eltorito
-rwxr-xr-x 1 root root   9556 2008-12-15 18:24 xfs_stage1_5

=============================== WinXP/boot.ini: ===============================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn



=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/loop0

00000000  e9 57 00 42 4f 4f 54 49  54 58 58 00 02 04 01 00  |.W.BOOTITXX.....|
00000010  02 00 02 00 00 f8 4f 00  3f 00 ff 00 3f 00 00 00  |......O.?...?...|
00000020  86 39 01 00 80 00 29 00  02 a8 9d 4e 45 57 20 4d  |.9....)....NEW M|
00000030  42 52 20 45 4e 54 46 41  54 31 36 20 20 20 00 00  |BR ENTFAT16   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 ea 5f 00 c0 07 fc  |..........._....|
00000060  0e 1f be 6e 00 e8 ce 00  33 c0 cd 16 cd 19 0d 0a  |...n....3.......|
00000070  54 68 69 73 20 70 61 72  74 69 74 69 6f 6e 20 64  |This partition d|
00000080  6f 65 73 20 6e 6f 74 20  63 6f 6e 74 61 69 6e 20  |oes not contain |
00000090  61 6e 20 6f 70 65 72 61  74 69 6e 67 20 73 79 73  |an operating sys|
000000a0  74 65 6d 2e 0d 0a 49 66  20 79 6f 75 20 61 72 65  |tem...If you are|
000000b0  20 61 62 6f 75 74 20 74  6f 20 69 6e 73 74 61 6c  | about to instal|
000000c0  6c 20 61 20 6e 65 77 20  4f 53 20 74 68 65 6e 20  |l a new OS then |
000000d0  69 6e 73 65 72 74 20 74  68 65 0d 0a 69 6e 73 74  |insert the..inst|
000000e0  61 6c 6c 61 74 69 6f 6e  20 64 69 73 6b 65 74 74  |allation diskett|
000000f0  65 20 69 6e 74 6f 20 64  72 69 76 65 20 41 3a 0d  |e into drive A:.|
00000100  0a 0a 50 72 65 73 73 20  61 6e 79 20 6b 65 79 20  |..Press any key |
00000110  74 6f 20 72 75 6e 20 74  68 65 20 42 49 4f 53 20  |to run the BIOS |
00000120  62 6f 6f 74 73 74 72 61  70 20 6c 6f 61 64 65 72  |bootstrap loader|
00000130  2e 2e 2e 0d 0a 00 06 53  50 56 57 ac 3c 00 74 0b  |.......SPVW.<.t.|
00000140  bb 07 00 b4 0e 56 cd 10  5e eb f0 5f 5e 58 5b 07  |.....V..^.._^X[.|
00000150  c3 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/dev/loop0: unknown volume type
```

---

### Post by Jammanuser on 2009-01-18
hmm...I just noticed this section in your RESULTS.txt:

```
$[COLOR="Red"]LogFile indicates unclean shutdown[/COLOR] (0, 0)
Failed to mount '/dev/loop0': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

```

:lol: That would be because damn Vista has been giving me some trouble lately, and I have had to do improper shutdowns several times, because it would freeze up on me! Damn Vista...:mad: It wont even let me finish the defrag I'm trying to do! :mad: :mad: :mad: I keep having to shut it down (improperly) before it completes! AHHHHH! :mad:

:D

-Jam man

:guitar:

EDIT: Finally got it to complete in Safe Mode...

---

### Post by Jammanuser on 2009-01-18
hmm...what exactly is this supposed to mean? :shock:

```
Boot sector info:  According to the info in the boot sector, BootIT NG 
                       has 0 sectors, but according to the info from fdisk, 
                       it has 618293655 sectors.

```

So fdisk and "the info in the boot sector" tell a different story? what exactly is reading the info in the boot sector in this instance? why would one say the BING partition has 0 sectors, but the other one say it has 618293655 sectors? It seems very stange...
Is this a problem with your script, or is it something else? And if something else, what exactly?

Looking forward to your reply.

-Jam man

:guitar:

---

### Post by meierfra. on 2009-01-18
> So fdisk and "the info in the boot sector" tell a different story? what exactly is reading the info in the boot sector in this instance? why would one say the BING partition has 0 sectors, but the other one say it has 618293655 sectors? It seems very stange...
Is this a problem with your script, or is it something else? And if something else, what exactly?
Both:

Problem with the script:
The script accidentally displayed the starting sector of the partition and not the size. 

something else:
Your boot sector reports the size of the partition has 0. This is quite common for vfat partitions, and does not cause any problems, unless  the boot sector is actually used  during boot up.    

I fixed  that problem with the script, and also made some changes how the partition table is displayed.

 Thanks for your help.

---

### Post by Jammanuser on 2009-01-18
> **meierfra. said:**
> Both:

Problem with the script:
The script accidentally displayed the starting sector of the partition and not the size. 

something else:
Your boot sector reports the size of the partition has 0. This is quite common for vfat partitions, and does not cause any problems, unless  the boot sector is actually used  during boot up.    

I fixed  that problem with the script, and also made some changes how the partition table is displayed.

 Thanks for your help.

Ok. Glad to be of assistance. :) 

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-18
Actually, Meierfra, maybe the two ntldrs aren't a problem with your script after all! :) Or at least not in the way we thought before...

```
WinXP: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com
```

I just noticed, it shows two ntdetect.coms as well, so I think the reason its detecting two is because there **is** two! :guitar: I'm not sure if you got this before, but I used EasyBCD to add an entry in my Vista bootloader for XP...which requires copying over the boot.ini, ntldr, and ntdetect.com from XP into your "system" partition, before it will work, which means there is a copy of both ntldr and ntdetect.com in my Vista partition, as well as the XP one! :) So it must be detecting the ones in my Vista partition as well, only perhaps confusing it with XP! 

Cheers! Maybe it wasn't a bug in your script after all...unless its not supposed to read XP boot files on any other than the XP partition! ;)

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-18
Here's the most recent RESULTS.txt file, which I created afresh just a few minutes ago, after learning you made changes to your script...thought you might like to take a look at the new results. ;)

```
============================= Boot Info Summary: ==============================

 => BootIt NG is installed in the MBR of /dev/sda

EMBR: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

OS-2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block. BootPart 
                       in the file 
                       /NST/nst_grub-95E2F748A3EF60E57EA4359261E8637F.mbr is 
                       trying to chain load sector #506706165 on boot drive 
                       #1 BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #506706165 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /ubuntu/disks/boot/grub/menu.lst 
                       /boot.ini /bootmgr /ntldr /ntdetect.com /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /boot /ubuntu/disks 
                       /ubuntu/disks/boot/ /ubuntu/disks/boot/grub 
                       /ubuntu/disks/boot/grub /NST

Ubuntu-real: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of 
                       Ubuntu-real and looks at sector 527464797 of the same 
                       hard drive for the stage2 file and on partition #4 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

Linux swap: _________________________________________________________________________

    File system:       swap

WinXP: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

Recovery: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: you must specify the filesystem type

Random-1: _________________________________________________________________________

    File system:       Extended Partition

BootIT NG: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BootIt: Fat16
    Boot sector info:  According to the info in the boot sector, BootIT NG 
                       has 0 sectors, but according to the info from fdisk, 
                       it has 618293655 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

    Ind  Label                  Start         End  Type   ?
      1  EMBR                      63       80324    16   0
      3  OS-2                20560325   506706164     7   0
      4  Ubuntu-real        506706165   547655849    83   0
      2  Linux swap         547655850   556861094    82   0
    151  WinXP              556861095   618293654     c  20
     29  Recovery               80325    20547134    17  20
    223  Random-1           618309720   625137344     f  20

	Partition     Boot       Start         End        Size  Type

    180  BootIT NG          618293655   618309719    df  60

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="WINXP-OS" UUID="5BE6-0200" TYPE="vfat" 
/dev/sda2: UUID="94cd6bbb-4b8c-437e-abef-fb744053d906" TYPE="swap" 
/dev/sda3: UUID="2C6EDB496EDB0B0A" LABEL="OS" TYPE="ntfs" 
/dev/sda4: LABEL="Ubuntu-real" UUID="dd4f326a-2165-40f6-aed4-2b44b15b71a5" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda3 on /media/drv0 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gorilla/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gorilla)
/dev/sda1 on /media/WinXP-OS type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

============================== OS-2/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD



#This is a comment. Comments are prefixed with a '#'



default 0		#Pick the task to be run if the user doesn't pick one within the time limit.

timeout 10		#Give the user 10 seconds to choose a task.



#We use the "title" keyword to indicate a new entry in the menu.



title 		Windows XP	#This is our first entry - it's number 0

find --set-root	/NTLDR  	#Search for NTLDR on all partitions. Once found, use that partition as root.

makeactive  			#Make this the active partition

chainloader /NTLDR		#Run NTLDR, the Windows XP bootloader

#If we're using a menu, we don't need to use the `boot` command - it's automatically implied.



#This is our second entry

title Ubuntu Linux
root (hd0,3) #Load Ubuntu from the 1st harddrive's 4th partition.
chainloader +1
#End Ubuntu entry

#That's it!


==================== OS-2/ubuntu/disks/boot/grub/menu.lst: ====================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst



================================ OS-2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NOEXECUTE=OPTIN 
================================== OS-2/boot: ==================================

total 4168
drwxrwxrwx 1 root root    8192 2009-01-07 15:41 .
drwxrwxrwx 1 root root   12288 2009-01-17 23:32 ..
-rwxrwxrwx 1 root root   28672 2009-01-17 23:32 BCD
-rwxrwxrwx 1 root root  262144 2008-12-10 14:34 BCD.Backup.0001
-rwxrwxrwx 1 root root  262144 2009-01-17 23:32 BCD.LOG
-rwxrwxrwx 2 root root       0 2008-02-03 16:06 BCD.LOG1
-rwxrwxrwx 2 root root       0 2008-02-03 16:06 BCD.LOG2
-rwxrwxrwx 1 root root    1024 2008-03-04 09:08 bootfix.bin
-rwxrwxrwx 1 root root 3170304 2008-03-04 09:08 boot.sdi
-rwxrwxrwx 1 root root   65536 2008-02-03 16:06 bootstat.dat
drwxrwxrwx 1 root root       0 2009-01-07 15:41 cs-CZ
drwxrwxrwx 1 root root       0 2009-01-07 15:41 da-DK
drwxrwxrwx 1 root root       0 2009-01-07 15:41 de-DE
drwxrwxrwx 1 root root       0 2009-01-07 15:41 el-GR
drwxrwxrwx 1 root root       0 2009-01-07 15:41 en-US
drwxrwxrwx 1 root root       0 2009-01-07 15:41 es-ES
-rwxrwxrwx 1 root root    2048 2008-03-04 15:05 etfsboot.com
drwxrwxrwx 1 root root       0 2009-01-07 15:41 fi-FI
drwxrwxrwx 1 root root    4096 2008-02-03 16:06 fonts
drwxrwxrwx 1 root root       0 2009-01-07 15:41 fr-FR
drwxrwxrwx 1 root root       0 2009-01-07 15:41 hu-HU
drwxrwxrwx 1 root root       0 2009-01-07 15:41 it-IT
drwxrwxrwx 1 root root       0 2009-01-07 15:41 ja-JP
drwxrwxrwx 1 root root       0 2009-01-07 15:41 ko-KR
-rwxrwxrwx 1 root root  405248 2008-10-17 22:30 memtest.exe
drwxrwxrwx 1 root root       0 2009-01-07 15:41 nb-NO
drwxrwxrwx 1 root root       0 2009-01-07 15:41 nl-NL
drwxrwxrwx 1 root root       0 2009-01-07 15:41 pl-PL
drwxrwxrwx 1 root root       0 2009-01-07 15:41 pt-BR
drwxrwxrwx 1 root root       0 2009-01-07 15:41 pt-PT
-rwxrwxrwx 1 root root   20480 2008-12-10 21:30 Recovery.bcd
-rwxrwxrwx 2 root root   17408 2008-12-10 21:30 Recovery.bcd.LOG
-rwxrwxrwx 2 root root       0 2008-12-10 21:30 Recovery.bcd.LOG1
-rwxrwxrwx 2 root root       0 2008-12-10 21:30 Recovery.bcd.LOG2
drwxrwxrwx 1 root root       0 2009-01-07 15:41 ru-RU
drwxrwxrwx 1 root root       0 2009-01-07 15:41 sv-SE
drwxrwxrwx 1 root root       0 2009-01-07 15:41 tr-TR
drwxrwxrwx 1 root root       0 2009-01-07 15:41 zh-CN
drwxrwxrwx 1 root root       0 2009-01-07 15:41 zh-HK
drwxrwxrwx 1 root root       0 2009-01-07 15:41 zh-TW

============================== OS-2/ubuntu/disks: ==============================

total 14648448
drwxrwxrwx 1 root root           0 2008-12-13 00:03 .
drwxrwxrwx 1 root root        4096 2008-12-12 15:54 ..
drwxrwxrwx 1 root root        4096 2008-12-12 17:15 boot
-rwxrwxrwx 2 root root 14000000000 2009-01-16 14:29 root.disk
drwxrwxrwx 1 root root           0 2008-12-12 15:53 shared
-rwxrwxrwx 2 root root  1000000000 2008-12-12 17:10 swap.disk

=========================== OS-2/ubuntu/disks/boot/: ===========================

total 13016
drwxrwxrwx 1 root root    4096 2008-12-12 17:15 .
drwxrwxrwx 1 root root       0 2008-12-13 00:03 ..
-rwxrwxrwx 1 root root  503560 2008-10-24 01:55 abi-2.6.27-7-generic
-rwxrwxrwx 1 root root   85316 2008-10-24 01:55 config-2.6.27-7-generic
drwxrwxrwx 1 root root       0 2008-12-12 17:15 grub
-rwxrwxrwx 1 root root 8901816 2008-12-12 17:15 initrd.img-2.6.27-7-generic
-rwxrwxrwx 1 root root  124152 2008-09-11 14:11 memtest86+.bin
-rwxrwxrwx 1 root root 1352144 2008-10-24 01:55 System.map-2.6.27-7-generic
-rwxrwxrwx 1 root root    1130 2008-10-24 01:57 vmcoreinfo-2.6.27-7-generic
-rwxrwxrwx 1 root root 2339712 2008-10-24 01:55 vmlinuz-2.6.27-7-generic

========================= OS-2/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2008-12-12 17:15 .
drwxrwxrwx 1 root root 4096 2008-12-12 17:15 ..
-rwxrwxrwx 1 root root  191 2008-12-12 17:15 default
-rwxrwxrwx 1 root root   30 2008-12-12 17:15 device.map
-rwxrwxrwx 1 root root 5135 2008-12-15 18:24 menu.lst
-rwxrwxrwx 1 root root 4261 2008-12-12 17:15 menu.lst~

========================= OS-2/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2008-12-12 17:15 .
drwxrwxrwx 1 root root 4096 2008-12-12 17:15 ..
-rwxrwxrwx 1 root root  191 2008-12-12 17:15 default
-rwxrwxrwx 1 root root   30 2008-12-12 17:15 device.map
-rwxrwxrwx 1 root root 5135 2008-12-15 18:24 menu.lst
-rwxrwxrwx 1 root root 4261 2008-12-12 17:15 menu.lst~

================================== OS-2/NST: ==================================

total 37
drwxrwxrwx 1 root root  4096 2009-01-04 00:00 .
drwxrwxrwx 1 root root 12288 2009-01-17 23:32 ..
-rwxrwxrwx 1 root root  1065 2008-12-25 13:28 menu.lst
-rwxrwxrwx 1 root root  1065 2008-12-25 13:27 menu.lst~
-rwxrwxrwx 1 root root  8192 2008-04-08 11:50 NeoGrub.mbr
-rwxrwxrwx 2 root root   512 2008-12-23 12:00 nst_grub-95E2F748A3EF60E57EA4359261E8637F.mbr
-rwxrwxrwx 1 root root   512 2008-12-15 00:56 nst_grub.mbr

======================= Ubuntu-real/boot/grub/menu.lst: =======================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows XP
root (hd0,0)
chainloader +1


title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1

============================ Ubuntu-real/etc/fstab: ============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda4
UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda3
UUID=2C6EDB496EDB0B0A       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda2
UUID=94cd6bbb-4b8c-437e-abef-fb744053d906      none            swap        sw          0   0


============================== Ubuntu-real/boot: ==============================

total 38232
drwxr-xr-x  3 root root    4096 2009-01-11 20:05 .
drwxr-xr-x 22 root root    4096 2009-01-11 22:03 ..
-rw-r--r--  1 root root  504280 2009-01-08 03:01 abi-2.6.27-11-generic
-rwxr-xr-x  1 root root  503560 2008-12-15 18:23 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 16:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85310 2009-01-08 03:01 config-2.6.27-11-generic
-rwxr-xr-x  1 root root   85316 2008-12-15 18:23 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 16:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-17 15:13 grub
-rw-r--r--  1 root root 8674428 2009-01-11 20:05 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8668699 2008-12-21 01:39 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8671708 2008-12-21 16:10 initrd.img-2.6.27-9-generic
-rwxr-xr-x  1 root root  124152 2008-12-15 18:23 memtest86+.bin
-rw-r--r--  1 root root 1354843 2009-01-08 03:01 System.map-2.6.27-11-generic
-rwxr-xr-x  1 root root 1352144 2008-12-15 18:23 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 16:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1131 2009-01-08 03:05 vmcoreinfo-2.6.27-11-generic
-rwxr-xr-x  1 root root    1130 2008-12-15 18:23 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 16:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2344000 2009-01-08 03:01 vmlinuz-2.6.27-11-generic
-rwxr-xr-x  1 root root 2339712 2008-12-15 18:23 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 16:30 vmlinuz-2.6.27-9-generic

============================ Ubuntu-real/boot/grub: ============================

total 344
drwxr-xr-x 2 root root   4096 2009-01-17 15:13 .
drwxr-xr-x 3 root root   4096 2009-01-11 20:05 ..
-rwxr-xr-x 1 root root    191 2008-12-15 18:23 default
-rwxr-xr-x 1 root root     30 2008-12-15 18:23 device.map
-rwxr-xr-x 1 root root   8108 2008-12-15 18:24 e2fs_stage1_5
-rwxr-xr-x 1 root root   7856 2008-12-15 18:24 fat_stage1_5
-rwxr-xr-x 1 root root   8712 2008-12-15 18:24 jfs_stage1_5
-rwxr-xr-x 1 root root   4632 2009-01-17 15:13 menu.lst
-rw-r--r-- 1 root root   4427 2009-01-16 13:54 menu.lst~
-rwxr-xr-x 1 root root   7352 2008-12-15 18:24 minix_stage1_5
-rwxr-xr-x 1 root root   9756 2008-12-15 18:24 reiserfs_stage1_5
-rwxr-xr-x 1 root root    512 2008-12-15 18:24 stage1
-rwxr-xr-x 1 root root 121460 2008-12-15 18:24 stage2
-rwxr-xr-x 1 root root 121460 2008-12-15 18:24 stage2_eltorito
-rwxr-xr-x 1 root root   9556 2008-12-15 18:24 xfs_stage1_5

=============================== WinXP/boot.ini: ===============================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn



=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/loop0

00000000  e9 57 00 42 4f 4f 54 49  54 58 58 00 02 04 01 00  |.W.BOOTITXX.....|
00000010  02 00 02 00 00 f8 4f 00  3f 00 ff 00 3f 00 00 00  |......O.?...?...|
00000020  86 39 01 00 80 00 29 00  02 a8 9d 4e 45 57 20 4d  |.9....)....NEW M|
00000030  42 52 20 45 4e 54 46 41  54 31 36 20 20 20 00 00  |BR ENTFAT16   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 ea 5f 00 c0 07 fc  |..........._....|
00000060  0e 1f be 6e 00 e8 ce 00  33 c0 cd 16 cd 19 0d 0a  |...n....3.......|
00000070  54 68 69 73 20 70 61 72  74 69 74 69 6f 6e 20 64  |This partition d|
00000080  6f 65 73 20 6e 6f 74 20  63 6f 6e 74 61 69 6e 20  |oes not contain |
00000090  61 6e 20 6f 70 65 72 61  74 69 6e 67 20 73 79 73  |an operating sys|
000000a0  74 65 6d 2e 0d 0a 49 66  20 79 6f 75 20 61 72 65  |tem...If you are|
000000b0  20 61 62 6f 75 74 20 74  6f 20 69 6e 73 74 61 6c  | about to instal|
000000c0  6c 20 61 20 6e 65 77 20  4f 53 20 74 68 65 6e 20  |l a new OS then |
000000d0  69 6e 73 65 72 74 20 74  68 65 0d 0a 69 6e 73 74  |insert the..inst|
000000e0  61 6c 6c 61 74 69 6f 6e  20 64 69 73 6b 65 74 74  |allation diskett|
000000f0  65 20 69 6e 74 6f 20 64  72 69 76 65 20 41 3a 0d  |e into drive A:.|
00000100  0a 0a 50 72 65 73 73 20  61 6e 79 20 6b 65 79 20  |..Press any key |
00000110  74 6f 20 72 75 6e 20 74  68 65 20 42 49 4f 53 20  |to run the BIOS |
00000120  62 6f 6f 74 73 74 72 61  70 20 6c 6f 61 64 65 72  |bootstrap loader|
00000130  2e 2e 2e 0d 0a 00 06 53  50 56 57 ac 3c 00 74 0b  |.......SPVW.<.t.|
00000140  bb 07 00 b4 0e 56 cd 10  5e eb f0 5f 5e 58 5b 07  |.....V..^.._^X[.|
00000150  c3 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/dev/loop0: unknown volume type
```

---

### Post by meierfra. on 2009-01-18
Looks like you didn't run the newest version.  This could be because

1)  I forgot to upload the newest version to the server. (Just to make sure I uploaded it right now)

2)  You did not download the newest version  before you run the script (seems unlikely)

3)  You did not deleted the old script and/or RESULTS.txt.  Then the new script  would be called "boot_info_script-1.sh" and/or the new RESULTS.txt  would be called RESULTS1.txt.

---

### Post by Jammanuser on 2009-01-18
> **meierfra. said:**
> Looks like you didn't run the newest version.  This could be because

1)  I forgot to upload the newest version to the server. (Just to make sure I uploaded it right now)

2)  You did not download the newest version  before you run the script (seems unlikely)

3)  You did not deleted the old script and/or RESULTS.txt.  Then the new script  would be called "boot_info_script-1.sh" and/or the new RESULTS.txt  would be called RESULTS1.txt.

I used the exact same command as last time to obtain and run the script. :) But yes, I did not delete my (two) older RESULTS.txt files, so the latest one that I posted was named RESULTS2.txt. ;)

Do you want me to download and run the script again?

I kept the old RESULTS.txt(s) because I wanted to compare the latest one with the last two, so I could tell exactly what changes you have made. :) But I could always move the old result files to some other dir than the desktop, and then download and run the script again...and that should produce a file with the name of "RESULTS.txt" if you want, though I'm not sure why that would make a difference. But its up to you...

I'll do it again if you want. ;)

-Jam man

:guitar:

---

### Post by meierfra. on 2009-01-19
> Do you want me to download and run the script again?
As long as you are volunteering, yes.
You can keep the RESULT.txt. Just make sure you delete the old script, before you download the new one. 

Thanks.

---

### Post by Jammanuser on 2009-01-19
> **meierfra. said:**
> As long as you are volunteering, yes.

Alright. I will do that, then. Just don't expect it until sometime tomorrow, because I have a few things I need to do today in the real world that takes precedence...:)
> 
You can keep the RESULT.txt. Just make sure you delete the old script, before you download the new one. 


Alright...I will do that, then, though I still don't quite understand why keeping the old script might mess things up. ;)

Cheers.

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-19
```
============================= Boot Info Summary: ==============================

 => BootIt NG is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       swap

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block. BootPart 
                       in the file 
                       /NST/nst_grub-95E2F748A3EF60E57EA4359261E8637F.mbr is 
                       trying to chain load sector #506706165 on boot drive 
                       #1 BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #506706165 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /ubuntu/disks/boot/grub/menu.lst 
                       /boot.ini /bootmgr /ntldr /ntdetect.com /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /boot /ubuntu/disks 
                       /ubuntu/disks/boot/ /ubuntu/disks/boot/grub 
                       /ubuntu/disks/boot/grub /NST

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda4 and 
                       looks at sector 527464797 of the same hard drive for 
                       the stage2 file and on partition #4 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c5a8d58

/dev/sda1        556,861,095  618,293,654   61,432,560   c W95 FAT32 (LBA)
/dev/sda2        547,655,850  556,861,094    9,205,245  82 Linux swap / Solaris
/dev/sda3         20,560,325  506,706,164  486,145,840   7 HPFS/NTFS
/dev/sda4     *  506,706,165  547,655,849   40,949,685  83 Linux

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="WINXP-OS" UUID="5BE6-0200" TYPE="vfat" 
/dev/sda2: UUID="94cd6bbb-4b8c-437e-abef-fb744053d906" TYPE="swap" 
/dev/sda3: UUID="2C6EDB496EDB0B0A" LABEL="OS" TYPE="ntfs" 
/dev/sda4: LABEL="Ubuntu-real" UUID="dd4f326a-2165-40f6-aed4-2b44b15b71a5" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda3 on /media/drv0 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gorilla/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gorilla)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn



=================== sda1: Location  of files loaded by Grub: ===================


============================== sda3/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD



#This is a comment. Comments are prefixed with a '#'



default 0		#Pick the task to be run if the user doesn't pick one within the time limit.

timeout 10		#Give the user 10 seconds to choose a task.



#We use the "title" keyword to indicate a new entry in the menu.



title 		Windows XP	#This is our first entry - it's number 0

find --set-root	/NTLDR  	#Search for NTLDR on all partitions. Once found, use that partition as root.

makeactive  			#Make this the active partition

chainloader /NTLDR		#Run NTLDR, the Windows XP bootloader

#If we're using a menu, we don't need to use the `boot` command - it's automatically implied.



#This is our second entry

title Ubuntu Linux
root (hd0,3) #Load Ubuntu from the 1st harddrive's 4th partition.
chainloader +1
#End Ubuntu entry

#That's it!


==================== sda3/ubuntu/disks/boot/grub/menu.lst: ====================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst



================================ sda3/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NOEXECUTE=OPTIN 
================================== sda3/boot: ==================================

total 4168
drwxrwxrwx 1 root root    8192 2009-01-07 15:41 .
drwxrwxrwx 1 root root   12288 2009-01-19 14:32 ..
-rwxrwxrwx 1 root root   28672 2009-01-19 14:34 BCD
-rwxrwxrwx 1 root root  262144 2008-12-10 14:34 BCD.Backup.0001
-rwxrwxrwx 1 root root  262144 2009-01-19 14:27 BCD.LOG
-rwxrwxrwx 2 root root       0 2008-02-03 16:06 BCD.LOG1
-rwxrwxrwx 2 root root       0 2008-02-03 16:06 BCD.LOG2
-rwxrwxrwx 1 root root    1024 2008-03-04 09:08 bootfix.bin
-rwxrwxrwx 1 root root 3170304 2008-03-04 09:08 boot.sdi
-rwxrwxrwx 1 root root   65536 2008-02-03 16:06 bootstat.dat
drwxrwxrwx 1 root root       0 2009-01-07 15:41 cs-CZ
drwxrwxrwx 1 root root       0 2009-01-07 15:41 da-DK
drwxrwxrwx 1 root root       0 2009-01-07 15:41 de-DE
drwxrwxrwx 1 root root       0 2009-01-07 15:41 el-GR
drwxrwxrwx 1 root root       0 2009-01-07 15:41 en-US
drwxrwxrwx 1 root root       0 2009-01-07 15:41 es-ES
-rwxrwxrwx 1 root root    2048 2008-03-04 15:05 etfsboot.com
drwxrwxrwx 1 root root       0 2009-01-07 15:41 fi-FI
drwxrwxrwx 1 root root    4096 2008-02-03 16:06 fonts
drwxrwxrwx 1 root root       0 2009-01-07 15:41 fr-FR
drwxrwxrwx 1 root root       0 2009-01-07 15:41 hu-HU
drwxrwxrwx 1 root root       0 2009-01-07 15:41 it-IT
drwxrwxrwx 1 root root       0 2009-01-07 15:41 ja-JP
drwxrwxrwx 1 root root       0 2009-01-07 15:41 ko-KR
-rwxrwxrwx 1 root root  405248 2008-10-17 22:30 memtest.exe
drwxrwxrwx 1 root root       0 2009-01-07 15:41 nb-NO
drwxrwxrwx 1 root root       0 2009-01-07 15:41 nl-NL
drwxrwxrwx 1 root root       0 2009-01-07 15:41 pl-PL
drwxrwxrwx 1 root root       0 2009-01-07 15:41 pt-BR
drwxrwxrwx 1 root root       0 2009-01-07 15:41 pt-PT
-rwxrwxrwx 1 root root   20480 2008-12-10 21:30 Recovery.bcd
-rwxrwxrwx 2 root root   17408 2008-12-10 21:30 Recovery.bcd.LOG
-rwxrwxrwx 2 root root       0 2008-12-10 21:30 Recovery.bcd.LOG1
-rwxrwxrwx 2 root root       0 2008-12-10 21:30 Recovery.bcd.LOG2
drwxrwxrwx 1 root root       0 2009-01-07 15:41 ru-RU
drwxrwxrwx 1 root root       0 2009-01-07 15:41 sv-SE
drwxrwxrwx 1 root root       0 2009-01-07 15:41 tr-TR
drwxrwxrwx 1 root root       0 2009-01-07 15:41 zh-CN
drwxrwxrwx 1 root root       0 2009-01-07 15:41 zh-HK
drwxrwxrwx 1 root root       0 2009-01-07 15:41 zh-TW

============================== sda3/ubuntu/disks: ==============================

total 14648448
drwxrwxrwx 1 root root           0 2008-12-13 00:03 .
drwxrwxrwx 1 root root        4096 2008-12-12 15:54 ..
drwxrwxrwx 1 root root        4096 2008-12-12 17:15 boot
-rwxrwxrwx 2 root root 14000000000 2009-01-16 14:29 root.disk
drwxrwxrwx 1 root root           0 2008-12-12 15:53 shared
-rwxrwxrwx 2 root root  1000000000 2008-12-12 17:10 swap.disk

=========================== sda3/ubuntu/disks/boot/: ===========================

total 13016
drwxrwxrwx 1 root root    4096 2008-12-12 17:15 .
drwxrwxrwx 1 root root       0 2008-12-13 00:03 ..
-rwxrwxrwx 1 root root  503560 2008-10-24 01:55 abi-2.6.27-7-generic
-rwxrwxrwx 1 root root   85316 2008-10-24 01:55 config-2.6.27-7-generic
drwxrwxrwx 1 root root       0 2008-12-12 17:15 grub
-rwxrwxrwx 1 root root 8901816 2008-12-12 17:15 initrd.img-2.6.27-7-generic
-rwxrwxrwx 1 root root  124152 2008-09-11 14:11 memtest86+.bin
-rwxrwxrwx 1 root root 1352144 2008-10-24 01:55 System.map-2.6.27-7-generic
-rwxrwxrwx 1 root root    1130 2008-10-24 01:57 vmcoreinfo-2.6.27-7-generic
-rwxrwxrwx 1 root root 2339712 2008-10-24 01:55 vmlinuz-2.6.27-7-generic

========================= sda3/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2008-12-12 17:15 .
drwxrwxrwx 1 root root 4096 2008-12-12 17:15 ..
-rwxrwxrwx 1 root root  191 2008-12-12 17:15 default
-rwxrwxrwx 1 root root   30 2008-12-12 17:15 device.map
-rwxrwxrwx 1 root root 5135 2008-12-15 18:24 menu.lst
-rwxrwxrwx 1 root root 4261 2008-12-12 17:15 menu.lst~

========================= sda3/ubuntu/disks/boot/grub: =========================

total 21
drwxrwxrwx 1 root root    0 2008-12-12 17:15 .
drwxrwxrwx 1 root root 4096 2008-12-12 17:15 ..
-rwxrwxrwx 1 root root  191 2008-12-12 17:15 default
-rwxrwxrwx 1 root root   30 2008-12-12 17:15 device.map
-rwxrwxrwx 1 root root 5135 2008-12-15 18:24 menu.lst
-rwxrwxrwx 1 root root 4261 2008-12-12 17:15 menu.lst~

================================== sda3/NST: ==================================

total 37
drwxrwxrwx 1 root root  4096 2009-01-04 00:00 .
drwxrwxrwx 1 root root 12288 2009-01-19 14:32 ..
-rwxrwxrwx 1 root root  1065 2008-12-25 13:28 menu.lst
-rwxrwxrwx 1 root root  1065 2008-12-25 13:27 menu.lst~
-rwxrwxrwx 1 root root  8192 2008-04-08 11:50 NeoGrub.mbr
-rwxrwxrwx 2 root root   512 2008-12-23 12:00 nst_grub-95E2F748A3EF60E57EA4359261E8637F.mbr
-rwxrwxrwx 1 root root   512 2008-12-15 00:56 nst_grub.mbr

=================== sda3: Location  of files loaded by Grub: ===================

  26.0GB: ubuntu/disks/boot/grub/menu.lst
  33.3GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
 234.5GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic

=========================== sda4/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows XP
root (hd0,0)
chainloader +1


title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1

=============================== sda4/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda4
UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda3
UUID=2C6EDB496EDB0B0A       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda2
UUID=94cd6bbb-4b8c-437e-abef-fb744053d906      none            swap        sw          0   0


================================== sda4/boot: ==================================

total 38232
drwxr-xr-x  3 root root    4096 2009-01-11 20:05 .
drwxr-xr-x 22 root root    4096 2009-01-11 22:03 ..
-rw-r--r--  1 root root  504280 2009-01-08 03:01 abi-2.6.27-11-generic
-rwxr-xr-x  1 root root  503560 2008-12-15 18:23 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 16:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85310 2009-01-08 03:01 config-2.6.27-11-generic
-rwxr-xr-x  1 root root   85316 2008-12-15 18:23 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 16:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-17 15:13 grub
-rw-r--r--  1 root root 8674428 2009-01-11 20:05 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8668699 2008-12-21 01:39 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8671708 2008-12-21 16:10 initrd.img-2.6.27-9-generic
-rwxr-xr-x  1 root root  124152 2008-12-15 18:23 memtest86+.bin
-rw-r--r--  1 root root 1354843 2009-01-08 03:01 System.map-2.6.27-11-generic
-rwxr-xr-x  1 root root 1352144 2008-12-15 18:23 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 16:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1131 2009-01-08 03:05 vmcoreinfo-2.6.27-11-generic
-rwxr-xr-x  1 root root    1130 2008-12-15 18:23 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 16:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2344000 2009-01-08 03:01 vmlinuz-2.6.27-11-generic
-rwxr-xr-x  1 root root 2339712 2008-12-15 18:23 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 16:30 vmlinuz-2.6.27-9-generic

=============================== sda4/boot/grub: ===============================

total 344
drwxr-xr-x 2 root root   4096 2009-01-17 15:13 .
drwxr-xr-x 3 root root   4096 2009-01-11 20:05 ..
-rwxr-xr-x 1 root root    191 2008-12-15 18:23 default
-rwxr-xr-x 1 root root     30 2008-12-15 18:23 device.map
-rwxr-xr-x 1 root root   8108 2008-12-15 18:24 e2fs_stage1_5
-rwxr-xr-x 1 root root   7856 2008-12-15 18:24 fat_stage1_5
-rwxr-xr-x 1 root root   8712 2008-12-15 18:24 jfs_stage1_5
-rwxr-xr-x 1 root root   4632 2009-01-17 15:13 menu.lst
-rw-r--r-- 1 root root   4427 2009-01-16 13:54 menu.lst~
-rwxr-xr-x 1 root root   7352 2008-12-15 18:24 minix_stage1_5
-rwxr-xr-x 1 root root   9756 2008-12-15 18:24 reiserfs_stage1_5
-rwxr-xr-x 1 root root    512 2008-12-15 18:24 stage1
-rwxr-xr-x 1 root root 121460 2008-12-15 18:24 stage2
-rwxr-xr-x 1 root root 121460 2008-12-15 18:24 stage2_eltorito
-rwxr-xr-x 1 root root   9556 2008-12-15 18:24 xfs_stage1_5

=================== sda4: Location  of files loaded by Grub: ===================

 270.0GB: boot/grub/menu.lst
 270.0GB: boot/grub/stage2
 270.0GB: boot/initrd.img-2.6.27-11-generic
 270.1GB: boot/initrd.img-2.6.27-7-generic
 270.1GB: boot/initrd.img-2.6.27-9-generic
 270.0GB: boot/vmlinuz-2.6.27-11-generic
 270.1GB: boot/vmlinuz-2.6.27-7-generic
 270.1GB: boot/vmlinuz-2.6.27-9-generic
 270.0GB: initrd.img
 270.1GB: initrd.img.old
 270.0GB: vmlinuz
 270.1GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by Jammanuser on 2009-01-21
Just recently I shrunk an NTFS partition to 100 **GBs** (yes...that's not a typo!;)) less in space, with BING, which took approx. 1 hour to complete...anyone know how long it would have taken Gparted to accomplish the same task? :) I did make sure to defrag first though, in case you're wondering...;)

That was to create that data partition I mentioned when I first started this thread, and I have now moved all my Vista and XP data files to that partition...and will likely move now my Ubuntu data over to it as well!

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-02-01
> **meierfra. said:**
> Sure. Edit /etc/fstab to mount your the Data partition to some folder. Then bookmark that folder  and it will appear in Places->Bookmarks. Or   add the folder to your top panel by dragging the folder to your top panel. It might also be possible to edit the Places menu and have it appear directly in  Places (but I don't know how to do that).

Ok...so now I need some help with editing fstab to mount my Data partition to a folder of my choosing. I'm assuming that I need to add another line to it, giving it the appropriate UUID address and mount point? 

Here's my fstab file:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda4
UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda3
UUID=2C6EDB496EDB0B0A       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda2
UUID=94cd6bbb-4b8c-437e-abef-fb744053d906      none            swap        sw          0   0

```

And here's my menu.lst:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows XP
root (hd0,0)
chainloader +1


title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1
```

And lastly, here's my latest RESULTS.txt (since my partition setup has been changed since my last one):

```
============================= Boot Info Summary: ==============================

 => BootIt NG is installed in the MBR of /dev/sda

Dell Utility 0: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BootIt: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

OS-2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /ubuntu.lnx is trying to chain 
                       load sector #276558975 on boot drive #1 BootPart in 
                       the file /NST/nst_grub.mbr is trying to chain load 
                       sector #506706165 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /bootmgr /boot/BCD 
                       /ntldr /ntdetect.com /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk

Ubuntu-real: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of 
                       Ubuntu-real and looks at sector 297317607 of the same 
                       hard drive for the stage2 file. A stage2 file is at 
                       this location on /dev/sda. Stage2 looks on partition 
                       #4 for /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

WinXP: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

Recovery: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

BootIT NG: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BootIt: Fat16
    Boot sector info:  According to the info in the boot sector, BootIT NG 
                       has 0 sectors.
    Operating System:  
    Boot files/dirs:   /DEFAULT.MNU /default.mnu

Extended: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

Extended_5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

Extended_6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, Extended_6 
                       starts at sector 63.
    Operating System:  
    Boot files/dirs:   

Extended_7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, Extended_7 
                       starts at sector 63.
    Operating System:  
    Boot files/dirs:   

Primary #Seven: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c5a8d58

Partition          Boot         Start           End          Size  Id System          Ind  ?
Dell Utility 0        -            63        80,324        80,262   6 FAT16             1  0
OS-2                  -    20,560,325   276,558,974   255,998,650   7 HPFS/NTFS         3  0
Ubuntu-real           -   276,558,975   317,508,659    40,949,685  83 Linux             4  0
WinXP                 -   552,009,465   613,442,024    61,432,560   c W95 FAT32 (LBA) 151 20
Recovery              -        80,325    20,547,134    20,466,810   7 HPFS/NTFS        29 20
BootIT NG             -   613,442,025   613,458,089        16,065  df BootIt          180 60
Extended              -   317,508,660   552,009,464   234,500,805   f W95 Ext d (LBA) 198 20
Extended_5                317,508,723   326,713,904     9,205,182  82 Linux swap / Solaris       
Extended_6                326,713,968   449,595,089   122,881,122   7 HPFS/NTFS             
Extended_7                449,595,153   552,009,464   102,414,312   7 HPFS/NTFS             
Primary #Seven        -   613,458,090   625,137,344    11,679,255   7 HPFS/NTFS       167 20


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="WINXP-OS" UUID="5BE6-0200" TYPE="vfat" 
/dev/sda2: UUID="2C6EDB496EDB0B0A" LABEL="OS" TYPE="ntfs" 
/dev/sda4: LABEL="Ubuntu-real" UUID="dd4f326a-2165-40f6-aed4-2b44b15b71a5" TYPE="ext3" 
/dev/sda6: UUID="162839AD28398D2D" LABEL="DATA" TYPE="ntfs" 
/dev/sda7: UUID="786CF89A6CF853FA" LABEL="Programs" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda2 on /media/drv0 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gorilla/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gorilla)

============================== OS-2/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD



#This is a comment. Comments are prefixed with a '#'



default 0		#Pick the task to be run if the user doesn't pick one within the time limit.

timeout 10		#Give the user 10 seconds to choose a task.



#We use the "title" keyword to indicate a new entry in the menu.



title 		Windows XP	#This is our first entry - it's number 0

find --set-root	/NTLDR  	#Search for NTLDR on all partitions. Once found, use that partition as root.

makeactive  			#Make this the active partition

chainloader /NTLDR		#Run NTLDR, the Windows XP bootloader

#If we're using a menu, we don't need to use the `boot` command - it's automatically implied.



#This is our second entry

title Ubuntu Linux
root (hd0,3) #Load Ubuntu from the 1st harddrive's 4th partition.
chainloader +1
#End Ubuntu entry

#That's it!


==================== OS-2/ubuntu/disks/boot/grub/menu.lst: ====================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst



======================== OS-2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ OS-2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NOEXECUTE=OPTIN 



C:\ubuntu.lnx="Ubuntu Linux"


=================== OS-2: Location of files loaded by Grub: ===================


  26.0GB: ubuntu/disks/boot/grub/menu.lst
  33.3GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
  67.9GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic

======================= Ubuntu-real/boot/grub/menu.lst: =======================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows XP
root (hd0,0)
chainloader +1


title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1

============================ Ubuntu-real/etc/fstab: ============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda4
UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda3
UUID=2C6EDB496EDB0B0A       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda2
UUID=94cd6bbb-4b8c-437e-abef-fb744053d906      none            swap        sw          0   0


================ Ubuntu-real: Location of files loaded by Grub: ================


 152.2GB: boot/grub/menu.lst
 152.2GB: boot/grub/stage2
 152.2GB: boot/initrd.img-2.6.27-11-generic
 152.3GB: boot/initrd.img-2.6.27-7-generic
 152.3GB: boot/initrd.img-2.6.27-9-generic
 152.2GB: boot/vmlinuz-2.6.27-11-generic
 152.3GB: boot/vmlinuz-2.6.27-7-generic
 152.3GB: boot/vmlinuz-2.6.27-9-generic
 152.2GB: initrd.img
 152.3GB: initrd.img.old
 152.2GB: vmlinuz
 152.3GB: vmlinuz.old

=============================== WinXP/boot.ini: ===============================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn



=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1043: [: =: unary operator expected
```

---

### Post by meierfra. on 2009-02-01
Create a folder for your Data partition:

```
sudo mkdir /media/NameOfYourChoosing 
```


and add this to your fstab:

```
#/dev/sda6
UUID=162839AD28398D2D   /media/NameOfYourChoosing    ntfs-3g   defaults      0    0  
```

---

### Post by Jammanuser on 2009-02-01
Alright...thanks Meierfra! :D **Much** appreciation! :p

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-02-02
Thanks again. :) That worked! :D
My DATA partition is now easily accessible from the top panel of the screen...I only wish there was a way to make my username folder inside the Home folder appear in my Places menu. :(

If anyone has an answer for this, then please let me know!

-Jam man

:guitar:

---

