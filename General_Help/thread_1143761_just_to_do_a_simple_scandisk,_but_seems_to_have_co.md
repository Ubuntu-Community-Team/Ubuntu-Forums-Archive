---
title: "just to do a simple scandisk, but seems to have corrupted the file system"
date: 2009-04-30
forum: General Help
---

### Post by liketofindoutwhy on 2009-04-30
I have Ubuntu 9.04 and just wanted to do a simple scandisk, so searching on the internet says fsck is the tool to use on the command line.

so i tried using fsck, and it almost returned immediately.  so i used "man fsck" and found that "fsck -A" can check all file system...

so i ran it.  there is a note saying that  e2fsck can severely damage a file system if the disk is mounted.  so i thought, since i am running fsck but not e2fsck, that's ok.  later on, i think the message actually might have meant "e2fsck or fsck can severely damage the file system if the disk is mounted."  is that true?

so i ran it, and it suggested quite a bit of corrections.  i just accepted them.  and press ENTER continuously to accept all of them.   later on, when i reboot the system, it immediately said the GRUB file has an error.  Error code 15.  and it won't boot anything.

so is the Ubuntu file system damaged?  Is the Vista file system also damaged?

To try to fix the GRUB problem, i reinstalled Ubuntu.  After that, the newer installation of Ubuntu can boot, but the old one disappeared from the boot manual.  Is my Vista file system also damaged?  Is there is way to get back the earlier Ubuntu installation?  It was installed with a 30GB partition.

Is it true that the disk needs to be unmounted before fsck is run?  Maybe we can have a simple too that's like XP or Vista, that it will simple set a fsck next time it boots up Ubuntu, so that it is easier and won't so easily damage the file system for the general users?

---

### Post by sdennie on 2009-04-30
> **liketofindoutwhy said:**
> 
so is the Ubuntu file system damaged?


Yes.  fsck picks the appropriate flavor of fsck (in this case e2fsck) and runs that.  Running that on a mounted ext partition is likely to break it.

> 
Is the Vista file system also damaged?


Was it mounted?  Is it FAT or NTFS?  There is no fsck.ntfs so, it wouldn't have touched the Vista partition if it's mounted as NTFS.  It should be fine.

> 
To try to fix the GRUB problem, i reinstalled Ubuntu.  After that, the newer installation of Ubuntu can boot, but the old one disappeared from the boot manual.  Is my Vista file system also damaged?  Is there is way to get back the earlier Ubuntu installation?  It was installed with a 30GB partition.


You probably won't be able to recover it.  You could try unmounting the partition from your new installation and running fsck on it.  For example, if the old partition was /dev/sda2:

```

fsck -f /dev/sda2

```

> 
Is it true that the disk needs to be unmounted before fsck is run?  Maybe we can have a simple too that's like XP or Vista, that it will simple set a fsck next time it boots up Ubuntu, so that it is easier and won't so easily damage the file system for the general users?

Yes, the partition should always be unmounted first.  Also, Ubuntu already has what you are suggesting.  Try: 

```

sudo touch /forcefsck

```

Then reboot.

---

### Post by tytso on 2009-04-30
It's true; it's not safe to run fsck while the system is mounted.  Fsck is a front-end program which runs fsck.ext3 (or more generally, fsck.<filesystem type>, where <filesystem type> is ext3 if you are using an ext3 filesystem, ext4 if you are using an ext4 filesystem, xfs if you are using an xfs filesystem, and so on).   The ext2, ext3, and ext4 filesystems all use e2fsck, so fsck.ext[234] are a link to /sbin/e2fsck.

When you ran fsck -A, it would have printed a fairly explicit message:

# fsck -A
fsck 1.41.5 (23-Apr-2009)
e2fsck 1.41.5 (23-Apr-2009)
/dev/mapper/ssd-root is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? 

As you can see, the first line indicates the version number of fsck; then after fsck runs fsck.ext3 (which is a symlink to e2fsck), e2fsck prints the second line, which indicates the version of e2fsck.   E2fsck then displays a fairly explicit WARNING.   Even if you thought you were running fsck, and didn't understand about e2fsck, perhaps there was a really good reason why the program asked "Do you really want to continue"?!?

Note that it's actually pretty rare that unlike Windows, an unclean shutdown with ext3 doesn't require running a scandisk like program.   The init scripts take care of this automatically, and modern Linux filesystems, which include ext3, ext4, jfs, and xfs, all use a technique called journalling to prevent filesystem corruption due to unclean shutdowns.   And the boot-up scripts automatically check to see if the filesystem needs checking, and will take care of running the filesystem checker if it is necessary.

