---
title: "quick hard link question (that i cant find on google)"
date: 2009-01-07
forum: General Help
---

### Post by max_power on 2009-01-07
im using rsync to back up a mounted cifs.

first i make a backup (day0). when the backup runs again, first,  i copy day0 into day1 using cp -al . my understanding is cp -al only makes hard links and doesn't actually copy the files. right? 

when i run this command both folders (day0 & day1) are the same size.

is it only showing the same size but not actually taking up double the space?

Thanks.

---

### Post by Titan8990 on 2009-01-07
I think you will find this article very helpful: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

### Post by max_power on 2009-01-07
> **Titan8990 said:**
> I think you will find this article very helpful: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

:) thats the article im basing my script off. i guess i just need some clarification regarding the size of hard links

---

