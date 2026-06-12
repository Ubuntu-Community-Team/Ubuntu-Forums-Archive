---
title: "rsync how to exclude dot directories"
date: 2008-05-24
forum: Desktop Environments
---

### Post by MrGreen on 2008-05-24
Hi,

I do not have a real problem using rsync, but in backing up my home directory I wish to exclude a certain directory... namely .VirtualBox

Now I have tried using --exclude=".VirtualBox' [one or two I forget hehe]

But it still gets backed up either I need to put full path or something else?

Even tried Flyback could not get it too work too

The only way I could do it is either move .VirtualBox before back up or delete it after

TIA

MrG

---

### Post by tamoneya on 2008-05-24
try```
--exclude=.VirtualBox/*
```

---

### Post by MrGreen on 2008-05-24
Wow what a quick reply thanks I will ;-)

MrG

---

### Post by MrGreen on 2008-05-25
Folder gets copied but not contents thanks again :-)

MrG

---

### Post by leonbravo on 2011-07-15
--exclude ".VirtualBox/"

should do it also. 

The recommendation for people out there, doing a backup with Grsync is running it as root. 

Some options seems to be ignored, including exclude if there are permission problems.

---

