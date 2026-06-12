---
title: "How do I format a partition in NTFS from linux?"
date: 2005-12-01
forum: Desktop Environments
---

### Post by megamania on 2005-12-01
I need to format a partition in NTFS in order to restore a win xp system backup that I need for a specific task.

I thought gparted would do, but ntfs is marked as "red" (not available). I guess there's something I'm missing - I searched for ntfs libraries or things like that, but have not succeeded.

Any help would be appreciated. I have no Win installed at home, so I can't (and don't *want to*) use it - I'd like to learn how to do this with Linux.

---

### Post by tagg3rx on 2005-12-01
I'll start by saying I dont know....

But if you have a partition set aside just pop in the windows cd and let the installer format it.

That should work

---

### Post by aysiu on 2005-12-01
Is the problem that you have a Windows XP restore disk or installer disk, and it won't recognize an Ext3 or blank partition? If so, create a FAT32 partition, and the installer will ask if you want to convert it to NTFS before installing Windows.

---

### Post by megamania on 2005-12-01
[QUOTE=aysiu]Is the problem that you have a Windows XP restore disk or installer disk, and it won't recognize an Ext3 or blank partition? If so, create a FAT32 partition, and the installer will ask if you want to convert it to NTFS before installing Windows.[/QUOTE]

Thanks Aysiu - that's part of the problem, but:

- my cd player is giving me problems with the xp cd
- the installer will start installing windows immediately, and I don't want that - I have to restore a backup to the ntfs partition.

Can't I format it directly from Ubuntu?

---

### Post by aysiu on 2005-12-01
GParted and QTParted are a bit limited in their capabilities. I would use Mandriva's [DiskDrake](http://qa.mandriva.com/twiki/bin/view/Main/DiskDrake).

Download the first installer CD of Mandriva.
Use the installer until you get to the DiskDrake part. Use DiskDrake to create your NTFS partition, then force a reboot.

---

### Post by az on 2005-12-01
You need ntfsprogs

[http://packages.ubuntu.com/breezy/otherosfs/ntfsprogs](http://packages.ubuntu.com/breezy/otherosfs/ntfsprogs)

Qtparted should use it to make an ntfs filesystem:

"mkntfs - Format a partition with a NTFS filesystem. "


ntfsprogs is a reccommends for gparted, but not a dependancy.  You have to install yourself - that's why you don't have it installed after installing gparted.
[http://packages.ubuntu.com/breezy/gnome/gparted](http://packages.ubuntu.com/breezy/gnome/gparted)

---

### Post by Hairy_Palms on 2005-12-01
hmmm i wonder if its possible to compile diskdrake in ubuntu, does anyone know where i can find the source?

---

### Post by az on 2005-12-01
What can diskdrake do that gparted cannot?

They are both frontends to parted and other filesystem utilities.

---

### Post by crispingatiesa on 2005-12-01
Maybe the least cumbersome way to go is to use qparted after booting knopix, Of course after re-formating and /or reinstalling XP in the  partition grub will be lost so, you better be ready for some messing around with it

---

### Post by aysiu on 2005-12-01
[QUOTE=azz]What can diskdrake do that gparted cannot?

They are both frontends to parted and other filesystem utilities.[/QUOTE] I don't know. I just know from personal (i.e., anecdotal--not scientific or technologically minded) experience that DiskDrake has never let me down for partitioning. It can handle any partiiton type and well. There are never any greyed out options. It just does its job.

---

### Post by megamania on 2005-12-01
[QUOTE=azz]You need ntfsprogs

Qtparted should use it to make an ntfs filesystem:

"mkntfs - Format a partition with a NTFS filesystem. "

ntfsprogs is a reccommends for gparted, but not a dependancy.  You have to [/QUOTE]

As usual, the speed and quality of responses in this forum are amazing! :-)

I had seen ntfsprogs (and other packets) by doing a "ntfs" search in synaptic, but I wasn't sure which was the right one.
Now I just installed it and NTFS is [COLOR="Green"]green[/COLOR]. :-)

I'm going to try it right away - thank you everybody (and especially Azz, this time!).

---

### Post by Hairy_Palms on 2005-12-01
i use diskdrake as my partitioner by botting mandrake 10.1 first cd, knoppix with qtparted crashed on me whilst formatting the ubuntu livecd has an irritating habit of using the hard disks swap partition which prevents me doing anything to that hard disk. gParted rarely works for me, it says its doing it then when finished nothing has changed except the occasional hard disk corruption causing me to need to fsck my system

---

### Post by Irony on 2005-12-01
Try;

*sudo cfdisk*

Toggle to the partition then move to the type section and format as NTFS (no. 07).

Note that you should unmount the partition first (if its mounted), you can do this from gparted.

---

