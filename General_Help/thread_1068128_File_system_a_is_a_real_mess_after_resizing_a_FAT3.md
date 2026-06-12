---
title: "File system a is a real mess after resizing a FAT32 partition"
date: 2009-02-12
forum: General Help
---

### Post by Benic on 2009-02-12
I have a Samsung external hard drive that I use for backups. I resized a FAT32 partition with Gparted (the partition wasn't fragmented), but the file system is now a total mess. I can't do a disk check with GParted Live CD. There's an error message saying that the boot and backup sectors are not identical. I tried to save the error message, but the system hangs when I do so. I tried to fix it using Testdisk, but I'm not very familiar with it. Can I recover the data?

---

### Post by jerome1232 on 2009-02-12
Yikes, while I may not be of much help with the actual recovery process I can suggest one thing, make an image of the partition and do your recovery attempts on the image file, this way you can use destructive recovery attempts without fear of losing any data, you can just make a new image file if the attempt ends up doing more damage.

--edit-- hopefully this will be of help

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by mttman on 2009-02-12
Hello,

Have you tried using another OS to look at the data? can you still see the files you had on the drive? 

Generally speaking from my experience - if you can see it and read it you can copy it. At this point i would recommend trying to backup the data and reformat your partition. 

I don't know why Gparted would have done this, I've never had trouble with it before. It could just be that it was some little setting in Gparted but I don't know for sure.

If you can answer those questions we might be able to diagnose the problem a little better.

I would also suggest that check around the Gparted site to look for some information about the issue your having. 

<Mttman>

---

### Post by Benic on 2009-02-12
> **mttman said:**
> Hello,

Have you tried using another OS to look at the data? can you still see the files you had on the drive? 

Generally speaking from my experience - if you can see it and read it you can copy it. At this point i would recommend trying to backup the data and reformat your partition. 

I don't know why Gparted would have done this, I've never had trouble with it before. It could just be that it was some little setting in Gparted but I don't know for sure.

If you can answer those questions we might be able to diagnose the problem a little better.

I would also suggest that check around the Gparted site to look for some information about the issue your having. 

<Mttman>

I can see most of the files and folders, but the files are unreadable. I tried to use Windows-based recovery software with Hiren's Boot CD, but I don't know how to use it with an external drive.

My problem is that I can't copy the partition, because it's too big. I'll try to look for another external drive that I can borrow. 

Could a broken partition table be the problem?

---

### Post by Benic on 2009-02-12
I decided to give photorec a try. I can copy the files, but they are misnamed. They all have a name starting with F and a couple of digits after that. It will take ages to sort this mess, especially since there are no folders. But at the very least, I can recover everything!

---

### Post by 1ronlung on 2009-02-12
If you installed an OS on the partition you made, try supergrubdisk to boot from it ?..

---

### Post by Benic on 2009-02-12
> **1ronlung said:**
> If you installed an OS on the partition you made, try supergrubdisk to boot from it ?..

There's no OS installed. It's mainly a 250Gb storage drive.

---

### Post by Benic on 2009-02-15
Bump...

---

### Post by caljohnsmith on 2009-02-15
Benic, how about posting:
```
sudo fdisk -lu
```
Also, I'm not sure what version of testdisk you are using, but if you are using a version prior to 6.10, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/[COLOR="Blue"]sdXY[/COLOR]
```
And replace sdXY with your FAT partition. Then select "Proceed", "None", "Advanced", "Boot", then select "Rebuild BS". If testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After that try mounting the partition:
```
sudo mount /dev/[COLOR="Blue"]sdXY[/COLOR] /mnt && ls -l /mnt
```
And please post the output.

---

### Post by Benic on 2009-02-16
> **caljohnsmith said:**
> Benic, how about posting:
```
sudo fdisk -lu
```
Also, I'm not sure what version of testdisk you are using, but if you are using a version prior to 6.10, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/[COLOR="Blue"]sdXY[/COLOR]
```
And replace sdXY with your FAT partition. Then select "Proceed", "None", "Advanced", "Boot", then select "Rebuild BS". If testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After that try mounting the partition:
```
sudo mount /dev/[COLOR="Blue"]sdXY[/COLOR] /mnt && ls -l /mnt
```
And please post the output.


OK, here's the first output (sorry it's in French):

Disque /dev/sdb: 250.0 Go, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x00000000

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1              63   488392064   244196001    c  W95 FAT32 (LBA)


I realised I was using Testdisk 6.9 instead of 6.10. I followed your instructions in Testdik. When I choose Advanced, I have two options: Change type or create image. Should I change type to unknown or FAT32?

Thanks

---

### Post by caljohnsmith on 2009-02-16
So after selecting "Advanced", you only see two options, i.e. "Type" and "Image Creation", but no "Boot" option? Did you make sure to run testdisk on the particular FAT32 partition like:
```
sudo testdisk-6.10/linux/testdisk_static [COLOR="Blue"]/dev/sdb1[/COLOR]
```
If so, how about instead running testdisk again with the above command, choose "Proceed", "None", "Analyze", "Quick Search", then press "p" to see if testdisk will display the directory contents of that partition. Does that work?

---

### Post by Benic on 2009-02-16
I forgot to add '1' after 'sdb'. Ok, now Testdisk is looking for root cluster. It will take time (1% after 10 minutes).

---

### Post by Benic on 2009-02-17
Testdisk went through all clusters, but at the end, it says no file found, filesystem seems damaged.

---

### Post by caljohnsmith on 2009-02-17
If you really want to recover your files from that partition, you could try "photorec" which comes in the testdisk package. You will need some place to save all the recovered files to that is at least as large as the sdb1 FAT partition. You can run photorec simply by doing:
```
sudo photorec /dev/sdb1
```
Good luck and let me know how that goes if you decide to give it a try.

---

### Post by Benic on 2009-02-17
I already did that. Photorec is awesome! The only drawback is that now files are named by the sector they were found on. So I have thousands of files to check. Pictures are easy to sort out, but documents and pdfs will take few days. 

Thanks for the help!


EDIT: Because it too much a mess and I don't have time to rename 5000 files, I tried several Windows recovery software R-studio to see if I can find one that gives files and folders names. The only one that is really working is R-Studio. 49$ and it's worthing it. Saved me a lot of time!

---

