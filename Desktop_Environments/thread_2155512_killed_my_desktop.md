---
title: "killed my desktop"
date: 2013-06-18
forum: Desktop Environments
---

### Post by Timmy0829 on 2013-06-18
I installed compiz and did everything like I found here in the first sticky post.

But when I typed this: 

compiz --replace

and restarted my computer the whole desktop was gone. I could only run programs through the keyboard shortcuts.

Anyway I tryed to set the default settings in compiz, then put back unity but nothing helped. 
So my last great movement was I reinstalled the ubuntu. But I chosed to keep my data and music etc. But now I can only boot in this new system an I see a 387gb hdd instead of the 500 and I cant find my datas.

So please how can I save my datas to an external hdd? Where can I find them? 

Thanks

---

### Post by sudodus on 2013-06-18
1. Please use the file browser and try to mount all available partitions

2. Post the output of the following commands (within code tags)

```
sudo parted -l
```
```
sudo blkid
```
```
df
```

This will make it possible to give detailed advice.

---

### Post by Timmy0829 on 2013-06-18
Here is the output of the first command:
```
  Model: ATA TOSHIBA MK5061GS (scsi)Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  387GB  387GB   primary   ext4            boot
 2      387GB   500GB  113GB   extended
 6      387GB   488GB  100GB   logical   ext4
 5      488GB   500GB  12.6GB  logical   linux-swap(v1)




Model: ATA SanDisk SSD U100 (scsi)
Disk /dev/sdb: 24.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  24.0GB  24.0GB               Basic data partition  hidden




Model: SanDisk Cruzer Edge (scsi)
Disk /dev/sdc: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8004MB  8004MB  primary  fat32        boot, lba

```


the second:

```

 /dev/sda1: UUID="73fbb8a7-e8e6-498a-90da-faf06b85d40a" TYPE="ext4" /dev/sda5: UUID="b2c40813-992a-4234-8ed3-aacf0913f25d" TYPE="swap" 
/dev/sda6: UUID="80899e3f-16ba-4eb3-a416-4d444dd5fa7c" TYPE="ext4" 
/dev/sdc1: LABEL="PENDRIVE" UUID="17FE-264C" TYPE="vfat" 



```

and the third:

```

 Filesystem     1K-blocks      Used Available Use% Mounted on/dev/sda1      372370020 275792648  77662008  79% /
udev             6071724         8   6071716   1% /dev
tmpfs            2431868       948   2430920   1% /run
none                5120         0      5120   0% /run/lock
none             6079664       148   6079516   1% /run/shm
/dev/sdc1        7786256    709358   7076898  10% /media/PENDRIVE



```


I ran the terminal from the old os , where i should reach my data.
I just figured out how to open nautilus from terminal, it worked fine, but I cant see anything. Just the home folder, but theres nothing in it. And I tried to open trash but its not allowed.

Thanks

---

### Post by grahammechanical on 2013-06-18
Look at the output from that first command and add

387GB primary + 113GB Extended = 500GB  or

387GB primary + 100Gb logical + 12.6GB swap = 499.6GB = near enough as makes no difference. Your 500GB hard disk is still there. It has been partitioned into a 387GB primary partition and a 100GB logical partition and a 12.6GB logical/swap partition both encased in a 113GB extened partition. Where the data is I cannot say.

Regards.

---

### Post by Timmy0829 on 2013-06-18
Okay. But how come I cant reach my data from the old system nor the new one. It has to be somewhere. And Im pretty sure its in the old one. But I cant see anything through nautilus

---

### Post by sudodus on 2013-06-18
I guess you should be looking into /dev/sda6, the second ext4 partition on the first drive. Can you mount it and browse it with Nautilus. You may need root privileges

```
gksu nautilus
```

But the SSD drive looks strange. It is encrypted?

---

### Post by Timmy0829 on 2013-06-18
I cant make a screenshot... If I type this then nautilus opens up but I can see the Home folder with the desktop folder but its totally empty no downloads nothing. I can see the system. and the pendrive, what is plugged in.

No the SSD i think its not working. I think ubuntu not recognise it. I didnt do anything with it.

And I tried to attach a pic and then I COULD SEE the data, the downloads folder and everything. But still nautilus doesnt show anything.

---

### Post by Timmy0829 on 2013-06-18
Victory :D

The solution. I was searching for an artist in the nautilus and it found it :D and I opened the folder and I could see my docs, my music folder and everything. Soo now Im copying everything to a external hdd and reinstall the whole system. 

And I will never ever install compiz again.

---

