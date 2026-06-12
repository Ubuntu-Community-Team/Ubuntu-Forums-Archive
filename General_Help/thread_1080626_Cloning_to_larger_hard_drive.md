---
title: "Cloning to larger hard drive"
date: 2009-02-25
forum: General Help
---

### Post by luke0927 on 2009-02-25
Hello...When i installed  ubuntu i just had and old 20gb HD and used it to install  ubuntu as a secondary drive.  Since i like it so much and its all ive used for the last couple months i need to expand to a larger drive...i do not want to start all over....what is the best open source program to do this...i have read about clonezilla and have downloaded the live CD but have not used it yet.  Im assuming if i clone it to a larger drive it will basically just be using a 20gb partion out of that drive...what will i do then to expand my file system so i can keep on adding to my desktop...Is this the best way to go about this?

any good ideas 

Thanks!

---

### Post by HermanAB on 2009-02-25
It is so easy to install Ubuntu, that I sure won't bother to copy the drive.  However, you could use dd (or clonezilla - same thing) to copy the drive and then run a partitioning tool to grow the partition over the whole drive, or you can simply install two drives - the old and the new.

Cheers,

Herman

---

### Post by pdwerryhouse on 2009-02-25
You could possibly just use dd to copy on drive to the other (though occasionally the boot loader might not work, so you might still need to boot from a CD to reinstall the bootloader).

If you've created your partitions with LVM, then you can then grow the volume group, and then grow the logical volumes after that.

---

### Post by pdwerryhouse on 2009-02-25
> **HermanAB said:**
> It is so easy to install Ubuntu, that I sure won't bother to copy the drive. 

That depends; often people have made a lot of configuration changes and it's much easier to copy it across. When I get my new laptop, I will most likely copy my existing one.

---

### Post by luke0927 on 2009-02-25
Reinstalling ubuntu is the easy part its reinstalling all the apps and then bringing the data over...when i setup ubuntu i just told it to use the entire disk so i have an ext3 FS around 18Gb then there is an extended and linux swap space...all i would need to expand would be my ext FS right?  would i need to make the extended and swap space larger if I increase my main FS size or are they always the same size. does ubuntu 8.10 support online resizing?

---

### Post by pdwerryhouse on 2009-03-02
You only need to increase the size of your swap space if you feel that the existing swap is too small for the amount of memory you're likely to be using.

You don't even have to have a swap partition at all, though there are plenty of demonstrations that show that the OS will perform better if you have one.

---

### Post by Odd_sam on 2009-03-02
I performed this very same operation to my ubuntu installation a few weeks ago. This is an article I used.

