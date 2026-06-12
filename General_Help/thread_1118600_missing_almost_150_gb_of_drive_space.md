---
title: "missing almost 150 gb of drive space?"
date: 2009-04-07
forum: General Help
---

### Post by Polygon on 2009-04-07
I was running a backup and suprised to find that my external drive was out of space. I ran baobab (drive usage analyzer) and i was even more surprised to see that it reports only 300 gb is being used out of my 500 gb drive!

What disk usage analyzer shows:

[img]http://img162.imageshack.us/img162/5139/screenshotdiskusageanal.png[/img]

but what it detects my disk as:

[img]http://img529.imageshack.us/img529/512/screenshotlinuxbackuppr.png[/img]

As you can see, disk usage analyzer shows that only around 295 gb is being used out of a possible 458. I have already tried emptying my trash and running the command "tune2fs -m 1 /dev/sdc1" which actually gave me back 17 gb...but not nearly close to what i should be getting

any suggestions?

edit: just ran a check (aka a fsck) in gparted, and it said the drive was fine...so that is not the problem either

---

### Post by Polygon on 2009-04-08
any ideas....?

---

### Post by coffeecat on 2009-04-08
I noticed your first post shortly after you posted, but didn't comment because I had nothing constructive to offer. I don't know whether this will add any useful information, but try this. Install Gparted (if you haven't already). Run it from System -> Administration -> Partition Editor with the external drive plugged in and mounted. In the Gparted Window, switch to the external drive with the switcher drop down thing top right. Now post a screenshot of what Gparted is showing.

---

### Post by Polygon on 2009-04-08
gparted showing its around 500 gb (minus space used for formatting) as well.

[IMG]http://img6.imageshack.us/img6/7310/screenshot001yct.png[/IMG]

---

### Post by drs305 on 2009-04-08
I am in the process of writing a guide for the Tutorials section concerning lost disk space. In the meantime, parts of it are included in the guide about finding and removing trash. Section 8 lists other things that could be the problem.

Did you happen to clone another partition onto this drive? If so, you may have to run resize2fs to correct the file system. I didn't mention this the in the Trash guide, whose link is in my signature line.

---

### Post by Polygon on 2009-04-08
i have emptied my trash, and rebooted, and tried unmounting and remounting it, and i ran a 'check' in gparted (which just runs a fsck on the drive) and it said that the partition was the correct size and everything.....still the same thing

```

mark@Humboldti:~$ sudo fsck  -V -M /dev/sdc1 
fsck 1.41.3 (12-Oct-2008)
[/sbin/fsck.ext3 (1) -- /dev/sdc1] fsck.ext3 /dev/sdc1 
e2fsck 1.41.3 (12-Oct-2008)
LinuxBackup: clean, 303067/61063168 files, 120875236/122096000 blocks
mark@Humboldti:~$ 

```

Actually....this drive is pretty old and noisy....maybe my problem is that there are a ton of bad blocks/sectors and ext3 is just marking them for non-use and thats why i'm missing a ton of space? Is there a way to check for this?

---

### Post by ShaunG on 2009-04-08
Did you by any chance run the backup and accidentally include the backup in your backup? Or any other mounted drives?

---

### Post by drs305 on 2009-04-08
Are you running baobab/DUA as root. Running it as a normal user will not give you an accurate picture if root owns some of the files/folders.
```
gksu baobab  # or gksu baobab /path.to.LinuxBackup
```

---

### Post by callie510 on 2009-04-08
I had a very similar-looking problem after a cloned a smaller drive onto a larger one, and the empty space disappeared just as you are describing. 

Looks like the partition is the right size, but your filesystem is not. Try the command 'resize2fs'. This fixed my problem (resized my filesystem to the correct size).

---

### Post by Polygon on 2009-04-08
> **drs305 said:**
> Are you running baobab/DUA as root. Running it as a normal user will not give you an accurate picture if root owns some of the files/folders.
```
gksu baobab  # or gksu baobab /path.to.LinuxBackup
```

bingo. .Trash-0 (roots trash) has over 140 gb of used space. Deleted that cleared it up. Thanks!

---

