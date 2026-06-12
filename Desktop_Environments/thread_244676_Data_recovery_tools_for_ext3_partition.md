---
title: "Data recovery tools for ext3 partition?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by rabidwalrus on 2006-08-26
Hello, I just wondered if anybody knew of any tools that I could use to recover data from a deleted ext3 partiton? (I deleted it, but I haven't created any partiton over it yet). I tried googling but I didn't find anything that suited my needs. Anything that you can suggest would be greatly appreciated, but I'll have to use something that is available for linux and is free. Thanks in advance!

---

### Post by az on 2006-08-26
Well, you can use parted to "rescue" the partition.  Boot the live cd and run parted.  If you remember whereabouts the partition was, you can type in aproximate parameters.  If not, you can just start from zero and work the whole drive.

sudo parted /dev/hda

and whitin parted you would do 

rescue
0
10000

and if it find it, it will ask you if you want to add it to the partition table.

All your data is still there.


As well, you can use foremost to recover lost files.

Again, I recommend the live cd and getting the version from upstream, as the version of foremost in the repos is old and less user friendly.

You will have to make sure that you have a big enough storage space mounted somewhere to put all the files foremost will dump for you.

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

sudo foremost /dev/hda -o /media/usbdrive/files

---

### Post by rabidwalrus on 2006-08-26
Alright, thanks! That's precisely what I was looking for.

---

### Post by emunch on 2008-03-03
Hi There, 

I kind of have a similar problem. Would this work after deleting the partition? I did delete the partition by accident thinking I'm working on a different one. Did not touch it after the incident looking for a recovery tool now! I'll try this one now. 

rabidwalrus how did it work for you? 

Any other possible tools you can recommend?

Thanks to all in advance.

Cheers,

---

### Post by slick1a on 2008-03-14
TestDisk is a powerful free data recovery program! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting your Partition Table).

PhotoRec is a File Recovery program designed to recover lost files; including video, documents and archives from Hard Disks, CDRom and lost pictures from digital camera memory (thus, its Photo Recovery name). PhotoRec ignores the filesystem and goes after the underlying data, so it can still find files even if your media's filesystem has been severely damaged or re-formatted (overwritten data, of course, can not be recovered).

You can download the latest version from
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

TestDisk & PhotoRec 6.9 comes with numerous improvements.
EFI GUID Partition Table is now supported. EFI GPT is used mainly on Itanium, MacBook and Mac Pro.
Both utilities can use sudo if the user is not root, this functionnality will be enable for MacOSX at least so users won't have to go in command line. Under Linux, disk model is now displayed to help identify the media.
Internal card readers are now better supported under Windows.

TestDisk
New filesystem support have been added: encrypted LUKS, Mac HFSX, Linux raid md 1.0/1.1/1.2 (0.9 was already supported).
UFS, UFS2 filesystem are better identified now.
TestDisk 6.9 handles Mac partition table partially overwritten by an Intel partition.
It display unicode filenames correctly and can handle unicode filesname when copying files from an NTFS partition when supported by the underlying libraries. TestDisk warns if the media is in read-only instead of read-write access.
It's now possible to copy files from a delete FAT partition found by TestDisk (already possible for NTFS) without having to rewrite the partition table. In the advanced functionality, raw partition imaging capability have been added.

PhotoRec
PhotoRec 6.9 can search for lost files in ext2/ext3 unallocated space only (Was available for FAT and NTFS)
It has a better session support that allow a recovery to be strop and restart later. Windows forensics has been improved with the addition of Windows Enhanced MetaFile .emf (Printing), MS Windows Link .lnk, Internet Explorer index.dat (navigation history...). Nunmerous new file formats have been added.
This version fixes Mac Adress Book and Outlook 64-bits .pst recovery and NTFS free space recovery.
Support for .mov, .zip, FastTrackerII Extended Module .xm and ACE archive has been improved.

---

### Post by slick1a on 2008-03-15
The following is intended for research purposes only , I take no resposibility if you do not  read this post in full before trying anything.

If TestDisk is not yet installed, it can be downloaded from TestDisk Download. Extract the files from the archive including the sub-directories.

 One condition:

    * TestDisk must be executed with "Administrator privileges." 

Important points for using TestDisk:

    * To navigate in TestDisk, use the Arrow and PageUp/PageDown keys.
    * To proceed, confirm your choice(s) with the Enter key.
    * To return to a previous display or quit TestDisk, use the q (Quit) key.
    * To save modifications under TestDisk, you must confirm them with the y (Yes) and/or Enter keys, and
    * To actually write partition data to the MBR, you must choose the "Write" selection and press the Enter key. 

Code sudo testdisk-6.9/linux/testdisk_static

Here's how i did it; 

1. opened terminal typed 'pho' and hit the autocomplete button (tab) why didnt i just think of this in the first place ?? dur !!

2. Enlarged terminal window as 'Photorec' needs 25 lines to work

3. Of options : Disk /dev/hdc - 2048 B (R0)  selected Disk /dev/sdf - 320 GB / 298 GiB (R0)

4. Hit proceed   - N/B of note: Some disks won't appear unless your a root user. Disk capacity must be correctly detected for a successful recovery. if a disk listed above has an incorrect size, check jumper settings, BIOS detection, and install the latest OS patches and disk drivers.

5. now select the partion table type, pushing enter when done :
[intel] Intel/PC Partition   < my choice > usually the default value is the correct one as TestDisk auto-detects the partition table type
[Mac] Apple partition map
[None] non partitioned media
[Sun] Sun solaris partition
[Xbox] Xbox partition
[return] return to disk selection

6. checked file options photorec searches for, as i'm specifically searching for .jpegs

7. To recover lost files, Photorec needs to know the filesystem type were the files are stored:

[ EXT2/EXT3]  EXT2/EXT3 filesystem
[ Other] FAT/NTFS/HFS+/ReiserFS/. . .       < my choice

8. then i got fumbled so i looked up  

9. [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

10.  After following the above link , I located missing .jpegs . I recommend this tool for anyone who has accidently deleted a hard drive or has missing files which YOU KNOW are there somewhere.

---

### Post by emunch on 2008-03-23
slick1a,

TestDisk Rocks! I've just saved 200 GB from a wiped disk! As far as parted and foremost they didn't work for me. Thanks a lot all!

---

### Post by slick1a on 2008-05-04
your most welcome EMUNCH !!

---

### Post by alxbb on 2008-06-23
I also suddenly had an Error 17 and tried to repair grub with all the help from the forum. Nothing worked. TestDisk found the partition and identified it as Linux but could not repair it: "filesystem may be damaged". I tried "parted" and rescue but that did not help either. Could it be a hardware error that prevents me from accessing this partition? Although I have backups of everything, I would like to get a copy of all the files in their original folder structure on a separate drive so I can double-check. I am not sure how to get Foremost to work after extracting. Many thanks in advance! Alx

---