[quote=http://www.linux.com/feature/152592]Just upgraded your system with a shiny new hard disk and want to make it your new book disk? Cloning Ubuntu to another hard disk is easy. In fact, Ubuntu provides tools to clone the entire hard disk -- including the Windows partition, if there's one on there. This is the kind of fundamental task that Linux excels at, in fact.

This article is excerpted from the newly published book Ubuntu Kung Fu and published with the express permission of the publisher, the Pragmatic Programmers, LLC.

Three things must be done. First, you must discover how Ubuntu refers to the hard disks. Second, you must install ddrescue and then use it to clone the disk. Third, once ddrescue has finished, you must use the Gparted utility to expand the disk partition(s) (assuming that the new disk is bigger than the old one, which is almost certainly going to be the reason for upgrading in the first place).

It's not a good idea to clone a hard disk that's in use (any more than it's a good idea to repair a car while it's being driven), so you must use your Ubuntu install CD's live distro mode. To carry out the following instructions, boot from your Ubuntu install CD, and select Try Ubuntu from the boot menu.

Note that all the following stages are carried out using the Ubuntu install CD's live distro mode. At no point in the process do you need to boot into your standard Ubuntu installation, apart from to test the cloned disk at the end.
Preparing to clone

Before starting, it's a good idea to do three things in preparation. First, back up all valuable personal files to CD/DVD-R/RW disc, a USB keystick, or an external hard disk. The instructions that follow involve drastic fundamental disk management and the possibility of data loss.

Second, it's a good idea to check the filesystem of the original hard disk for errors and possibly enact repairs. Ideally, you should check the Windows filesystem for errors too.

Third, remove any USB memory sticks, card readers, or other kinds of attachable storage, such as MP3 players or mobile phones. This will avoid confusion when partitioning.

After all this, open a terminal window, and type the command sudo fdisk -l, which will scan the hard disks and list their partitions. Here are the results from my test system:

Disk /dev/sda: 81.9 GB, 81964302336 bytes 255 heads, 63 sectors/track, 9964 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x1c381c37 Device Boot Start End Blocks Id System /dev/sda1 * 1 4742 38090083+ 7 HPFS/NTFS /dev/sda2 4743 9964 41945715 5 Extended /dev/sda5 4743 9744 40178533+ 83 Linux /dev/sda6 9745 9964 1767118+ 82 Linux swap/Solaris Disk /dev/sdb: 120.0 GB, 120034123776 bytes 255 heads, 63 sectors/track, 14593 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0xb94838a4 Disk /dev/sdb doesn't contain a valid partition table

Two hard disks are listed in the results: look for the headings Disk /dev/sda and Disk /dev/sdb. Beneath each heading is technical information about the disk, and beneath that the partitions on that disk are listed.

It should be obvious that, on my test computer, /dev/sdb is the new hard disk because it has no partitions (it "doesn't contain a valid partition table"), while /dev/sda has the standard partition layout of an Ubuntu system. Yours will probably be similar, if not identical.

Look for the reference to your new hard disk and make a note of it. In my case, I make a note of /dev/sdb. Then type sudo cfdisk -z /dev/sdb to start the cfdisk partitioning program, which we'll use to write an initial partition table to the disk. If necessary, replace /dev/sdb with the details of the new hard disk you discovered earlier. When cfdisk starts, type W (note that's Shift+w) and then type yes to write a blank partition table. Then press q to quit cfdisk. You can ignore the handful of minor errors that are reported.
Cloning the disk

Now that we have this information, we can install ddrescue and use it to clone the disk. This needs to be installed because it isn't a default system tool. Although the computer is running the Ubuntu install CD live distro mode, it's still possible to install additional software from the online repositories. However, before doing this, it's necessary to enable the Universe software repository (of course, you will need to use NetworkManager to get online too, if you haven't already). Click System -> Administration -> Software Sources, and put a check in the box alongside Community-maintained Open Source software (universe). Then click the Close button, and agree to refresh the list of software when asked.

After this, type sudo apt-get install gddrescue at the prompt to install ddrescue.

Use ddrescue by first specifying the old hard disk, then the new hard disk. Add the -v command option to provide a status report as the command progresses:

$ sudo ddrescue -v /dev/sda /dev/sdb

It's extremely important that you ensure you get the old and new disks in the right order. Otherwise, you might well overwrite the data on your old disk!

Once the cloning has finished -- it will probably take an hour or more, depending on the size of the original hard disk -- you should shut down the computer, remove the old disk (you must disconnect the old disk before you can continue!), and boot from the cloned copy to test things. If you use Windows XP/Vista, it might object to a new hard disk as part of its Windows Genuine Advantage system, and you might have to revalidate online. Of course, Ubuntu will work fine without any such worries.

Assuming everything works correctly, you can move on to the next step: expanding the partitions to take advantage of the larger hard disk.
Expanding the partitions

Before attempting to expand the partitions, it's a good idea to check that your Ubuntu partition's filesystem is sound. To do this, boot into the Ubuntu install CD's live distro mode as before. Open a terminal window and type the command sudo fsck.ext3 -f /dev/sda5 to perform a disk check (assuming that Ubuntu is installed alongside Windows on your hard disk in the standard configuration).

