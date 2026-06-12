---
title: "Problem when I try to delete dicectory"
date: 2012-03-30
forum: Desktop Environments
---

### Post by forsubhi on 2012-03-30
I use dolphin file Manager and I face this problem when trying to delete 40.buildtrees directory 

Could not delete file /media/sda5/sphinx/tutorial/digit2/logdir/40.buildtrees/digit.buildtree.&#65533;.0.log.

any help !

---

### Post by zombifier25 on 2012-03-30
Try deleting as root.

---

### Post by Zorael on 2012-03-31
> **forsubhi said:**
> Could not delete file /media/sda5/sphinx/tutorial/digit2/logdir/40.buildtrees/digit.buildtree.&#65533;.0.log.

I hate to suggest it, but have you tried deleting it from a terminal? If nothing else it may be more descriptive about the error.
```
$ cd /media/sda5/sphinx/tutorial/digit2/logdir/40.buildtrees
$ rm digit.buildtree.     *<hit TAB twice>*
```
It may be the character encoding mucking things up, or it may be a permissions thing.

---

### Post by forsubhi on 2012-03-31
I try what you say 
and this is the result

[IMG]http://img6.imagebanana.com/img/liapg9bw/Selection_003.png[/IMG]

---

### Post by jacksaff on 2012-03-31
Try replacing the ? character with a * which should match all of the files you want. ie rm digit.buildtree.*.log
If you have other files in that directory with similar names that you want to keep use the rm -i instead of just rm so that you can confirm each separately.

---

### Post by forsubhi on 2012-04-01
rm digit.buildtree.*.log  work for me 
but I wondered why the dolphin cannot delete the files and this command can ?

---

