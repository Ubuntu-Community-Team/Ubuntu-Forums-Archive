---
title: "help please"
date: 2007-08-11
forum: Dell  Ubuntu Support
---

### Post by linuxnoob40 on 2007-08-11
here is the story.... i have installed ubuntu dapper onto a dell dimension 2400 howvere i made the mistake of instaling the one for AMD processor and some things like java dont work. so i downloaded xubuntu seeing as this is an older machine it should work better. ok when i try to install and i get to the partition manager i get this error...

the ext3 file system creation in partition #1 of scsi1 (0,0,0) sda failed 


i cannot get past this no matter what i do can someone please tell me what im doing wrong here and help me to correct this :confused:

---

### Post by jimrz on 2007-08-11
> **linuxnoob40 said:**
> here is the story.... i have installed ubuntu dapper onto a dell dimension 2400 howvere i made the mistake of instaling the one for AMD processor and some things like java dont work. so i downloaded xubuntu seeing as this is an older machine it should work better. ok when i try to install and i get to the partition manager i get this error...

the ext3 file system creation in partition #1 of scsi1 (0,0,0) sda failed 


i cannot get past this no matter what i do can someone please tell me what im doing wrong here and help me to correct this :confused:

not sure, but you could try using the G-parted "live" cd, better than the ver the install uses [[COLOR="Sienna"]**_download here_**[/COLOR]]("http://gparted.sourceforge.net/livecd.php"), and format the partition to ext3 then run your install without formatting just use the patirtionioner to mount it as / . while you are at it you might consider creating a separate partition for /home, which is handy for re-installs etc

---

### Post by linuxnoob40 on 2007-08-11
so i use the g parted disk to wipe out the old partitions then try to install using the xubuntu disk if im reading you correctly?

---

### Post by jimrz on 2007-08-11
> **linuxnoob40 said:**
> so i use the g parted disk to wipe out the old partitions then try to install using the xubuntu disk if im reading you correctly?

yep, except that I would also create the new / + /home partitions and format them with the G-parted "live" cd then do the install and only use that partitioner to mount the parttitions

---

### Post by linuxnoob40 on 2007-08-11
couldn't figure out the g parted thing so i used the dapper ubuntu disk to just delete the partition then i shut off the computer and the xubuntu installed with no problems.  the thing that i find strange is instead of showing ide1 it shows as sda1 but its not a serial drive dont know if thats something that i should be concerned over

---

### Post by Blindraven on 2007-08-11
sda1 is SATA or possibly SCSE.

---

