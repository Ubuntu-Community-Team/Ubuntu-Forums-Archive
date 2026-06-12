---
title: "rsync backs up some files even if not altered"
date: 2009-06-13
forum: General Help
---

### Post by KingNeil on 2009-06-13
I've been using rsync to backup my files to an external hard drive. It's been working very well, except for one thing: there are a few files on my hard drive that get backed up every single time, even if I haven't altered them since the last backup.

These files are ISO files and DVD VOB files, as well as a few JPEG images, and as you can imagine, this takes up a lot of time due to the size of the files.

Do you know why this is happening?

This is the command I run, by the way:

rsync -avz --delete /home/myname /media/nameofhdd

---

### Post by unutbu on 2009-06-13
Let's say /home/myname/big.iso is getting saved here: /media/nameofhdd/home/myname/big.iso

I assume you've recently run ```

rsync -avz --delete /home/myname /media/nameofhdd
```
if not, do so now.

Next run
```

stat /home/myname/big.iso
stat /media/nameofhdd/home/myname/big.iso
```

This will show us some statistics about the files, such as when they were last modified.

Then run ```


rsync -avz --delete /home/myname /media/nameofhdd
stat /home/myname/big.iso
stat /media/nameofhdd/home/myname/big.iso
df -T /home/myname/big.iso
df -T /media/nameofhdd/home/myname/big.iso

```

again and post the output of the above stat and df commands.

---

### Post by KingNeil on 2009-06-13
This is an ISO file from my local drive.

Size: 4091873280	Blocks: 7999760    IO Block: 4096   regular file
Device: 801h/2049d	Inode: 1941505     Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/    myname)   Gid: ( 1000/    myname)
Access: 2009-06-02 18:33:06.000000000 +0100
Modify: 2009-06-02 18:32:37.000000000 +0100
Change: 2009-06-02 18:32:37.000000000 +0100

As you can see, it hasn't been modified since the 2nd of June, with today being the 13th of June. This file shouldn't have been synced.

---

### Post by KingNeil on 2009-06-14
bump

---

