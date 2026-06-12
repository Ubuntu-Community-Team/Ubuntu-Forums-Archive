---
title: "is there an &quot;Overwrite older files&quot; copy option"
date: 2010-03-22
forum: Desktop Environments
---

### Post by geoffm on 2010-03-22
I need to often backup my data on an external HD. I will have new and changed files in several separate subfolders. I find it weird that  in Nautilus when the destination file already exists, it doesn't even display the two files' dates (even Windows Explorer does) and it doesn't offer the option to overwrite older files only. Since most of the several GBs of data I need to keep backed up doesn't change between my backups, it's unconveniently slow to just overwrite the whole 4GB when there's only 10MB of new stuff...

I've  looked into the cp command line options, it doesn't look like there's such an option as "overwrite older files" when copying.

Is there a workaround? A cp option I missed? A better file manager?

---

### Post by 2hot6ft2 on 2010-03-22
I think krusader will suite your needs and if you do much renaming then you may want krename which will work with krusader. They're KDE apps but they work without a hitch in Gnome sine I use it myself. Tou can click on Tools > Synchronize Directories and it will look at subfolders as well with recursive checked.

You can either find one or both in synaptic or you can install one or both with this just remove krename from the command if you don't want it.
```
sudo apt-get install krusader krename
```
They will be in Applications > Accessories > krusader and/or krename once installed.

P.S. I used it just yesterday with 2 locations comparing and synchronizing 215 GB with no problem.

---

### Post by Alan James on 2010-03-22
I use the program rsync to back up my Samba server monthly.
 [URL="http://en.wikipedia.org/wiki/Rsync"]
[/URL] 
 [http://en.wikipedia.org/wiki/Rsync](http://en.wikipedia.org/wiki/Rsync)
 

  It is similar to the cp command in that is copies data, but it does it much more efficiently in my opinion. It copies only the bytes that have changed, thus reducing transfer time and still bringing the backup up-to-date.
 

 There are lots of GUIs for rsync if you are not used to using a terminal to operate your machine. Search Google for “rsync GUI” and pick one that you like.
 

 I hope this is what you are looking for.

---

### Post by kelt65 on 2010-03-22
At the least you should be using rsync for this, and there are some nice rsync based backup programs, such as rdiff-backup that you could use as well.

---

### Post by Nandox7 on 2010-03-22
Hi,

Maybe I misunderstood the need, but 'cp -u' provides what you need.

----------------
-u, --update
      copy only when the SOURCE file is newer than the destination file or when the destination file is missing
----------------

Still rsync and other backup tools are great in case you need to keep several versions of the changed files.

---

### Post by geoffm on 2010-03-22
> **Nandox7 said:**
> Hi,

Maybe I misunderstood the need, but 'cp -u' provides what you need.

----------------
-u, --update
      copy only when the SOURCE file is newer than the destination file or when the destination file is missing
----------------

Still rsync and other backup tools are great in case you need to keep several versions of the changed files.

that **is** what I was looking for, I missed it when I looked! thanks.

I'll checkout rsync too.

---

### Post by dirtyhabanero on 2012-01-04
If I use cp -u with two folders, then it only compares the 'date of modification' with those two folders, and not the files within. 

If the r option is included, will it check and compare recursive files, after which cp will perform the copy if the destination file is older?
```
cp -ru source destination
```

I've had success with this, but uncertain of what is being performed.

DH

---

