---
title: "Lost files (and entire disc) during copy"
date: 2006-09-06
forum: Desktop Environments
---

### Post by seppe on 2006-09-06
I was copying a directory (~200GB) on a external usb drive (let's call it *master*) to another usb drive (the *slave*) with rsync:
[INDENT][FONT="monospace"]rsync -rtv /media/usbdisk-1/Backups/ /media/usbdisk/Backups/[/FONT][/INDENT]
During copy I had some warnings from rsync:

[INDENT][FONT="monospace"]file has vanished: "/media/usbdisk-1/Backups/mail_0608.tar.gz"[/FONT][/INDENT]

I tought "Strange...", since I wasn't deleting anything on my primary drive, and checked the master: **all files were vanished!** Not only the files on the directory I was copying, but **the entire disc!**.

How could this had been happened?

I tell you that:
[LIST]
[*]I'm using Ubuntu 6.06 2.6.15-26-686
[*]the master drive has a big (~250GB) FAT32 partition
[*]i bought the master six months ago
[*]the slave drive has a big ext3 partition
[*]i wasn't using the master at all except for copying the directory
[*]a friend of mine had the same problem (on Ubuntu 6.06) copying some files from a 40GB FAT32 disc, he found a corrupted file.
[*]the system didn't froze like the post "[Crash: Copy files from partition to partition]("http://www.ubuntuforums.org/showthread.php?t=250138")"
[/LIST]
Could it be a problem with scratched surface? But, int this case, I think it's not a good idea to loose all files by simply copying them to another place...

Now I'm trying to recover my files with EasyRecov... on Windo... and I've  to admit that I'm not so plased with this... :(

---

### Post by orb9220 on 2006-09-06
I don't believe rsync does not support fat32. You might want to check that out.

---

### Post by seppe on 2006-09-06
No, I think it's not an rsync's fault, I mean: I've used it so much times before with FAT32 partitions...

---

