---
title: "How to recover data from casper-rw?"
date: 2009-03-26
forum: General Help
---

### Post by leet hacker on 2009-03-26
I made a USB startup disk with the "Create a USB startup disk" wizard with Ubuntu 8.10 Live CD. I allocated 3.1 GB for storing files + settings. I stopped using the CD in favor of the USB (I did a full install onto the computer's hard drive but I get GRUB error 18 which is why I'm using live CDs/USBs).

Earlier today I installed updates for the live USB and some of them failed to download (I cannot remember which ones). I rebooted and when it started again, programs would not start (I would see the "Starting <program name>" but then the program wouldn't start). I shut the computer down and put the USB stick in my desktop computer and started the live USB. It showed the live CD menu with the options to try Ubuntu, install Ubuntu, check CD for errors, etc. It got to the loading screen but after it loaded it went straight to a command-line shell. It was just like a terminal with the "ubuntu@ubuntu:" etc. I could run the programs I had written that were text-based so I hoped maybe I could copy some of my important files to another USB drive or something. I had to reboot (I can't remember why) and then it didn't even get to the command-line shell. It said it was loading things ( like, "Starting Wacom... [ OK ]"  ) and on some things it said that there was no free space on the disk (which makes sense since casper-rw is 3.1 GB and the OS takes up 700 MB and my drive is 4 GB).

I do not know what to do. Any help would be greatly appreciated as I have some important files stored on the USB disk but I don't know how to retrieve them from casper-rw (I know, I probably should have backed them up).

EDIT: I'm using a Kingston DataTraveler 4GB flash drive with FAT32 file system.

---

### Post by leet hacker on 2009-03-27
Bump

---

### Post by leet hacker on 2009-03-29
Bumpity-Bump

---

### Post by leet hacker on 2009-03-30
Does no one have any ideas?

---

### Post by leet hacker on 2009-03-30
I searched some more and found that someone had used The Sleuth Kit to view the contents of his casper-rw file. I installed TSK and did what he did. Here is the output:
```
ubuntu@ubuntu:/media/UBUNTU$ fls casper-rw
d/d 11:	lost+found
r/r 12:	.wh..wh.aufs
d/d 7937:	.wh..wh.plnk
d/d 174593:	.wh..wh..tmp
d/d 95233:	rofs
d/d 111105:	etc
d/d 158721:	cdrom
d/d 63489:	var
d/d 142849:	home
d/d 71425:	tmp
d/d 103169:	usr
d/d 119041:	sbin
d/d 15873:	lib
d/d 182529:	root
d/d 126977:	media
d/d 23809:	bin
d/d 31745:	boot
d/d 198558:	gconf--0KDI_
r/r * 4277(realloc):	.aufs.xino
d/d 206337:	$OrphanFiles
```
I do not know how to view the contents of the folders without viewing every single file and folder in the entire casper-rw. Is there a way to view the contents of files or to copy and paste folders/files using sleuthkit?

---

### Post by leet hacker on 2009-03-30
Bump-bump

---

### Post by leet hacker on 2009-03-31
LOL, this is like a one-person bump thread

---

### Post by leet hacker on 2009-04-05
Anyone?

---

### Post by leet hacker on 2009-04-16
I forgot about my question... It's not as urgent any more but I'd still like to recover the files if possible.

---

### Post by seventyeights on 2009-04-17
Can you mount it?

> Endolith
just make a directory to mount it in:

sudo mkdir /media/casper

and then mount it:

sudo mount -o loop casper-rw /media/casper/
[http://ubuntuforums.org/archive/index.php/t-1028564.html](http://ubuntuforums.org/archive/index.php/t-1028564.html)

---

### Post by leet hacker on 2009-04-20
Thanks, it works!

---

### Post by tulcak on 2009-08-26
Thank GOD!!  I have been searching for days on how to recover my Documents folder from my USB Ubuntu bootable flash disk.  Why is it that people who are obsessed, nay, slaves to the command line assume that everyone should know certain things... and then do their best to take something soooo simple and make it more complicated than DNA.

Two simple commands and I have restored my documents.  GEEEESSSHHHHH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Mr. Keepitsimplestupid

---

### Post by agustincordoba on 2010-08-27
Hi there

I know this is probaly an old and forgotten thread now, but I just wanted to say thank you for the explanation on how to mount casper-rw. This was of great help to me, as I am using a live linux from flashcard, so it was not just a problem with permissions.

I did as suggested, creating 
/media/casper which then I mounted it with 
"mount -o loop /media/PENDRIVE/casper-rw /media/casper/"

I am not quite sure of the meaning of "-o loop" but it worked just fine

I unmounted with "umount /media/casper"

All well, thanks again

Update: I see now that -o loop is for mounting *.iso, I should have checked before :)

Agustin

---

### Post by MestreLion on 2010-12-09
Similar problem here... ubuntu restats the PC when loading, it never reaches the desktop screen. I suspect its (system) files got corrupted. If i plug the USB drive in another working comouter, i can mount and read casper-rw, and back up all my /home folder, but i would really like to make that USB boot (i mean, load) again... been using it for 3 months, LOTS of programns, updates and configuration done on it.

The files and folders in both live and casper seem, at first glance, to be OK. No read errors, i can browse all folders, etc. But i noticed some strange stuff in casper-rw partition:

/.wh..wh.orph (folder, empty)
/.wh..wh.plnk (folder, 26.044 items!!!!)
/.wh..wh.aufs (file, 0 bytes)

What are those folders?? is /.wh..wh.plnk some sort of "recovered files form a failed checkdisk"? Are those corrupted files? How can i restore them and make that system work again?

Any help would be appreciated!

---

### Post by C.S.Cameron on 2010-12-09
> **MestreLion said:**
> Similar problem here... ubuntu restats the PC when loading, it never reaches the desktop screen. I suspect its (system) files got corrupted. If i plug the USB drive in another working comouter, i can mount and read casper-rw, and back up all my /home folder, but i would really like to make that USB boot (i mean, load) again... been using it for 3 months, LOTS of programns, updates and configuration done on it.

The files and folders in both live and casper seem, at first glance, to be OK. No read errors, i can browse all folders, etc. But i noticed some strange stuff in casper-rw partition:

/.wh..wh.orph (folder, empty)
/.wh..wh.plnk (folder, 26.044 items!!!!)
/.wh..wh.aufs (file, 0 bytes)

What are those folders?? is /.wh..wh.plnk some sort of "recovered files form a failed checkdisk"? Are those corrupted files? How can i restore them and make that system work again?

Any help would be appreciated!

Sometimes computer janitor will restore some space, if not:
Mount casper-rw and delete unnecessary stuff, start at var/cache/apt/archives/

---

### Post by doperative on 2011-01-07
> **MestreLion said:**
> Similar problem here... ubuntu restats the PC when loading, it never reaches the desktop screen. I suspect its (system) files got corrupted.

You suspect correctly, it appears casper-rw isn't being cleanly unmounted, eventually this leads to the file system getting corrupted. The only solution being to boot from the LiveCD and run fsck -y /dev/casper-rw-partition. I would have thought this would be a high priority to fix.

[casper-rw fs not cleanly unmounted]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702")

---

