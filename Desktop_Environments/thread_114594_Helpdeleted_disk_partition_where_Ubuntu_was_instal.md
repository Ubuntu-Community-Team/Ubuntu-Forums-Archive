---
title: "Help:deleted disk partition where Ubuntu was installed"
date: 2006-01-08
forum: Desktop Environments
---

### Post by sup on 2006-01-08
First of all, I am stupid. Being clear on that, we may as well proceed to the reasons and solutions. Any help from you will be greatly appreciated.

Also, I am not sure if this is really related to Ubuntu, but I do not know any other place in linux world to ask and I hope it warns someone who could be as silly as me - and also that I get some advice.

I had Ubuntu installed on a logical partition, Windows on primary. As I decided to move to Ubuntu as my primary desktop, I decided to reinstall Windows since it got too big (7GB) and slow. It went well, only the GRUB table was deleted, but it was not a problem, because I know how ot painlessly restore it with Ubuntu install CD. However, since the install of Windows had about 2GB, I decided it would be a nice idea to shrink windows partition because I did not plan on using it much nor installing much stuff on it. Somehow I got to having some filest that allowed me to install Partition Magic. I tried to resize the windows partition with it. It offered me to create a rescue disc, which I refused as it never was needed before (and there is no floppy drive in my laptop and I did not have any CDRW around, but then again, yeah, you are right, it was really silly and stupid of me), then it rebooted computer. However, it printed out some errors after that and rebooted once more. I still, feeling alright opened the program again only to find out that my partition with Ubuntu was somehow lost (unlocated space being where in  the place Ubuntu should be). 

After short period of panic, I remebred drive rescue, found out it does not work for ext3, so I googled a bit and found R-Linux. I hope it will do the trick. I installed it, scaned the physicall drive where Ubuntu used to be and I was able to see all the system files. Right now I am recovering all of them to my external harddrive (takes ages, although it is just 3,3GB) and I am planning on making a complete image of the drive as well just to be sure I will not lost my system. However, I am kind at a loss as to how restore Ubuntu to be usable right now. 

I am thinking about using the Ubuntu install to create an ext3 partition in unalocated space where Ubuntu used to be and than copying the restored files there (using some live CD). But I am not sure if the restored files saved to FAT partition will do - will the file permissions be stored in them or not? And will the whole process work or should I do something else? I will be gald for any suggestions as it takes at leas an half an hour to try anything (I have  written this post during saving former Ubutnu files and I am afraid it is not going to stop anytime soon).

---

### Post by Sef on 2006-01-09
If your files are saved on the external hard drive,  I would reinstall Ubuntu on the empty space.  Make a /home and then move your files from your external hard drive to to there.  If you're unsure of how to dual boot or simply install see this:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by sup on 2006-01-09
Well, I can give it a go{in several hours as soon as I get home], but I would like to have the same system as before (with everything set up and installed]  I store my /home directory on another partition, so that it is not really an issue. Maybe just reformating the partition and then moving all those files in there would do?

---

### Post by Luke771 on 2006-01-09
I think you can't get your old system back, you will have to reinstall; you did not lose your data, which is actually good news, but as for your installation with everything set up...it's gone.
After reinstalling, install Automatix so you can set up your system with your favorite programs up and running in five minutes (well, almost all of them).
Why did you install Ubuntu on a logical partition in the first place? Next time, make two primarys instead, one for ubuntu and one for windows, make the ubuntu partition active so Grub will load first.
A good way to keep your data from disappearing if one or even both OS's screwes up, is to make a logical FAT32 partition and use it to store your data (make it FAT32 because it is accessible and safely writeble bay both Linux and Windows). The swap partition should be at the beginning of the space after the two primarys as the first logical partition with the FAT32 partition last.
As for the two primary, something like 6-10 GB each should be enough to have place for all the programs you could possibly install (except for some windows games, in which case I suggest a dedicated games partition), all the rest will be file storage, FAT32 will do fine, will be accessible by both and wont disappear, no matter what happens to the OS's.

---