In fact, most people usually complain about it running because to fsck the filesystem.   And because we're paranoid (and PC-class computers are generally optimized for being cheap rather than high quality --- at least compared to data-center grade enterprise equipment --- Ted's Law of PC-class computers: "They're sh*t"), ext3 will perform a forced fsck every 25-30 bootups.  If you want to force a filesystem check on the next reboot, the following command (substitute /dev/hdXXX with the device name of your root filesystem) will do the trick:

 tune2fs -C 16000 -T 19000101 /dev/hdXXX

For really advanced Linux system administrators, there is a safe way to run fsck while the system is booted, but it requires that you use LVM, or the Logical Volume Manager.  This isn't installed by default by Ubuntu (a design decision think is unfortunate, because LVM is very useful and powerful); to use LVM, you have to use the "Alternate" installer disk, which is a bit more complicated than the user-friendly installer intended for the novice user.

If you are a more advanced user, then use the "Alternate" installer, and install your system with a logical volume manager, but when you create the logical volume for your root filesystem, *don't* make it completely fill your hard drive.  Leave a little bit of extra space for the snapshot volume.

Then you can use a shell script like this, either run out of cron, or manually.   If this you don't understand what's going on with the script, then you probably just want to stick to the default installer and simply don't worry and be happy.  Most of the time you don't need to do anything special with respect to fsck.  Unfortunately, I think you "knew just enough to be dangerous", and then after googling turned up some advice that wasn't very comprehensive, blindly ignored the safety warnings that had been placed to try to protect users from themselves.

The e2croncheck script can be found here:

[ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/e2croncheck](ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/e2croncheck)

---

### Post by liketofindoutwhy on 2009-04-30
> **tytso said:**
> It's true; it's not safe to run fsck while the system is mounted.  Fsck is a front-end program which runs fsck.ext3 (or more generally, fsck.<filesystem type>, where <filesystem type> is ext3 if you are using an ext3 filesystem, ext4 if you are using an ext4 filesystem, xfs if you are using an xfs filesystem, and so on).   The ext2, ext3, and ext4 filesystems all use e2fsck, so fsck.ext[234] are a link to /sbin/e2fsck.

When you ran fsck -A, it would have printed a fairly explicit message:

# fsck -A
fsck 1.41.5 (23-Apr-2009)
e2fsck 1.41.5 (23-Apr-2009)
/dev/mapper/ssd-root is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? 

As you can see, the first line indicates the version number of fsck; then after fsck runs fsck.ext3 (which is a symlink to e2fsck), e2fsck prints the second line, which indicates the version of e2fsck.   E2fsck then displays a fairly explicit WARNING.


i think there are a few things here:
it says running e2fsck will damage a mounted filesystem will damage it.  the fact is, the user didn't type is e2fsck.  the user typed in fsck.   how is the general user supposed to know fsck is in fact, the same as e2fsck?   A portion of the user may think that they are running fsck so therefore the e2fsck warning doesn't apply.

second, it says 
/dev/mapper/ssd-root is mounted.  
does that mean it is the current fileystem we are checking?  Why doesn't the statement say exactly:  You are doing fsck on a mounted filesystem.  Doing so may severely damage the filesystem.  Isn't that more clear?

As the 95% of Windows and Mac users out there, they don't know what a mounted filesystem means.  And they don't know what the dev/mapper/ssd-root means.   They are more familiar with the C: and D:, and the Mac hard drive icon.

Also,  could the warning include a statement to say how to unmount the filesystem first?  And if it unmounts the filesystem, does that mean you cannot even shut down the computer afterwards?  Do you need to unmount, run fsck, and mount it again before you reboot?   Or, why not just print a statement saying the safest way to do fsck is to do the

sudo touch /forcefsck
and then reboot ubuntu

and that will be the safest for the general users?

and if fsck (e2fsck also) knows that it is about to scan a mounted filesystem and likely to damage it, why does it go on at all?  you mention LVM won't let it happen, and that LVM is for the advanced users.  so the general users are just left out there, fsck will go ahead and damage their filesystem anyway?

and i think something so destructive as damaging your filesystem, at least you need to ask the user twice, or tell the user to use  fsck --forcecheck  if absolutely needed.  the reason is that many users they used  sudo apt-get install ruby, apt-get install apache2, apt-get install php5, and they are so used to just hitting ENTER to accept the default behavior or replying "Y" for yes.  So before fsck destroys a filesystem, it gives a similar UI to the user, isn't that rather dangerous UI before damaging the filesystem?

ordering a book twice on the web, at least it is not so irreversible.  deleting a file, it may not be reversible, but at least the damage may be limited to that one file.  Damaging the whole filesystem -- that is pretty irreversable and a pretty big damage.  The UI and the message can be made better in situations like this.

---

