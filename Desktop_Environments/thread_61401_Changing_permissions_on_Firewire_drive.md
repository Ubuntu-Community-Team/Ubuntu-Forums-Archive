---
title: "Changing permissions on Firewire drive"
date: 2005-08-31
forum: Desktop Environments
---

### Post by Gordonbp531 on 2005-08-31
I have a 10GB partition on my Firewire drive formatted as ext3 for my Linux archiving. At the moment the owner is Root so I can't create files and directories there. How do I change the Owner to myself so that I can create files and directories there?

---

### Post by Gordonbp531 on 2005-08-31
Sorry - found it on the Unofficial Guide.......

---

### Post by KingBahamut on 2005-08-31
chown [options] user[:group] file...

or 

chmod [options] [level] <file or directory> 


Do a 
man chown
and
man chmod 

One of those should do it for you I think.

---

### Post by schdefan on 2005-08-31
You can change that by using chown
```
sudo chown -R yourname directoryname
```
The -R means recursive, so that all subfolders are owned by yourself. 
schdefan

---

