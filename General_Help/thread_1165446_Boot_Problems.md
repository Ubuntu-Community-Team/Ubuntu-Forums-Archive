---
title: "Boot Problems"
date: 2009-05-20
forum: General Help
---

### Post by X1R1 on 2009-05-20
Hi all!! I expect someone can help me with this issue

ok here is my question

Recently I installed on my computer a program called "Acronis True Image home" said to be the best program around to make full PC backups. 

This software has an option called "Acronis Safe Zone" in which I can specify a partition and the run the software from there (not from windows, standalone
version to backup in case of disaster).

So after I made this...now my computer only can see the XP partition and not the Linux one, no idea why. Maybe it got messed up with grub configuration or
something. So to try and recover my boot backto normal. I saw an option of this software called "Acronis OS selector" so I tought that if I was able to
manually select my linux partition it will be all back to normal. So I decide to rey it out. when the program opens up before any OS it lets you select
the OS that you want to boot. AND THERE was my UBUNTU partition! GREAT!!! everything is solved....WRONG!!! I select it and the screen goes black and start
printing out nines...yes..."9" lots of times...till it crashes.

I know my linux partition its still there untouched cause I can see it from this Acronis OS selector and I can see all the files in the partition. But no
boot.

I think the solution here is to insert the ubuntu cd, ADD this "acronis safe zone" (the one I explained at the beginning of this post) to GRUB and apply
changes, correct me if im wrong. The thing is I have no idea of how to do this. I think i need to edit grub.conf file but I dont know how.

I am willing to give any info you guys need in order to solve this! I want my linux back!!!

PS: After I saw that my linux partition was still there. I deactivated the acronis OS selector. So now the PC boots XP directly like if it was a standalone
OS on my system.


Thank you all for the help and sorry for the long post lol!!

---

### Post by Happy_Man on 2009-05-20
This is rather easy to solve. Download and burn the Super Grub Disk (google for it) and use that to restore GRUB. It should pick up the Acronis system and create a new GRUB menu for you.

---

### Post by X1R1 on 2009-05-20
Thank you very much!!! I will download it right now...try it at night and then report back with results!

thanks for the tips!

---

### Post by X1R1 on 2009-05-22
Here I am again. One thing I forgot to let you know is that I have both my linux and windows installation on one hard disk. and my acronis acronis one on another hard disk. When I insert the Super grub cd It does recognize the windows and linux partitions but does not recognize the acronis one. Any idea how to solve this?

regards

---

### Post by KhurramM on 2009-05-22
I think u are making a big mistake.

Just recover grub first to boot linux.

SGD may not show it. But u have to load it into the grub menu just like windows is loaded.

This u will have to experiment. ;)

---

### Post by VMC on 2009-05-22
X,
I noticed your avatar states your using Jaunty. Do you know which file system you used to install it? In either case, it will have 256-byte inodes, and True Image doesn't understand that. Someone reported that version 9 or 10 of TI will work. If it's Ext4, for sure TI won't recognize it. And your right in the assessment that True Image is the best. Problem is after they moved away from 128-byte inodes TI was left behind. It will backup but only using byte by byte. Very time consuming.

I stayed away from the "Acronis Safe Zone" method and just used either the CD or USB flash as boot up using TI.

There's two other methods to backup your system. Part Magic's partimage (only if your not using Ext4), or Clonezilla, which I use now. The newest version will backup Ext4. It uses Partclone, which backs up using only used sectors. Very fast. Especially on restore. Not as fast as TI but not bad. And WAY faster than tar or dd backups.

---

### Post by X1R1 on 2009-05-25
> **VMC said:**
> X,
I noticed your avatar states your using Jaunty. Do you know which file system you used to install it? In either case, it will have 256-byte inodes, and True Image doesn't understand that. Someone reported that version 9 or 10 of TI will work. If it's Ext4, for sure TI won't recognize it. And your right in the assessment that True Image is the best. Problem is after they moved away from 128-byte inodes TI was left behind. It will backup but only using byte by byte. Very time consuming.

I stayed away from the "Acronis Safe Zone" method and just used either the CD or USB flash as boot up using TI.

There's two other methods to backup your system. Part Magic's partimage (only if your not using Ext4), or Clonezilla, which I use now. The newest version will backup Ext4. It uses Partclone, which backs up using only used sectors. Very fast. Especially on restore. Not as fast as TI but not bad. And WAY faster than tar or dd backups.

Im using Ext3 filesystem. And what you just said makes a lot of sense. Cause If I use Super Grub disk It recovers the boot menu BUT deactivates the safe zone, and If I activate the safe zone I lose my GRUB boot. I have True Image home 2009, I think its the lastest version so It should handle everything as you just stated. what I want its to have the safe zone in a new 500Gb hard disk im going to buy, and choose at startup to either boot ubuntu, windows or the true image recovery manager.