### Post by sdennie on 2009-04-30
> **liketofindoutwhy said:**
> i think there are a few things here:
it says running e2fsck will damage a mounted filesystem will damage it.  the fact is, the user didn't type is e2fsck.  the user typed in fsck.   how is the general user supposed to know fsck is in fact, the same as e2fsck?   A portion of the user may think that thye are running fsck so therefore the e2fsck warning doesn't apply.


I'm an experienced user and if I see "WARNING!!!", "SEVERE" and "damage" with a prompt to continue, unless I know exactly what I'm doing, I say "n".  It doesn't matter if the message is: "WARNING!!!  Running e2fsck while in the presence of a Tyrannosaurus Rex may cause SEVERE filesystem damage.  Continue (y/n)"  You click "n" anyway.  Just in case...

---

### Post by liketofindoutwhy on 2009-04-30
> **sdennie said:**
> 


Was it mounted?  Is it FAT or NTFS?  There is no fsck.ntfs so, it wouldn't have touched the Vista partition if it's mounted as NTFS.  It should be fine.



yes, my Vista is on NTFS, so fsck didn't damage it huh?  and i think it wasn't mounted either.  I was running Ubuntu 9.04 on a separate partition when installing... hm...  but the Vista file could be visible to me (although I forgot whether I actually open the drive folder at that time).

So is that true?  if running Ubuntu on a separate partition, the Vista filesystem could be mounted or could be not mounted, and since it is NTFS, it is not damaged.

And if you install Ubuntu to "run inside Vista" -- i tried that on a different computer and there, i can't find the Vista partition and files at all.  So is it true in that case, the vista filesystem is not mounted? (and can never be).   If I boot Vista in that case, I do see a c:\ubuntu folder and in there, there is a 5.8GB virtual hard drive image, and I think those contain the Ubuntu files.  So in that case, Ubuntu won't be running as fast, since it is working from a virtual hard drive instead of a real physical one?  thanks.

---

### Post by liketofindoutwhy on 2009-04-30
> **sdennie said:**
> 


You probably won't be able to recover it.  You could try unmounting the partition from your new installation and running fsck on it.  For example, if the old partition was /dev/sda2:

```

fsck -f /dev/sda2

```

how do i find out the number for that filesystem?  ( /dev/sda_ )
in my Computer folder, i do see a 33GB media, and that should be my 30GB partition of the first Ubuntu install.  if i right click on it, it says "Mount" at the bottom of the list.  So by default it is not mounted?  How do i find out whether it is sda6 or sda5?

So i can fsck it to try to fix it... and then i use

gksudo gedit /boot/grub/menu.lst

to list that filesystem back to the boot menu?  (copy and paste the current ubuntu boot lines and change the sda7 to whatever that filesystem is?)

and if that filesystem cannot be fixed, is there a way to reinstall ubuntu on that partition?  or use Vista's partition manager to reclaim that partition space?  thanks.

---

### Post by sdennie on 2009-04-30
> **liketofindoutwhy said:**
> how do i find out the number for that filesystem?  ( /dev/sda_ )
in my Computer folder, i do see a 33GB media, and that should be my 30GB partition of the first Ubuntu install.  if i right click on it, it says "Mount" at the bottom of the list.  So by default it is not mounted?  How do i find out whether it is sda6 or sda5?


It's probably not mounted by default.  To find out what disk it us, use:

```

sudo fdisk -l

```

> 
So i can fsck it to try to fix it... and then i use

gksudo gedit /boot/grub/menu.lst

to list that filesystem back to the boot menu?  (copy and paste the current ubuntu boot lines and change the sda7 to whatever that filesystem is?)


That probably won't work.  However, it's highly likely that you won't get to the stage of needed to edit /boot/grub/menu.lst because the fsck won't be able to fix the filesystem.  If it can, I would start another thread asking  how to edit menu.lst or google for it.

> 
and if that filesystem cannot be fixed, is there a way to reinstall ubuntu on that partition?  or use Vista's partition manager to reclaim that partition space?  thanks.

Yes, you will have no problem re-installing Ubuntu on it at all.  It creates a new filesystem on the disk at installation time.

---

### Post by liketofindoutwhy on 2009-04-30
> **sdennie said:**
> 
 it's highly likely that you won't get to the stage of needed to edit /boot/grub/menu.lst because the fsck won't be able to fix the filesystem.  If it can, I would start another thread asking  how to edit menu.lst or google for it.

Yes, you will have no problem re-installing Ubuntu on it at all.  It creates a new filesystem on the disk at installation time.

