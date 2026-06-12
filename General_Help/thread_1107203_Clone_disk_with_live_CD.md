---
title: "Clone disk with live CD?"
date: 2009-03-26
forum: General Help
---

### Post by W. Irving on 2009-03-26
I have been asked to 'upgrade' a laptop from Vista to XP and thought I could probably use the Ubuntu live CD to create a copy of the drive before I install XP. I suppose I could use Clonezilla, but I am already familiar/'fluent' with Ubuntu. The copy will have to be saved on an external USB drive (NTFS partition), as a file.

Would the following procedure be a good idea?

[LIST=1]
[*]Boot live CD
[*]Mount external USB disk (sda1)
[*]Demo Ubuntu to owner (wouldn't you rather...? ;) )
[*]dd if=/dev/hda of=/dev/sda1/backup.img
[/LIST]

I obviously want the MBR and any recovery partitions on hda so that if anything goes wrong, I'll just..

[LIST=1]
[*]Boot live CD
[*]Mount external USB disk (sda1)
[*]dd if=/dev/sda1/backup.img of=/dev/hda
[/LIST]

The drive on the laptop is a SATA drive, does that mean it will appear as /dev/sda instead? Does the Ubuntu live CD come with ntfs-3g?

How about it?

---

### Post by damis648 on 2009-03-26
> **W. Irving said:**
> 
[LIST=1]
[*]Boot live CD
[*]Mount external USB disk (sda1)
[*]Demo Ubuntu to owner (wouldn't you rather...? ;) )
[*]dd if=/dev/hda of=/dev/sda1/backup.img
[/LIST]
...snip...
[LIST=1]
[*]Boot live CD
[*]Mount external USB disk (sda1)
[*]dd if=/dev/sda1/backup.img of=/dev/hda
[/LIST]


It doesn't work like that. What you need to do is
1. Boot LiveCD
2. Don't mount the Vista partition, but DO mount your backup drive, just plug it in and wait for the desktop icon.
3. Run: (note the sudo)
```
sudo dd if=/dev/sda of=/media/external_diskname/backup.img
```
, Replacing external_diskname with the name of the partition on the external disk (will show on desktop, but if it says 'XX GB Media' then it should be known simply as 'disk') And that is all. To restore,
```
sudo dd if=/media/external_diskname/backup.img of=/dev/sda
```
Like you said, his disk will be sda if it is SATA in AHCI mode, but hda if it is a SATA in legacy mode or IDE. I make these changes because /dev/sda or whatever is not a directory, you cannot copy a file to it. It is a block device, THE device. You have to mount it in order to copy to it, which is why the /media.

---

### Post by W. Irving on 2009-03-26
> **damis648 said:**
> It doesn't work like that. What you need to do is
1. Boot LiveCD
2. Don't mount the Vista partition, but DO mount your backup drive, just plug it in and wait for the desktop icon.


That is what I said though.. Mount external USB disk (1st partition). No point mounting the Vista partition, as I want the whole drive. Forgot about the mount point in /media.. fusebox really does speak ntfs out of the box?

So I assume by your reply that there is no flaw in my method that will only become apparent once I'm there at the machine with my sister breathing down my neck, inquiring every 5 mins when I'll be done.

---

### Post by damis648 on 2009-03-26
> **W. Irving said:**
> That is what I said though.. Mount external USB disk (1st partition). No point mounting the Vista partition, as I want the whole drive. Forgot about the mount point in /media.. fusebox really does speak ntfs out of the box?

So I assume by your reply that there is no flaw in my method that will only become apparent once I'm there at the machine with my sister breathing down my neck, inquiring every 5 mins when I'll be done.

There is no problem, but you need to recognize that you cant copy to /dev/sda or anything like that, you have to copy to the mountpoint.:popcorn:

---

### Post by stchman on 2009-03-26
> **W. Irving said:**
> I have been asked to 'upgrade' a laptop from Vista to XP and thought I could probably use the Ubuntu live CD to create a copy of the drive before I install XP. I suppose I could use Clonezilla, but I am already familiar/'fluent' with Ubuntu. The copy will have to be saved on an external USB drive (NTFS partition), as a file.

Would the following procedure be a good idea?

[LIST=1]
[*]Boot live CD
[*]Mount external USB disk (sda1)
[*]Demo Ubuntu to owner (wouldn't you rather...? ;) )
[*]dd if=/dev/hda of=/dev/sda1/backup.img
[/LIST]

I obviously want the MBR and any recovery partitions on hda so that if anything goes wrong, I'll just..

[LIST=1]
[*]Boot live CD
[*]Mount external USB disk (sda1)
[*]dd if=/dev/sda1/backup.img of=/dev/hda
[/LIST]

The drive on the laptop is a SATA drive, does that mean it will appear as /dev/sda instead? Does the Ubuntu live CD come with ntfs-3g?

How about it?

Yes, use the LiveCD.  When you boot into the LiveCD plug in the external hdd.  You will then bring up Gnome Partition Editor.

Make sure the external hdd is unallocated space.

After that right mouse click on the Vista partition and select Copy.  Go to the extrernal hdd and select Paste.  Pretty easy.

---

### Post by damis648 on 2009-03-26
> **stchman said:**
> Yes, use the LiveCD.  When you boot into the LiveCD plug in the external hdd.  You will then bring up Gnome Partition Editor.

Make sure the external hdd is unallocated space.

After that right mouse click on the Vista partition and select Copy.  Go to the extrernal hdd and select Paste.  Pretty easy.

That is not what the OP wanted to do, he wanted to make an image file. Not re-image his external drive.

---

### Post by W. Irving on 2009-03-26
> **damis648 said:**
> That is not what the OP wanted to do, he wanted to make an image file. Not re-image his external drive.

Yup! Thanx for the responses! 8)

---

### Post by W. Irving on 2009-03-27
A follow up.. is there any way I could read the contents of this file I have created from the hard drive? It contains two partitions, but I'm only interested in the second. Could I mount this partition in any way?

---

