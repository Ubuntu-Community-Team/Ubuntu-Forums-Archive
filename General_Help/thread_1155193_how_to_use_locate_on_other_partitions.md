---
title: "how to use locate on other partitions"
date: 2009-05-10
forum: General Help
---

### Post by cholericfun on 2009-05-10
hi

i just realized that using locate to find files will not find anything on my other partitions (ntfs).

i guess it has to do with the database "mlocate.db" not doing anything on those.

so my question is how could i use locate to find files on other partitions - maybe by doing something to mlocate - but what?

thanks in advance

---

### Post by geirha on 2009-05-10
You'll want to edit /etc/updatedb.conf to configure what paths it should or should not index. Read the man-page for a description of the syntax. ```
man updatedb.conf
```

I usually use find instead, it does not use a database, but rather searches through the filesystem(s) directly.

```
find /media/something -name "*.jpg"
```

---

### Post by cholericfun on 2009-05-10
i just find "locate" easier to use... haven't taken my time to figure out how to use "find" effectively e.g. to show the path to a given file

i think its working as should be now
(i guess i'll have to wait until that database gets refreshed)


thanks a lot for the quick reply !

---

### Post by king EZi on 2010-11-18
Hey, you can go edit the /etc/updatedb.conf file and remove "/media" or wherever you mounted the partition

---