so i just put the Ubuntu 9.04 CD in, re-install, and instead of choosing new partition to be used (resized from Vista's partition), just choose the third option to use an existing partition?  

what if i just have some files in that old Ubuntu installation, and i want to get it back.  Can i fsck it, mount it, and be able to try to get those files back?  thanks.

---

### Post by sdennie on 2009-04-30
> **liketofindoutwhy said:**
> so i just put the Ubuntu 9.04 CD in, re-install, and instead of choosing new partition to be used (resized from Vista's partition), just choose the third option to use an existing partition?

Yes

> 
what if i just have some files in that old Ubuntu installation, and i want to get it back.  Can i fsck it, mount it, and be able to try to get those files back?  thanks.

The only way to know is to try.  :)

---

### Post by liketofindoutwhy on 2009-04-30
so i ran the following.  does it look like they are good?  it didn't even try to fix anything.  the line  sudo fsck -f /dev/sda5  was able to be finished in 2 minutes or so.

can i now mount it and try to relocate the useful files, or can i simply try to make it into bootable again? 

i think when i was doing fsck -A on the current filesystem, it wasn't running any app at all (besides a shell and firefox that is idle).  so maybe the damage was minimal?


```

astro@studio:~$ sudo fdisk -l
[sudo] password for astro: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3fd54c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1280    10240000    7  HPFS/NTFS
/dev/sda3   *        1280       32515   250894856    7  HPFS/NTFS
/dev/sda4           32516       38913    51391935    5  Extended
/dev/sda5           34612       38730    33085836   83  Linux
/dev/sda6           38731       38913     1469916   82  Linux swap / Solaris
/dev/sda7           32516       34517    16081002   83  Linux
/dev/sda8           34518       34611      755023+  82  Linux swap / Solaris

Partition table entries are not in disk order


astro@studio:~$ sudo fsck /dev/sda5
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda5: clean, 118225/2068528 files, 796221/8271459 blocks


astro@studio:~$ sudo fsck -f /dev/sda5
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 118225/2068528 files (0.6% non-contiguous), 796221/8271459 blocks


astro@studio:~$ sudo fsck -f /dev/sda6
fsck 1.41.4 (27-Jan-2009)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda6
astro@studio:~$ 

```

---

### Post by liketofindoutwhy on 2009-04-30
actually, right now if i use File Browser to mount the 33GB media, all is showing inside is "Lost+Found"

if i unmount it there and mount it at the shell, i get:

astro@studio:~$ sudo mount /dev/sda5
mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab

---

### Post by sdennie on 2009-04-30
If all it shows is lost+found it means that your data has been corrupted.  My guess is if you look inside lost+found you'll see a lot of numbered files that represent what used to exist on the partition.

---

### Post by liketofindoutwhy on 2009-04-30
> **sdennie said:**
> If all it shows is lost+found it means that your data has been corrupted.  My guess is if you look inside lost+found you'll see a lot of numbered files that represent what used to exist on the partition.

the first time i click on it, it simply tries to open the folder and the mouse cursor keep on being the turning wheel and it never open anything.

now i try again and it says i don't have permission to open it, and the turning wheel keep on spinning again.

---

### Post by liketofindoutwhy on 2009-04-30
> **tytso said:**
> 
 If you want to force a filesystem check on the next reboot, the following command (substitute /dev/hdXXX with the device name of your root filesystem) will do the trick:

 tune2fs -C 16000 -T 19000101 /dev/hdXXX
[U]
[/U]

so this is better than 

sudo touch /forcefsck

?

what if you type 19000101 wrong and typed 1900101 instead?  or 160000 instead of 16000?  will it destroy your whole ubuntu partition unless you are advanced user and set something up earlier?

---

### Post by liketofindoutwhy on 2009-04-30
> **tytso said:**
> 

When you ran fsck -A, it would have printed a fairly explicit message:

# fsck -A
fsck 1.41.5 (23-Apr-2009)
e2fsck 1.41.5 (23-Apr-2009)
/dev/mapper/ssd-root is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? 

As you can see, the first line indicates the version number of fsck; then after fsck runs fsck.ext3 (which is a symlink to e2fsck), e2fsck prints the second line, which indicates the version of e2fsck.   E2fsck then displays a fairly explicit WARNING.   Even if you thought you were running fsck, and didn't understand about e2fsck, perhaps there was a really good reason why the program asked "Do you really want to continue"?!?


I can see that it prints out a warning message.  BUT HOW CAN I SEE that "then after fsck runs fsck.ext3 (which is a symlink to e2fsck), e2fsck prints the second line" ??  you can see that because you are a programmer of fsck.  How can the GENERAL USER KNOW?  some users may think ok, fsck and e2fsck are tools of the same family, and e2fsck is dangerous and I am using fsck and that's ok, and that's why the program asked me if I'd like to continue at all.

Is there such possibility?  If yes, if 10% of users may think so or even 3% or 1% of users may think so, you are destroying their partition by providing a not so clear message right there.

---