Once this has completed, close the terminal window and click System -> Administration -> Partition Editor. What happens next depends on your requirements. If you just want to expand the Ubuntu partition, follow these steps:

   1. In the Partition list, right-click the linux-swap entry and select Swap off. This will stop Ubuntu's live distro mode from accessing the swap partition so that it can be moved on the hard disk.
   2. Before anything else can happen, you must resize the extended partition that contains Ubuntu. Right-click the extended entry in the list and select Resize/Move. In the dialog box that appears, change the Free Space Following (MiB) box to read 0, then press Tab. This will cause the partition to be expanded to fill the space. Click the Resize/Move button when done. Bear in mind that no changes are carried until you click the Apply button, which you will do after making all the changes to the disk's partitions.
   3. Right-click the linux-swap partition once again, and select Resize/Move. In the dialog box that appears, click and drag the graphical representation of the partition to the end of the free space (in other words, click and drag it to the right of the graphical display). After this, the Free Space Following (MiB) box should read 0. Click Resize/Move.
   4. Back in the main GParted program window, right-click the ext3 entry in the list, and select Resize/Move. Click and drag the rightmost edge of the partition in the graphical representation so that it "grows" to fill the free space. Eventually the Free Space Following (MiB) box will read 0. When this is the case, click the Resize/Move button.
   5. Finally, click the Apply button on the main GParted toolbar. Then click Apply in the dialog box that appears, and sit back and wait while the partitions are moved and resized. If you want to see what's happening, click the small arrow alongside Details in the Applying pending operations dialog box.
   6. When GParted has finished, close the program, then open a terminal window. Enter sudo fsck.ext3 -f /dev/sda5, which will once again check the Ubuntu partition for errors (and, again, these steps assume that Ubuntu is installed alongside Windows on your hard disk in the standard configuration). If there are any errors, you'll be prompted to repair them. Usually you can agree to the repair.

After the filesystem check, you can reboot your computer from the new hard disk. You should find the Ubuntu partition is now larger.

If you want to resize your Windows partition too, these steps are still relevant. However, you will have to move the swap and ext3 partitions, as well as the extended partition containing them, before resizing the NTFS partition.

If you want to dispose of the old hard disk or pass it on to somebody else, be sure to securely wipe it. However, don't do so until you're 100% sure your new cloned copy is working correctly. I usually wait at least a week or two to ensure the copy works fine before doing anything to the old disk.[/quote]

[http://ubuntuforums.org/showthread.php?t=1067433](http://ubuntuforums.org/showthread.php?t=1067433)

**Read this whole section before performing the codes listed**
Short version:
*note assuming sda is your ubuntu drive and sdb is your empty drive

install gddrescue
```
sudo apt-get install gddrescue
```

reformat sdb
```
sudo cfdisk -z /dev/sdb
```
type "W" (Shift+w) then "yes" (y+e+s) then "q" (q).

Copy sda to sdb
```
sudo ddrescue -v /dev/sda /dev/sdb
```

once this is complete you will have a perfect clone of your ubuntu installation on a second hard drive. you will need to install gparted or use the live cd to resize your partitions to fill up the new hard drive. You also may need to delete your windows partition from the second hdd.

---

### Post by luke0927 on 2009-03-04
Thanks!

---

### Post by Al Fischer on 2009-03-16
I have been using a GPARTED live cd and it works like a charm. Put new drive in system, reboot with GPARTED and do a copy/paste of the partition to the new drive. Check UUID and FSTAB afterwards but it should be fine.

I have done this with Ubunto, Windows XP and DOS. Works.

---

### Post by workshop1702 on 2009-03-28
hi is it possible to clone a hard drive to a smaller hard drive i have a 160g hard drive which i want to clone to a 120g hard drive . 
the 160g is nowhere near full, the info will easily fit on the 120g but will i have any probs with partitions or anything else doing this.

---

### Post by Odd_sam on 2009-04-26
> **workshop1702 said:**
> hi is it possible to clone a hard drive to a smaller hard drive i have a 160g hard drive which i want to clone to a 120g hard drive . 
the 160g is nowhere near full, the info will easily fit on the 120g but will i have any probs with partitions or anything else doing this.

Not sure if you still need help but the method I posted above will work you just need to make a few modifications. Just a few things to remember will be that you can't put 160 Gigs of memory into 120 gigs. So you should shrink your partition size of your 160 to be as small as possible (but as long as you are below lets say 100 gigs to be safe you should be fine) before you do any of the steps above. The other thing to remember is check your drive names are sda and sdb where sda is the drive you want to copy and sdb is the drive you want to move the copy to.

If this didn't work or someone else has questions about this method send me a pm, email, im. you will get a faster response than posting here.

---

### Post by Versusnja on 2010-01-09
Isn't it right that GParted can clone HDD itself? Simply copy/paste? Right from Ubuntu Live CD?

Why to use dd or ddrescue if GParted can do this easily?

---

### Post by john newbuntu on 2010-01-09
If you copy those 446 bytes of MBR using dd, perform e2fsck, chkdisk and change UUIDs, you should be good to go in theory.

---