sorry for the delayed response but I didnt have internet at home, but now im backk 100% :D

---

### Post by X1R1 on 2009-05-25
Just found this on the SGD wiki

 >  menu.lst

Just edit your favourite /boot/grub/menu.lst file and write something like:

title Windows
rootnoverify (hd0,0)
chainloader +1
boot

title Fedora 11
rootnoverify (hd0,1)
chainloader +1
boot

title Debian 5
rootnoverify (hd0,2)
chainloader +1
boot

and so on.

Now that /boot/grub/menu.lst you will be able to boot your distributions. 

So...if my Acronis safe Zone is one hd1 (second hard disk) I think I could do:

> [B]title Acronis Recovery
rootnoverify (hd1,0)
chainloader +1
boot[/B]

And so I will have this entry added to my menu.lst. right????

correct me if im wrong...

regards

---

### Post by X1R1 on 2009-05-28
Please...can anyone confirm the entry? I dont want to do this without asking first.

regards

---

### Post by VMC on 2009-05-28
> **X1R1 said:**
> Please...can anyone confirm the entry? I dont want to do this without asking first.

regards
It looks right. Not sure if the Acronis partition is bootable, or rather how it gets booted. Just add that "title" entry. All it will do is error out if it doesn't work. Nothing lost. Come back with results. And exact error message if it does occur.

---

### Post by X1R1 on 2009-06-01
> **VMC said:**
> It looks right. Not sure if the Acronis partition is bootable, or rather how it gets booted. Just add that "title" entry. All it will do is error out if it doesn't work. Nothing lost. Come back with results. And exact error message if it does occur.

Ok tried it and I get this message when trying to boot:

non-system disk. press any key to continue

Does that mean that the partition is not bootable? or that there is some error in the configuration?

regards

---

### Post by VMC on 2009-06-01
> **X1R1 said:**
> Ok tried it and I get this message when trying to boot:

non-system disk. press any key to continue

Does that mean that the partition is not bootable? or that there is some error in the configuration?

regards
Now that I think about it, Acronis has its own boot sector code. It would be difficult to explain how to copy your current mbr then re-install Acronis and save it to a file and use that somehow. 

I'm not even sure what file system Acronis uses. If you do a fdisk -l what does Acronis partition show?

---

### Post by X1R1 on 2009-06-01
> **VMC said:**
> Now that I think about it, Acronis has its own boot sector code. It would be difficult to explain how to copy your current mbr then re-install Acronis and save it to a file and use that somehow. 

I'm not even sure what file system Acronis uses. If you do a fdisk -l what does Acronis partition show?

Where am I supposed to enter this command? in the Super Grub disk command line or In ubuntu command line? I typed "fdisk -l" on ubuntu command and nothing happened....

Found this entering /media/Acronis SZ (hard drive name I gave it) the properties:

Filesystem type: msdos

---

### Post by VMC on 2009-06-01
> **X1R1 said:**
> Where am I supposed to enter this command? in the Super Grub disk command line or In ubuntu command line? I typed "fdisk -l" on ubuntu command and nothing happened....

Found this entering /media/Acronis SZ (hard drive name I gave it) the properties:

Filesystem type: msdos

From a Ubuntu terminal you need to use "sudo", like so:

```
sudo fdisk -l
```

---

### Post by X1R1 on 2009-06-02
> **VMC said:**
> From a Ubuntu terminal you need to use "sudo", like so:

```
sudo fdisk -l
```

here is the complete output

> Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xfe37966b

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       13516   108567238+   7  HPFS/NTFS
/dev/sda2           13517       19457    47721082+   5  Extendida
/dev/sda5           13517       19208    45720958+  83  Linux
/dev/sda6           19209       19457     2000061   82  Linux swap / Solaris

Disco /dev/sdb: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pista, 9726 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xcfce28df

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb2   *           2        9726    78116062+   5  Extendida
/dev/sdb5               2        9726    78116031   ac  Desconocido

Disco /dev/sdc: 203.9 GB, 203928109056 bytes
255 cabezas, 63 sectores/pista, 24792 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x9503c6ab

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1       24792   199141708+   7  HPFS/NTFS


Disco /dev/sdb: 80.0 GB, 80000000000 bytes

thats the one in which I have the acronis SZ

---

### Post by VMC on 2009-06-02
> **X1R1 said:**
> here is the complete output



Disco /dev/sdb: 80.0 GB, 80000000000 bytes

thats the one in which I have the acronis SZ

Ok. It looks like you have 3 hard drives. Are they all internal possible raid or usb?

Also, I'm guessing on the Spanish, but it appears that sdb is missing partition 1, and that's where you tried to title Acronis:
Disco /dev/sdb: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pista, 9726 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xcfce28df

Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/sdb2 * 2 9726 78116062+ 5 Extendida
/dev/sdb5 2 9726 78116031 ac Desconocido