### Post by lha on 2006-01-09
Ever heard of [gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/")? It tries to guess where and what kind of partitions you had on your drive. There's also [fixdisktable]("http://bmrc.berkeley.edu/people/chaffee/fat32.html") (scroll a couples of pages down for info) and [TestDisk]("http://www.cgsecurity.org/index.html?testdisk.html") that have similar features.

---

### Post by steve.horsley on 2006-01-09
Don't try to recover your system files to external drive. Without the right permissions (that get lost on a FAT drive), your rebuilt system would be a bag of holes if it worked at all. Just save your data files.

Then try the partition recovery tools that lha mentions (I haven't tried any personally). 

Failing that, I think you should reinstall and then restore the data files.

---

### Post by sup on 2006-01-09
meanwhile, I found this: [http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition-Rescue.html]("http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition-Rescue.html")
so I am looking for gpart, but there is only gparted on ubuntu live install - is there a way to install anything on live install?

> Don't try to recover your system files to external drive. Without the right permissions (that get lost on a FAT drive), your rebuilt system would be a bag of holes if it worked at all. Just save your data files.

 i have also ext3 partition on my harddrive, would it work with that?

---

### Post by lha on 2006-01-09
[QUOTE=sup]meanwhile, I found this: [http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition-Rescue.html]("http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition-Rescue.html")
so I am looking for gpart, but there is only gparted on ubuntu live install - is there a way to install anything on live install?


 i have also ext3 partition on my harddrive, would it work with that?[/QUOTE]

There's a statically linked binary on [gpart's homepage]("http://www.stud.uni-hannover.de/user/76201/gpart/").  AFAIK, you just have download that file and make it executable. No further installation should be needed to make it usable.

You'll be much better of with copying files to an ext3 partition because you can preserve file permissions using correct options with cp. (Something like -axu.) You can also use tar to make one big file containing all your files. This backup-file can reside on fat32 partition, too. Again, remember to tell tar to preserve ownership and premission on all files you back up.

---

### Post by sup on 2006-01-09
I just found out you can install stuff via synaptic even on live CD, only thing needed is to add a repository:
```
ubuntu@ubuntu:~$ sudo gpart /dev/hda

** Error: invalid extended ptbl found at sector(6843690).

Begin scan...
Possible partition(Windows NT/W2K FS), size(3341mb), offset(0mb)
Possible partition(Linux ext2), size(5977mb), offset(3341mb)
Possible extended partition at offset(9318mb)
   Possible partition(Linux ext2), size(5796mb), offset(9319mb)
   Possible partition(Linux swap), size(282mb), offset(15115mb)
   Possible partition(Linux ext2), size(22803mb), offset(15398mb)
End scan.

Checking partitions...
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary
Partition(Linux ext2 filesystem): primary
   Partition(Linux ext2 filesystem): logical
   Partition(Linux swap or Solaris/x86): logical
   Partition(Linux ext2 filesystem): orphaned logical

* Warning: partition(Extended DOS, LBA) ends beyond disk end.
Number of inconsistencies found: 1.

Guessed primary partition table:
Primary partition(1)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 3341mb #s(6843624) s(63-6843686)
   chs:  (0/1/1)-(425/254/60)d (0/1/1)-(425/254/60)r

Primary partition(2)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 5977mb #s(12241400) s(6843816-19085215)
   chs:  (426/2/1)-(1023/254/63)d (426/2/1)-(1187/254/59)r

Primary partition(3)
   type: 015(0x0F)(Extended DOS, LBA)
   size: 34859mb #s(71392860) s(19085220-90478079)
   chs:  (1023/254/63)-(1023/254/63)d (1188/0/1)-(5631/254/63)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```
now I am going to do ```
man gpart
``` and see what can be done, but I am averall optimistic, those are my partitions.
(and if that will now work, I will just back it up to ext3)

---

### Post by sup on 2006-01-09
thank you all for help, I somehow made it and now I am writing from my proper Ubuntu box which feels real good after all those live CDs. I followed the tutorial I linked above and somehow with help of gpart and fdisk was able to set up partitions in such a way that they work and then I used install CD to make GRUB work. However, several things happened - I changed the extended partition where ubuntu used to be to primary (just by editing partition table) - and it works, to my surprise, actually, I could not believe my eyes when Ubuntu started to coming up, not mentiong my pleasure when I saw it in GRUB:-) - and the three of my partitions somehow grew in size - I do not know how, but together they took about 1GB more of my 40GB disk then they did before, but then again, it just works (I do not understand how). However, my back up was not perfect, so I lost couple of settings, about half of Opera (which is the program I have tweaked the most:-()... but I might still be able to recover them and I do not really care that much either.

However, during my trials, I replaced Windows system on my first partition with linux partition and system (crippled)... I will probably want to install Windows there (as far as goes my understanding, they must be installed in this partition), I would not like to lost grub stored there either, is it somehow possible to overcome this (by creating grub CD or something...

Also I am aware I need to do something really dramatic with my disc now because it is far from being in order, but now I am just going to bed:-D.

---

### Post by sup on 2006-01-14
In the end I found out that changing type of partitions form extended to primary was not a such a good idea (it was responsible for various things not working properly), so I (using gpart and some common sense) set it back how it used to be and now everything works well again. I only advice to save your partition table somewhere and also your /etc/fstab since it gets rewritten everytime you move your system on harddrive somehow - at least it seems so to me.

---

