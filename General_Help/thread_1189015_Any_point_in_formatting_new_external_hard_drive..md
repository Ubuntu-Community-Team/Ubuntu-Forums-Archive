---
title: "Any point in formatting new external hard drive."
date: 2009-06-16
forum: General Help
---

### Post by nothingspecial on 2009-06-16
I have a new hard drive.

It is never likely to be plugged into a windows machine.

Shall I make it ext3 before I put anything on it?

---

### Post by Therion on 2009-06-16
Well if it's a primary drive, meaning it will house your OS, formatting will take place as part of the install.  If you're going to use it as a slave drive for backups or data only then you'll need to partition/format it with a specific filesystem (e.g. NTFS, Ext3/4, whatever).

---

### Post by sedawk on 2009-06-16
I recommend to use ext3 and to set the inode size to 128 (bytes).
There is a windows driver that can read ext2/ext3 as long as
the inode size is 128:
[http://www.fs-driver.org/relnotes.html](http://www.fs-driver.org/relnotes.html)

(The default has changed recently from 128 bytes to 256 bytes).
(May be the windows driver will be updated, but for now 1.11 does not
 support inodes with 256 bytes).

---

### Post by nothingspecial on 2009-06-16
> Well if it's a primary drive, meaning it will house your OS, formatting will take place as part of the install. If you're going to use it as a slave drive for backups or data only then you'll need to partition/format it with a specific filesystem (e.g. NTFS, Ext3/4, whatever)

Nope, its just for data. One partition. Music, Vids the like.

I was just wondering, since my ubuntu box is ext3 weather there would be any noticable performance difference if the drive was too.

And if there was was less chance of file system corruption.
 
If the difference is negligable, I`ll leave it as it is.

---

### Post by nothingspecial on 2009-06-16
> **sedawk said:**
> I recommend to use ext3 and to set the inode size to 128 (bytes).
There is a windows driver that can read ext2/ext3 as long as
the inode size is 128:
[http://www.fs-driver.org/relnotes.html](http://www.fs-driver.org/relnotes.html)

(The default has changed recently from 128 bytes to 256 bytes).
(May be the windows driver will be updated, but for now 1.11 does not
 support inodes with 256 bytes).

I`m never likely to use windows, so the byte bit doesn`t matter.

---

### Post by sedawk on 2009-06-16
Let's assume you just downloaded the 27 MB Plants vs. Zombies Demo
(which works perfectly under Linux with Wine !) and
you want to show it to a (windows) friend (with no DSL) so you
bring your disk ... Bad luck!

Unless you don't forget to bring your Ubuntu LiveCD too ;-)

---

### Post by Therion on 2009-06-16
> **nothingspecial said:**
> Nope, its just for data. One partition. Music, Vids the like.
Yup, got one of those myself.  If the drive in question is already in use no point in RE-formatting it...  Unless you're into that sort of thing.  If it's right out of it's box and it's stinky mylar wrapper I'd format it NTFS for Windows compatibility (my slave is also my "bug out" drive so I don't count on being able to hook up with a Linux PC in an emergency sort of situation), but that's up to you.  You're not going to see any *practical* difference in access time either way (NTFS vs. Ext3/4).

Notice I said "practical"... So if someone out there who's reading this is about to post about how much faster Ext4 is over NTFS on some synthetic benchmark... 

DON'T.  Just. Don't.  Do it.

---

### Post by nothingspecial on 2009-06-16
Ok. I`ll start loading it now.

Cheers

---

