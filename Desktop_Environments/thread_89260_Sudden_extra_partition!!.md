---
title: "Sudden extra partition????!!"
date: 2005-11-12
forum: Desktop Environments
---

### Post by tomwell on 2005-11-12
Hi,

I followed the instructions on this website, 

[http://strdoc.net/2005/10/10/mounting-windows-xp-drive-ntfs-on-linux-ubuntu/](http://strdoc.net/2005/10/10/mounting-windows-xp-drive-ntfs-on-linux-ubuntu/)

and it seems to have created a 6th partition on my hard drive... All i was tryng to do was to mount my ntfs partition to read only ...  
I also get at start up when the computer is booting 

mounting local file systems [COLOR="Red"]Failed[/COLOR]

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         523     4200966   1b  Hidden W95 FAT32
/dev/hda2   *         524        7271    54203310    7  HPFS/NTFS
/dev/hda3            9274        9729     3662820    5  Extended
/dev/hda4            7272        9273    16081065   83  Linux
/dev/hda5            9365        9729     2931862+   b  W95 FAT32
/dev/hda6            9274        9363      722862   82  Linux swap / Solaris
l

can any one tell me what all this is about... am worried i have messed up my partitions...

Peace 
Tom

---

### Post by adwait on 2005-11-12
It says make a backup of fstab. If you did....you can restore that. If not, post the output of
```
sudo fdisk -l 
``` here.

---

### Post by tomwell on 2005-11-12
hey,

This is the result of sudo Fdisk: 

[COLOR="Red"]Device Boot Start End Blocks Id System
/dev/hda1 1 523 4200966 1b Hidden W95 FAT32
/dev/hda2 * 524 7271 54203310 7 HPFS/NTFS
/dev/hda3 9274 9729 3662820 5 Extended
/dev/hda4 7272 9273 16081065 83 Linux
/dev/hda5 9365 9729 2931862+ b W95 FAT32
/dev/hda6 9274 9363 722862 82 Linux swap / Solaris
l[/COLOR]

In theory i should only have 5 partitions:
1 for windows operating sys.
2 windows data
3 Ubuntu/linux
4 fat32
5 shared something...

But i get 6 thats is what am worriewd about... Oh and the message in boot up....


How do i restore the fstab file?? i just followed the code so am not sure where the back up is....


Ps thanks for your help i really appreciate it...!!!!

---

### Post by Kapre on 2005-11-12
[QUOTE=tomwell]hey,

This is the result of sudo Fdisk: 

[COLOR="Red"]Device Boot Start End Blocks Id System
/dev/hda1 1 523 4200966 1b Hidden W95 FAT32
/dev/hda2 * 524 7271 54203310 7 HPFS/NTFS
/dev/hda3 9274 9729 3662820 5 Extended
/dev/hda4 7272 9273 16081065 83 Linux
/dev/hda5 9365 9729 2931862+ b W95 FAT32
/dev/hda6 9274 9363 722862 82 Linux swap / Solaris
l[/COLOR]

In theory i should only have 5 partitions:
1 for windows operating sys.
2 windows data
3 Ubuntu/linux
4 fat32
5 shared something...

But i get 6 thats is what am worriewd about... Oh and the message in boot up....


How do i restore the fstab file?? i just followed the code so am not sure where the back up is....


Ps thanks for your help i really appreciate it...!!!![/QUOTE]

Sir - the 6th one is your linux swap. During the installation of Ubuntu, it asked you to create a swap drive.

K

---

### Post by adwait on 2005-11-12
Sorry, I meant could you post your fstab file here.

---

### Post by tomwell on 2005-11-12
Kapre 

Thank you for responding...

I rememeber that i needed to install a swap partition, a very small one i think 700MB or so... But that was my 5th partition In my last post i named it as "shared something"... 

That is why i am confused about the amount of partitions i have...

What would happen if i was to delete everything on my linux partions... would they merge back into my windows ntfs, then i could reeintsall Ubuntu/linux....

Thanks for your help!!

---

### Post by tomwell on 2005-11-12
Adwait here is the content of my fstab file...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb5 /media/xpdata ntfs nls=utf8,umask=0222 0 0


I hope this helps in determining what the prob is....

---

### Post by Kapre on 2005-11-12
[QUOTE=tomwell]Kapre 

Thank you for responding...

I rememeber that i needed to install a swap partition, a very small one i think 700MB or so... But that was my 5th partition In my last post i named it as "shared something"...[/quote]

You said you renamed it to "shared something". I guess that's why you got the 6th one because linux is looking for the swap and since the other was renamed to "shared something", it created a new one. 


> What would happen if i was to delete everything on my linux partions... would they merge back into my windows ntfs, then i could reeintsall Ubuntu/linux....

Thanks for your help!!

If you delete everything on your linux partition, it would not merge with your NTFs but will be another empty partition. If your reinstalling Ubuntu - just select the same partition (during the installation process) and erase entire partition. If will also ask you for a swap partition (if you have a lot of RAM in your pc - you have the  option of not creating a swap).

K

---

### Post by tomwell on 2005-11-12
Kapre,

Will all the partitions i used for installing linux merge together, or remain separate partitions??

T

---

### Post by Kapre on 2005-11-12
[QUOTE=tomwell]Kapre,

Will all the partitions i used for installing linux merge together, or remain separate partitions??

T[/QUOTE]

Tomwell - They will merge if they are in sequence. But looking in your post, there is fat32 in between so they will not merge into one. They will merge if you will also delete the win partition.

K

---

### Post by tomwell on 2005-11-12
ok really weird... i just formatted everything re-installed ubuntu and the same thing happens allthough i have only 5 partitions, fdisk command, list 6... weird!!! LMAO!!!

If anyone knows why Fdisk is giving me 6 instead of 5 partitions...(I am using the sudo fdisk- command...)

I guess i should not have reformated everything... LMAO At least i know how to do partitions now!!!! LMAO!!!!

;o)

Tom

---

### Post by slux on 2005-11-13
Your partition table is normal. hda3, which is labeled as "Extended" in the partition list is actually just a "container" for the logical partitions which are numbered starting from hda5 upwards.

---

### Post by tomp88 on 2005-11-13
Sir:
When secondary partitions are in use, they are enclosed in what
is called an "extended" partition.  Look at your fstab and notice
what is says about /dev/hda3!

Good luck.

---