---

### Post by X1R1 on 2009-06-02
> **VMC said:**
> Ok. It looks like you have 3 hard drives. Are they all internal possible raid or usb?

Also, I'm guessing on the Spanish, but it appears that sdb is missing partition 1, and that's where you tried to title Acronis:
Disco /dev/sdb: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pista, 9726 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xcfce28df

Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/sdb2 * 2 9726 78116062+ 5 Extendida
/dev/sdb5 2 9726 78116031 ac Desconocido

I only have one external hard drive (sdc, 200GB) the other 2 are normal sata drives...no raid. And what you said about the partitions its pretty strange. Cause I formated the entire drive, named it ACRONIS SZ, only one partition. Should I format the drive again and try to partition with acronis true image again?

---

### Post by VMC on 2009-06-02
> **X1R1 said:**
> I only have one external hard drive (sdc, 200GB) the other 2 are normal sata drives...no raid. And what you said about the partitions its pretty strange. Cause I formated the entire drive, named it ACRONIS SZ, only one partition. Should I format the drive again and try to partition with acronis true image again?

Ok, Now I know Acronis is on the 'C' drive. I was referring to this:
"Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/sdb2 * 2 9726 78116062+ 5 Extendida
/dev/sdb5 2 9726 78116031 ac Desconocido"

Which is your 'B' drive. No partition 1...wait a minute. Is that drive all extended?

---

### Post by X1R1 on 2009-06-03
> **VMC said:**
> Ok, Now I know Acronis is on the 'C' drive. I was referring to this:
"Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/sdb2 * 2 9726 78116062+ 5 Extendida
/dev/sdb5 2 9726 78116031 ac Desconocido"

Which is your 'B' drive. No partition 1...wait a minute. Is that drive all extended?

I read somewhere that acronis boot was a kind of linux distro, so no idea why > /dev/sdb5 2 9726 78116031 ac Desconocido appears as desconocido "unknown"

I found this "[http://ubuntuforums.org/showthread.php?t=449167]("http://ubuntuforums.org/showthread.php?t=449167")"

I figured I could do that but instead of using the files from the cd use the files from the acronis safe zone, so I go ahead and try but it did not work, maybe its cause im putting the wrong entry in GRUB or the wrong driver or something. This is my current entry for Acronis:

title    Acronis
root    (hd1,0)
kernel    (hd1,0)/boot/acronis/kernel.dat quiet vga=788 ramdisk_size=40000
initrd    (hd1,0)/boot/acronis/initrd

both kernel.dat and initrd are in that dir stated.

No idea what to from now on...

---

### Post by X1R1 on 2009-06-03
more info:

taken from acronis knowledge base, this is exactly what I mean and they say this is the solution. Make GRUB partition primary and active, then activate acronis safe zone in windows

[http://kb.acronis.com/content/1504]("http://kb.acronis.com/content/1504")

In this article states how to make it using fdisk:

[http://www.acronis.com/r/support/en/kb/102/fdisk.txt]("http://www.acronis.com/r/support/en/kb/102/fdisk.txt")

going to try it and come back with results :D

---

### Post by X1R1 on 2009-06-03
Finally I understand whats happening!!! lol

as in the article states for this to work GRUB must be installed on an ACTIVE AND PRIMARY partition. Just noticed that my entire linux hard drive space is logical and XP is primary. thats it!! If I manage to convert my logical partition to primary without losing my configuration settings, then Acronis would be loaded first and if I dont press F11 to launch it, then it would boot GRUB instead of XP (like the acronis knowledge base article says) and problem solved [-o< .

So here is my question:

-Is it possible to change a partition from logical to primary?

-Do I have to convert my XP partition to logical? (not sure if you can have 2 primary partitions on the same hard drive, my guess is no)

We are almost there VMC!! im planning on making a howto If I make this work so that everyone has it! I really appreciate your help so far!

---

### Post by VMC on 2009-06-03
I've never had to do this, but in reading google links, it may be possible. First backup the ubuntu partition before you try it. Will gparted convert on the fly? Maybe not. You might be able to first create another primary then just copy the existing ubuntu partition over to it. Then you would need to alter fstab and menu.lst to the newly created partition, but using ```
sudo blkid
```.

---

### Post by X1R1 on 2009-06-04
> **VMC said:**
> I've never had to do this, but in reading google links, it may be possible. First backup the ubuntu partition before you try it. Will gparted convert on the fly? Maybe not. You might be able to first create another primary then just copy the existing ubuntu partition over to it. Then you would need to alter fstab and menu.lst to the newly created partition, but using ```
sudo blkid
```.

I purchased a new 1TB hard drive to have a complete backup of my pc, once I have it I will try it and come back soon, I ordered it on amazon like 5 days ago so it should arrive very soon. after I backup i will try for sure what you are saying. thanks again for the help!

---

