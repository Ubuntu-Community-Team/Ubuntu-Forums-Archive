---
title: "I need my documents back"
date: 2009-02-21
forum: General Help
---

### Post by Nnako2 on 2009-02-21
Hi, maybe this topic is very usual, but nothing I found helped me...

Im on Ubuntu 7.10 and today I was deleting some documents I didn't need, but accidentally I deleted some important documents too. I have no idea of how many they were, or what their name was, but I need them back because they were almost all my documents for a year...

Everything I found was useless to me, because I don't need to recover all the hard disk but only those documents that I deleted today... 

Sorry for my bad English and for my little knowledge about this. I wish this forum would help me again. Thanks a lot.

---

### Post by oldos2er on 2009-02-21
Did you use Nautilus to delete these files? If so, they should be in /home/[user]/.local/share/Trash/files

---

### Post by Nnako2 on 2009-02-21
I used shift+supr... :(

I see nothing in there

---

### Post by doas777 on 2009-02-21
did you empty the trash? 
you may be able to recover deleted files with a tool like photorec, but you should shutdown/unmount the affected partition asap, so you don't accidentally overwrite the files you want to recover.

do you have another computer and perhaps a large external hdd?

---

### Post by doas777 on 2009-02-21
check out this thread. it should help. [http://ubuntuforums.org/showthread.php?t=1043909](http://ubuntuforums.org/showthread.php?t=1043909)

good luck,
franklin

---

### Post by Nnako2 on 2009-02-21
Yes, I have another PC but it's only Windows XP. And I have a 500gb external hd.

I'll see the link now

---

### Post by doas777 on 2009-02-21
Sweet! that should work. you only need the other pc to get to the internet while the affected one is shutdown.

---

### Post by Nnako2 on 2009-02-21
Ok, I just read the link, and I must say I burned a CD with Ubuntu Rescue Remix as an ISO, but I didn't know what to do when I booted it... o.o'

About creating an image file of the disc... I don't know how, I tried this [http://belinux.wordpress.com/2007/07/16/porque-es-dificil-recuperar-un-fichero-borrado-de-ext3/](http://belinux.wordpress.com/2007/07/16/porque-es-dificil-recuperar-un-fichero-borrado-de-ext3/) and this [http://www.veoh.com/browse/videos/category/educational/watch/v650805xkjawbh3](http://www.veoh.com/browse/videos/category/educational/watch/v650805xkjawbh3) before
but I got lots of things I didn't want :S
In fact, when the file got to 4 gb it stopped because "it had reached the size limit", and it wasn't useful for me


By the way, where should I download Photorec?

---

### Post by doas777 on 2009-02-21
photorec is on the rescueremix cd. here is a tutorial on it: [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

your best bet for getting your files back, is to create an image of the partition that lost the files, and saving the image to your external hard disk. here is a tutorial on making a partition image.
[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)
Note we are not going to "restore" the image, we just need a copy of your harddisk that we can work with, without accidentally overwriting your files.
you can forgo the imaging if you want, but it reduces the chances of success.

after you create an image file you mount it: [http://greekbitches.blogspot.com/2008/04/howto-mount-partition-image.html](http://greekbitches.blogspot.com/2008/04/howto-mount-partition-image.html)

and run photorec, examining the image for deleted files. if the files are found, you just save them to somewhere on the external harddisk. then when you are done, you can copy them back to the drive they came from and delete the image.


good luck

---

### Post by Nnako2 on 2009-02-21
Thanks for everything but...



paula@paula-laptop:~$ fdisk -l 

Disc /dev/sdb: 500.1 GB, 500107862016 octets
255 heads, 63 sectors/track, 60801 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)
paula@paula-laptop:~$ fdisk -l 

Disc /dev/sdb: 500.1 GB, 500107862016 octets
255 heads, 63 sectors/track, 60801 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)
paula@paula-laptop:~$ mount /media/LACIE/backup
mount: no s'ha pogut trobar /media/LACIE/backup a /etc/fstab o /etc/mtab
paula@paula-laptop:~$ mount /dev/media/LACIE/backup
mount: no s'ha pogut trobar /dev/media/LACIE/backup a /etc/fstab o /etc/mtab
paula@paula-laptop:~$ 


"no s'ha pogut trobar" = "couldn't find"
"a"="at"

---

### Post by doas777 on 2009-02-21
that message indicates that the mount point you are requesting does not exist in the fstab or mtab. all that means is you have to specify the device. also mount won't usually make dirs for you so make sure you create them first.

try ```

sudo mkdir /media/LACIE/backup
sudo mount  /dev/sdb /media/LACIE/backup

```

---

### Post by Nnako2 on 2009-02-21
paula@paula-laptop:~$ sudo mkdir /media/LACIE/backup
[sudo] password for paula:
mkdir: no s'ha pogut crear el directori(couldn't be created) «/media/LACIE/backup»: File exists
paula@paula-laptop:~$ sudo mount  /dev/sdb /media/LACIE/backup
mount: /dev/sdb ja està muntat o(is already mounted or) /media/LACIE/backup està ocupat (is busy/occupied)


thanks! I think xd

---

### Post by Nnako2 on 2009-02-21
It tells me to unmount the partition I want to backup, but i'm working with it, and with the Ubuntu live CD, i never have internet connection, so I would be lost...

---

### Post by Nnako2 on 2009-02-22
I finally tried photorec without any image file, but almost everything I get tells "error" when I try to open it.

By the way, is there any way to know what files I deleted so that I could know if they were important? Is it recorded at any history? Thanks a lot

---

### Post by rosencrantz on 2009-02-23
Hey Nnako2,

I don't quite understand your comment about working with the partition you want to backup. 
In case you want to get a bit-by-bit image of any partition, boot a live system, don't mount the partition to be backed up, but mount e.g. an external rescue partition and do a copy with dd or something similar. You have to back up the whole partition, because you have no idea which sector your deleted files were in. After that, unhook the partition and work (e.g. photorec) on the image.
The size limit problem is because your LaCie disk is formatted FAT32: file sizes may not exceed 4GB and your image will be a single file exactly as big as your hard disk capacity. If it's empty, you had better re-format it to ext3 or NTFS.
Do you know on what kind of partition your lost files were? You could get lucky if you have ext2 (or even more lucky, FAT ;-) ). ext3 overwrites the block pointers, instead of marking them to be unused, which is bad news for lost files (see [this article]("http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html")). Still, photorec is probably your best option in all cases.

