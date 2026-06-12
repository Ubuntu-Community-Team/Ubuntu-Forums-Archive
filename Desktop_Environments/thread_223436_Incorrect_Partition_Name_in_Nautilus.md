---
title: "Incorrect Partition Name in Nautilus"
date: 2006-07-26
forum: Desktop Environments
---

### Post by noynac on 2006-07-26
This is an issue that I previously raised, but I can't find the earlier thread. I apologize for raising the same issue twice. 

When I first installed Ubuntu Linux, I created a FAT32 partition with the name "store" on my computer's hard drive. After a few days, Nautilus began showing the name of this directory as PNG with a box that contains the characters 001A below it. 

A week or so later, I did a clean install, and I thought the directory-naming issue was behind me. Now it's back, and I don't know what to do about it.

I found other Ubuntu users who were having a similar problem. For example:

[http://ubuntuforums.org/showthread.php?t=184382](http://ubuntuforums.org/showthread.php?t=184382)

One user posted a screen shot of this problem at:

[http://ubuntuforums.org/attachment.php?attachmentid=10257&d=1148950204](http://ubuntuforums.org/attachment.php?attachmentid=10257&d=1148950204)

BTW, the line from my fstab file is:

/dev/sda4 /media/store vfat defaults,utf8,umask=007,gid=46 0 1

Does anyone know how to fix this? 

Thanks for the help.

Noynac

---

### Post by philippe_carlo on 2006-07-26
Change that fstab line into
```

/dev/sda4 /media/store vfat defaults,umask=007,user 0 0

```

---

### Post by tturrisi on 2006-07-26
I had a similar issue w/ my fat32 partition & it being give a numerical name.  I booted to xp and gave the partition a name and when back in ubuntu the name I had given it "FILES" was now in use by nautilus.

---

### Post by noynac on 2006-07-26
Thanks philippe_carlo and tturrisi for responding to my posting. I tried renaming the partition in Windows and that fixed the problem. It's a solution that never would have occurred to me. 

noynac

---

