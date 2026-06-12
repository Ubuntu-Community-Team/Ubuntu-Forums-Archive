---
title: "Help Viewing Partition After Ubuntu changes"
date: 2009-04-27
forum: General Help
---

### Post by nzkronic on 2009-04-27
Hi, 

I have a 80GB NTFS Media Partition (sda2) which I created in vista to allow me to access my media on both Ubuntu and Vista.

This worked fine in both OS's where I had the Media NTFS drive automatically mounted with this entry in fstab file. 

/dev/sda2 /media/Media ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 

This worked fine on both drives untill I added a fstab entry to auto mount my actual vista (C: ) in ubuntu as well:


/dev/sda3 /media/Vista ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

After doing this I can no longer access my Media (sda2) drive through vista as it says it is corrupt, disk management tool in vista sees the drive as (RAW) rather than NTFS.


After writing this post I think it may have something to do with the ID of the drive, here is the output of:

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8e74969

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+  83  Linux
/dev/sda2            7913       18701    86662642+   7  HPFS/NTFS
/dev/sda3   *        2551        7912    43070265    7  HPFS/NTFS
/dev/sda4           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris




Thanks in advance for any help

---

### Post by coffeecat on 2009-04-27
This seems to be a recurring problem, although I'm mystified as to how Vista decided your Media partition was raw only after you automounted the Vista C: partition.

Anyway, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1122108"), especially the links I posted in post #10. Nothing resolved on that thread unfortunately, but you might find something on the ntfs-3g forums. The only suggestion I have is to backup all your data from your Media partition and then reformat it in Vista. It's a bit much, though, when we have to use Linux to backup from a Microsoft filesystem. :roll: I'd also suggest removing your fstab Vista partition mount line, because the next thing to happen will be that Vista will decide it's sitting on a RAW filesystem and refuse to boot up.

Out of interest, is your Vista 32-bit or 64-bit? The reason I ask is that some threads on the ntfs-3g forum suggest that this might be a Vista 64-bit issue. It's obviously a problem, but you'd think it would happen more frequently and occur on this forum more often if it affected 32-bit Vista. My other reason is that I've just replaced XP with Vista on my desktop and bought myself a new Vista laptop. Both machines have Ubuntu Jaunty and a shared NTFS partition. This RAW issue hasn't happened to me yet but I feel as though I'm sitting on a time bomb. :(

One last suggestion. I was interested in your NTFS fstab lines. If you let the Ubuntu installer set up a mountpoint for a pre-exisiting NTFS partition, it uses the line...

```
device    mountpoint     ntfs        defaults,nls=utf8,umask=007,gid=46    0 1
```... which works well enough, except that there's a bug which means that if you copy a file from an ext3 partition to the mounted NTFS partition, it changes the date/time stamp. Copy the other way and you're OK. I found out, more or less by accident, that if I use....

```
device    mountpoint     ntfs        defaults    0 1
```... (which couldn't be simpler) everything still works fine and date/time is preserved on copy. You might want to check and see if date/time is preserved with your line. Also, don't worry that the filesystem reference is 'ntfs', not 'ntfs-3g'. Apparently Ubuntu will use the same fuse driver with both.

**Edit:** I just noticed this:

> /dev/sda3 /media/Vista ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

What's that '37' for in that line? With the 37, you've got 7 fields, making it an invalid fstab line.

---

### Post by nzkronic on 2009-04-27
Thanks for the reply coffeecat, yes I failed to mention that I am running vista 64bit and using Jaunty with the Ext4 filesystem.

As for using the "37" in the fstab line, I just used an example from this thread: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Not sure what it actually means but now confused because I am sure I used the same line for both my media and vista parition entries only changing the mount point and dev to use??

Anyway I will have a read of the links you provided and hopefully may find something that will work. I did try using the simplifed defaults line you provided for fstab file and just did the same as the previous line.

I have a finally brought a 500GB external hdd so I can finally backup data when this arrives. Will try formatting media in vista again and getting it sorted.

Still really confused why this seemed to work perfectly mounting my media drive in ubuntu and having it also working fine in vista, only to be changed to RAW after mounting the actual vista partition in Ubuntu. 


Thanks.

---

### Post by coffeecat on 2009-04-27
Yes, interesting that you're using 64-bit. It could very well be a problem with 64-bit Vista only, so this might bite you again. That is, until the ntfs-3g people work out what's going on. Just as well both my Vistas are 32-bit then. :p

I had a look in that thread. Yes, the lines with 37 came from the OP, but well down. But it looks like a typo. Go a few lines up and you see...

> /dev/disk/by-id/usb-IOMEGA_ZIP_250_059B00301400B0F1-part4 /mnt/zip vfat users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0

/dev/hda1  /mnt/windows  ntfs-3g  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1  37   0  0When typing out the second line, the OP probably hit the spacebar by accident and didn't notice and then copied and pasted for the lines below. Valid values for the 5th field (which the 37 is occupying) are 0 and 1, so I guess it was parsed as either 0 or 1, the next 0 was parsed for the sixth field, and the final 0 ignored. There's probably some error messages deep in your logs somewhere. 

> **nzkronic said:**
> Still really confused why this seemed to work perfectly mounting my media drive in ubuntu and having it also working fine in vista, only to be changed to RAW after mounting the actual vista partition in Ubuntu.

Weird, isn't it? I think we can sum it up in one word: Vista! :wink:

**Edit:** just noticed. The link right at the beginning of the OP in that thread - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) - doesn't have the typo. One for the bookmarks I think. I remember coming across both the thread and the wiki link some time ago, but forgot to bookmark them at the time.

---

### Post by nzkronic on 2009-04-27
Yeah vista seems to be be a bit of a pain, my laptop originally came with vista 32 bit which ran soooo slow on startup. Switched to Ubuntu and thought I would never go back to windows, wanted windows for gaming and couldnt install XP because there were no Graphics drivers available for xp. Ended up getting 64bit vista and the performance increased significantly and runs smoothly.

Anyway is it worth formatting this Media drive as fat32, not too sure what the difference is between the NTFS and Fat32 but I figured it would solve my problem untill the ntfs 3g people work it out, or even a EXT3 file system and using some windows workaround to read it in vista?

---

### Post by coffeecat on 2009-04-27
Fat32 works well enough but you've got the 4GB filesize limit to think about. If your media partition contains large media files or DVD ISOs, that might be a problem. And, obviously, because it's not a journalled filesystem, you need to be extra-vigilant with backups.

I'm a bit out of date with Windows drivers for ext3 partitions. There was quite a good one for XP which was read/write but which treated an ext3 partition as ext2, so it didn't deal with the journalling. Which theoretically made it less reliable, or less safe. Whether someone's come up with a reliable ext3 read/write driver, and whether they've come up with one for Vista I don't know. Either way, you have to choose between Linux messing in a Microsoft filesystem or Windows messing in a Linux filesystem. Bit of a lose-lose situation really.

---

