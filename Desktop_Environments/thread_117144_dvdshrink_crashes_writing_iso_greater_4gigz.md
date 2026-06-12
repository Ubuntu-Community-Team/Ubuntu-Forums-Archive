---
title: "dvdshrink crashes writing iso greater 4gigz"
date: 2006-01-14
forum: Desktop Environments
---

### Post by fishbroetchn on 2006-01-14
hi ubuntu-forums, 

i read a lot here, learned a lot and try to give some of that back, but here is a problem i cant figure out.

i installed dvd-shrink with wine and it runs fine, accept that it does not make a iso-file greater than 4 gb. Then it crashes. I tried shrinking the iso up to 3.8 gigz and it works fine. 

Is there a parameter in wine i set wrong or which needs to be reset??

thx a lot fishbroetchn

---

### Post by fishbroetchn on 2006-01-23
i figured it out. i tried to write the iso file on a fat32 partition. that is not possible due fat32 not being able to handle files greater then 4 gigz.

---

