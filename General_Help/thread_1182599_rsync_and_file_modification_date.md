---
title: "rsync and file modification date"
date: 2009-06-09
forum: General Help
---

### Post by Gingalone on 2009-06-09
Hi everybody,

it would be really useful to me (and I bet to many others) if it would be possible to make a backup copy of files with rsync specifying a file modification date interval (e.g. every night I'd like to copy all files which have been modified that day).
I had a look on the BIG man rsync file and couldn't find some obvious way... But I am just a few months newcomer to Linux/Ubuntu....
Thanks for hints!

---

### Post by Legace on 2009-06-09
> **Gingalone said:**
> Hi everybody,

it would be really useful to me (and I bet to many others) if it would be possible to make a backup copy of files with rsync specifying a file modification date interval (e.g. every night I'd like to copy all files which have been modified that day).
I had a look on the BIG man rsync file and couldn't find some obvious way... But I am just a few months newcomer to Linux/Ubuntu....
Thanks for hints!

But why'd you want to do that?
Rsync automatically copies ONLY files that have been modified. For example:

You can 5 files:
A.txt
B.txt
C.txt
D.txt
E.txt

You use rsync to copy them to another location.
Rsync will copy them into a new directory like this:
A.txt
B.txt
C.txt
D.txt
E.txt

One day, you decide to edit B.txt. Then you run rsync. Rsync will **only** copy the modfied B.txt, because it "knows" the others have not been modified. This means that the first time you run rsync, it might take a while, but 2nd, 3rd, etc. times will be much faster..

---

### Post by Gingalone on 2009-06-09
Thank you Legace, that's OK.
Since I'm a lazy boy, I was looking for a quick option to copy just a few modified files among many unmodified others...
:)

---

### Post by sedawk on 2009-06-09
rsync works exactly that way if you copy files to a directory
that already contains a backup - only necessary changes are copied!

If you only want to copy files changed in the last 24 hours to
a new (and empty) directory, you can try to use find.
This will find all files modified in the last 24 hours in the
current directory and subdirectories:
```

find . -mtime -1 -print

```
To find files which nobody changed in the last 3 months (90 days)
```

find . -mtime +90 -print

```
Some pipe like this should to the trick (at your own risk:)
```

find . -mtime -1 print|xargs cp -t __new_directory_for_backup

```

BTW: rsync has a newer option "--link-dest" which makes it
easy to implement incremental "online" backups (e.g. to an 
external disk" backup/20090607, backup/20090608, ..) that
look like full backups to the user (trick is implemented via
hardlinks to unchanged copies in older backup/2009xxxx directories).

---

### Post by Legace on 2009-06-09
You could use something like this:

```
find /dir/to/search -mtime -10 -exec cp {} /dir/to/copy \;
```

This is how it will work:
It will search **/dir/to/search** for files modfied in the last ten days (change **-10** to **-1** for one day) and then copy the files to **/dir/to/copy**

Hope this helps :)

---

### Post by Gingalone on 2009-06-10
Thanks a lot Legace and sedawk, very useful suggestions.
You made me go a step ahead with Ubuntu Linux!
):P

---

### Post by Legace on 2009-06-10
> **Gingalone said:**
> Thanks a lot Legace and sedawk, very useful suggestions.
):P

I'm sure you'll discover even more as you go :)
Enjoy the power of Linux!

---

