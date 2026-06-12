---
title: "Backing up an entire partition"
date: 2009-02-16
forum: General Help
---

### Post by pauligit on 2009-02-16
I need to back up an entire NTFS partition. Is there any specific tool for such task? There I have installed Windows, and of 60 Gigs, only 4 are used. My intention is to create a copy of it so as to avoid having to install Windows plus other useful software from scratch the next time I might need to do so.
For some reason I think dd wouldn't be appropriate, since I believe it would consume another 60 gigs more to store the image...
Cheers,
Pauligit

---

### Post by hyper_ch on 2009-02-16
well, with dd you can backup the whole partition but that will also backup non-written stuff...

for windows otherwise you could use norton ghost - that would backup only the written stuff

---

### Post by Phlee on 2009-02-16
I've used Norton Ghost pleant of times.   In a Unix world I think you can also use Mondo for NTFS Don't quote me.

---

### Post by bodhi.zazen on 2009-02-16
You can image the windows partition with partimage as well.

There are several tools you can use in fact ;)

---

### Post by kaibob on 2009-02-16
Have a look at Clonezillla

[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by handy on 2009-02-17
There is some useful info' here too:

*_[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)_*

---

### Post by pauligit on 2009-02-17
I'll check out those links and then leave some feedback. Thanx!

---