Best of luck
rosencrantz

---

### Post by rosencrantz on 2009-02-23
PS: AFAIK, the only app keeping track of file deletion is the waste bin, which isn't going to help in your case.
What you could do would be to let photorec search for certain file types (e.g. *.pdf, *.doc, *.jpg) and their characteristic headers. This works if your data isn't fragmented (more success with smaller files).

---

### Post by Nnako2 on 2009-02-27
Thanks to you too, rosencrantz. It's good to know that the size limit problem is because lacie is formated FAT32. Unfortunately, my Ubuntu partition is ext3, so I'm not very hopefut about getting my files back... There were small files from a folder, and I even don't remember all I had there...

I tried photorec, foremost, etc, and all the .doc or .txt I got were lots of files I didn't create. I think my problem is that I haven't lost all the partition (which is not a problem, of course!) but a single folder so it's very difficult for me to get all the files that I even don't remember, although I think I would had liked to have them...

Anyway, thanks you both. I'll keep trying :)

---

### Post by BOOBOOJS on 2009-02-27
Try this:
[http://ubuntumagnet.com/2007/09/recovering-deleted-files-ext3-filesystem]("http://ubuntumagnet.com/2007/09/recovering-deleted-files-ext3-filesystem")
good luck

---

### Post by Nnako2 on 2009-03-04
Thanks but I had loooots of pictures in my computer some time ago, and it only recovers that and documents from programs or something, because I don't want them... :(

---

### Post by mal_conductor on 2009-03-29
these are my notes on how to recover files using photorec and testdisk.
[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

