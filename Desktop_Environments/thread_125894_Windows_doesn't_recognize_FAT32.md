---
title: "Windows doesn't recognize FAT32?"
date: 2006-02-05
forum: Desktop Environments
---

### Post by tblehr on 2006-02-05
Ok, so I have an external HDD on USB.  I partitioned it with GParted in the FAT32 format cause I wanted to share it between Ubuntu and Windows XP.  Well it works great from Ubuntu's end, but as always, Windows falls short.  I looked under admin tools->disk managment (can't remember exactly the path) and it says FAT32 Unknown format.  I thought FAT32 was native to Windows.

Does anyone know why this is happening?  I'd appreciate it! :)

~Terrence~

---

### Post by ivan.virtuale on 2006-02-05
[QUOTE=tblehr]Ok, so I have an external HDD on USB.  I partitioned it with GParted in the FAT32 format cause I wanted to share it between Ubuntu and Windows XP.  Well it works great from Ubuntu's end, but as always, Windows falls short.  I looked under admin tools->disk managment (can't remember exactly the path) and it says FAT32 Unknown format.  I thought FAT32 was native to Windows.

Does anyone know why this is happening?  I'd appreciate it! :)

~Terrence~[/QUOTE]

It's happen to me some weeks ago!!
I've resolved it using Windows to partition and format ;I saw that Windows doesn't use alla the space for the partition, GParted used ALL the space!!
This is the different...

Ivan

---

### Post by tblehr on 2006-02-05
Thanks for the quick reply! :)  There's a prob with that, is I tryed to format with Windows, but it would only let me choose NTFS.  Is there a program I should download and use in windows to make it FAT32?

---

### Post by ESPOiG on 2006-02-05
partition magic

---

### Post by tblehr on 2006-02-05
[QUOTE=ESPOiG]partition magic[/QUOTE]

Thanks!  I'll give it a go!

---

### Post by manicka on 2006-02-05
There is a size limit with fat32 drives (32gb). I'd suggest using gparted to make some smaller fat32 partitions then reformatting them again in windows. With smaller partition sizes, fat 32 should be available as an option when you go to format them in windows.

Partition magic will also do this job, but is a more expensive option

---

### Post by tblehr on 2006-02-05
[QUOTE=manicka]There is a size limit with fat32 drives (32gb). I'd suggest using gparted to make some smaller fat32 partitions then reformatting them again in windows. With smaller partition sizes, fat 32 should be available as an option when you go to format them in windows.

Partition magic will also do this job, but is a more expensive option[/QUOTE]

Yeah, I checked out partition magic and it was gonna cost me money!  I'll try making smaller partitions.  That makes since, with the size limit.

Thanks for the advise! :)

---

### Post by plors on 2006-02-05
the max size of a fat32 filesystem is around 2 TiB. The problem is in winXP which can only format fat32 up to 32 GiB. However, once created (e.g. using gparted) winXP should be perfectly able to handle bigger filesystems.

> While FAT32 partitions this large work fine once created, some software won't allow creation of FAT32 partitions larger than 32GiB. This includes, notoriously, the Windows XP installation program.

[http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

---

### Post by Irony on 2006-02-05
Use;

*sudo cfdisk*

To format your partition, gparted is probably using the wrong FAT32 type, you want Id 0C FAT32 which you can select with cfdisk

---

### Post by tblehr on 2006-02-05
[QUOTE=Irony]Use;

*sudo cfdisk*

To format your partition, gparted is probably using the wrong FAT32 type, you want Id 0C FAT32 which you can select with cfdisk[/QUOTE]

It worked!:-D Thanks everybody for all your help!  I appreciate it!  I'm becoming more attached to Ubuntu every time I use it! :)

~Terrence~

---

