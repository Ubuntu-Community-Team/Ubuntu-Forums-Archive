---
title: "need help with mounting ntfs partition"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Panos on 2005-04-14
Hello everyone

I have almost finished tweaking ubuntu to the extend I want :grin:  But I cannot mount the second partition of my sata drive (sda2) although the first one (sda1) is mounted fine (both partitions are ntfs with WindowsXP in sda1). I get an error message when I give "sudo mount -a" telling me sth about wrong file type, or wrong encoding, and asks me if I' m trying to mount an extended partition instead of a logical volume .... (sorry, I' m at work right now and can't remember the full message).

The entry in my fstab file is exactly the same with the entry for mounting sda1, but with a different mount point of course. Why is it so difficult to mount partitions? I read almost all the relative posts and still can't work it out. The instructions in ubuntuguide just don't work for me. After several attempts I managed to mount sda1 (I tried one of the hundreds suggestions and it worked; I had to use weird options like "defaults,ro,user,uid=1000 0 0").

Moreover, I'm not sure if sda1 is really automounted: it just appears in the panel along with my dvd-roms and the floppy, and I have to click on it and select "mount".

Any help will be really appreciated.

Panos

---

### Post by erkki70 on 2005-04-14
Hi,
Posting your fstab file and precising the mount point you chose is definitely a good thing to do so people can help better. ;-)

Cheers,
Erkki

---

### Post by remmelt on 2005-04-14
My guess is: you are trying to mount the extended volume your logical ones are on.

Try this:
sudo fdisk -l

That will give you a list of all your partitions. sda1 is your first one (the c:\), you will probably see an sda2 one as well, with something like W95 Ext'd (LBA) as the System, and 'f' as the Id. That is kind of like a placeholder for the other partitions with numbers 5 and higher. 
In the early days of computing, people only thought we needed four partitions. This is no longer the case, but the hardware we use is still thinking of it that way. That is why there are 'Extended' partitions. These are placeholders so you can have more than 4 partitions. The partitions with numbers 5 and higher are located INSIDE the extended one, which will have a number like 2, 3 or 4.
You cannot mount an extended partition, only primary ones and logical ones.

So, the partition you are trying to mount will probably be sda5 or so. In the list you are looking at (fdisk -l) you can see it, its Id will be 7 and System is HPFS/NTFS.

The options you list are regular options for an NTFS drive. It's a bit tough to go into the fstab and type stuff up like that, but remember you only have to do it once and it's all set. The 'defaults' option makes the drive get automounted at startup, so I don't think you have to right-click and select mount. Try double-left-clicking!

Good luck!

---

### Post by Panos on 2005-04-15
[QUOTE=remmelt]My guess is: you are trying to mount the extended volume your logical ones are on.

Try this:
sudo fdisk -l

That will give you a list of all your partitions. sda1 is your first one (the c:\), you will probably see an sda2 one as well, with something like W95 Ext'd (LBA) as the System, and 'f' as the Id. That is kind of like a placeholder for the other partitions with numbers 5 and higher. 
In the early days of computing, people only thought we needed four partitions. This is no longer the case, but the hardware we use is still thinking of it that way. That is why there are 'Extended' partitions. These are placeholders so you can have more than 4 partitions. The partitions with numbers 5 and higher are located INSIDE the extended one, which will have a number like 2, 3 or 4.
You cannot mount an extended partition, only primary ones and logical ones.

So, the partition you are trying to mount will probably be sda5 or so. In the list you are looking at (fdisk -l) you can see it, its Id will be 7 and System is HPFS/NTFS.

The options you list are regular options for an NTFS drive. It's a bit tough to go into the fstab and type stuff up like that, but remember you only have to do it once and it's all set. The 'defaults' option makes the drive get automounted at startup, so I don't think you have to right-click and select mount. Try double-left-clicking!

Good luck![/QUOTE]

Thanks for your reply

This is a usefull piece of info you provided, but it only reinforces my theory that Ubuntu complicates things with mounting partitions.

If indeed sda2 represents the extended volume, then why can't I find an sda partition higher than 2 wherever I look?? I mean, when I examine devices in system configuration (I think that's the name of the utility you access through the System menu, sorry again - I'm not in my system right now) I can see my SATA drive with only two partitions, sda1 and sda2. The same applies when I search for the sda partitions in /dev. There are only two sda partitions, sda1 and sda2.

Anyway, what you are saying makes sense to me, and I'm just expressing my frustration for such misleading things. I just think that the OS MUST provide accurate and valid graphical representation of such basic things (please note that I like Ubuntu very much and I will definitely keep it - especially now that the Greek language is fully supported in every application  \\:D/ ) .

Thanks a lot for your help, I'll try it when I get home and let you know.

Panos

---

### Post by Panos on 2005-04-15
[QUOTE=remmelt]My guess is: you are trying to mount the extended volume your logical ones are on.

Try this:
sudo fdisk -l

That will give you a list of all your partitions. sda1 is your first one (the c:\), you will probably see an sda2 one as well, with something like W95 Ext'd (LBA) as the System, and 'f' as the Id. That is kind of like a placeholder for the other partitions with numbers 5 and higher. 
In the early days of computing, people only thought we needed four partitions. This is no longer the case, but the hardware we use is still thinking of it that way. That is why there are 'Extended' partitions. These are placeholders so you can have more than 4 partitions. The partitions with numbers 5 and higher are located INSIDE the extended one, which will have a number like 2, 3 or 4.
You cannot mount an extended partition, only primary ones and logical ones.

So, the partition you are trying to mount will probably be sda5 or so. In the list you are looking at (fdisk -l) you can see it, its Id will be 7 and System is HPFS/NTFS.

The options you list are regular options for an NTFS drive. It's a bit tough to go into the fstab and type stuff up like that, but remember you only have to do it once and it's all set. The 'defaults' option makes the drive get automounted at startup, so I don't think you have to right-click and select mount. Try double-left-clicking!

Good luck![/QUOTE]
 It worked remmelt. Indeed, with fdisk I could see the correct partition which was sda5.

Thanks for your help.

---

### Post by mishranurag on 2005-11-27
I can see the windows partitions in my Disk Manager, but I cannot mount them on my ubuntu system. Can anybody help me there?
I tried xffstab, the graphical utility which I have, to edit /edit/fstab
Anurag

---

### Post by aysiu on 2005-11-27
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

