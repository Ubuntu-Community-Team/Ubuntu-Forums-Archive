---
title: "Making a mounted NTFS drive visible in Computer?"
date: 2005-03-30
forum: Desktop Environments
---

### Post by Michael on 2005-03-30
Hi all, I think the topic pretty much sums it up.

I got these two lines in /etc/fstab:

```
/dev/sda1	/mnt/Windows	ntfs	umask=0222,nls=utf8	0	0
/dev/sda2	/mnt/Data	ntfs	umask=0222,nls=utf8	0	0
```

How can I have icons for these drives inside Computer?

And another thing - how can I make writing possible for *all users* for any of the drives? Just add "rw" to the options?

Thanks,
Michael.

---

### Post by lorap on 2005-03-30
hi!
all you've to do is to create those directories not in /mnt directory,but in /media!
everything created in media directory appears in DISKS.
have a nice day!
pavel

---

### Post by Michael on 2005-03-30
Cool! Thanks :)

---

### Post by lorap on 2005-03-30
did it help friend?
if it did i'm very glad could make someone smile!
pavel

---

### Post by Bicet on 2005-03-30
For me it doesn't work :(

---

### Post by c_dog on 2005-03-30
[QUOTE=Michael]Hi all, I think the topic pretty much sums it up.


And another thing - how can I make writing possible for *all users* for any of the drives? Just add "rw" to the options?

Thanks,
Michael.[/QUOTE]

You won't be able to give the NTFS parttions write access. Linux only supports reads on NTFS.  Microsoft has kept a pretty tight lip on the NTFS specification. The Windoze partitions would need to be set up in FAT32 for read-write access

---

### Post by Michael on 2005-03-30
Well, it worked at the beginning, but after a restart the icons are gone...

---

### Post by Julius on 2005-03-30
It's a bug :P more info here
[http://ubuntuforums.org/showthread.php?t=21508&page=2&pp=10](http://ubuntuforums.org/showthread.php?t=21508&page=2&pp=10)

Edit: I didn't know the nls=utf8 thingy. I can now see the all the characters!!!
 =D>  =D>  =D>

---

### Post by chronusdark on 2005-04-01
add the option users to your fstab..i had this issue back in my fedora core days

---

