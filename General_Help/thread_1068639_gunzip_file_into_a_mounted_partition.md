---
title: "gunzip file into a mounted partition"
date: 2009-02-13
forum: General Help
---

### Post by martin_legion on 2009-02-13
Hello
I hace this huge file.img.gz in /media/backup and need to gunzip-it in /media/hd2 (another hd mounted there).
The file is too big to uncompress it in the same partition, so I need gunzip to put the uncompressed file on the other drive.
Is that possible??

Thanks

---

### Post by heindsight on 2009-02-13
Yes, just do
```
cd /media/hd2
gunzip /media/backup/file.img.gz
```

---

### Post by martin_legion on 2009-02-13
> **heindsight said:**
> Yes, just do
```
cd /media/hd2
gunzip /media/backup/file.img.gz
```

That started to uncompress the file in the same directory as the file.
I've found this solution:
gunzip < /somedir/origfile.img.gz > /destdir/destfile.img

---

### Post by heindsight on 2009-02-13
> **martin_legion said:**
> That started to uncompress the file in the same directory as the file.

Sorry, my bad. I forgot gunzip does that.

you can also do:
```
gunzip -c /somedir/origfile.gz > /destdir/destfile
```

---

