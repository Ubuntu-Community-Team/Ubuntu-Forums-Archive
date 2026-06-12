---
title: "Blank Cds wont automount in ubuntu Fiesty 7.04"
date: 2007-07-13
forum: Dell  Ubuntu Support
---

### Post by ewmiller13 on 2007-07-13
I Have a dell inspiron 2650 notebook. I know it can burn cds because the drive says rewritable. I haven't been able to burn any cds at all. I need help

---

### Post by mbradlcu on 2007-07-14
what happens if you put a cd that's formatted and contains data in the drive? do you get the mounted icon on the desktop?
you may want to post the contents of your /etc/fstab too
thanks!

---

### Post by ewmiller13 on 2007-07-15
Burnt cds are mounted no problem. Like I said i am new to ubuntu so im not exactly sure what u mean about /etc/fstab

---

### Post by mbradlcu on 2007-07-15
thanks for the update!
unfortunately your issue has me a bit stumped since the system can not only see the drive but mount the cdrom if a valid data cd is inserted.. I'm assuming you've rebooted the machine a few times since you're post and it didn't resolve the issue.. I had a similar problem and running the following resolved my issue, it won't hurt to try:
```
sudo /etc/init.d/dbus restart
```
try running that command after a blank cd has been inserted..

good luck

---

### Post by ewmiller13 on 2007-07-16
Ok Ill try that and see what happens Ill let you know how it turns out

---

