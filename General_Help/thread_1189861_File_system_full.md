---
title: "File system full?"
date: 2009-06-17
forum: General Help
---

### Post by halbertinill on 2009-06-17
I am running ubuntu 8.04 on a dell mini (no hard drive), and am getting a "file system full" warning.  How do I find whatever is filling up the file system, and how do I clear it back out?  Any hints?

Yesterday I got an update manager request to download a huge series of updates that took a long time to download and install, and I wonder if that is what is filling everything up.

---

### Post by Celauran on 2009-06-17
```
df -h
sudo du -sh /*
```

---

### Post by Chronon on 2009-06-17
Try:
```
sudo apt-get clean
```

---

### Post by halbertinill on 2009-06-17
ok guys, i'm a total ubuntu rookie.  give me a hint on what you just put there.

---

### Post by Celauran on 2009-06-17
Those are commands you're meant to type into the terminal. The two I posted will show where the disk usage is occurring, the one Chronon posted will clean up unnecessary files left over from installing/removing programs.

---

### Post by mcduck on 2009-06-17
"df -h" lists your file systems and the available space in them,  "sudo du -sh /*" helps finding out where the space is actually used (listing direcotories and their disk usage), and "sudo apt-get clean" might help freeing up some disk space by removng .deb packages apt-get has stored on your hard drive when installing/updating packages.

---

### Post by m4tic on 2009-06-17
yeah:popcorn:

---

### Post by Chronon on 2009-06-17
I mentioned [FONT="Courier New"]**sudo apt-get clean**[/FONT] because of this: 
> **halbertinill said:**
> 
Yesterday I got an update manager request to download a huge series of updates that took a long time to download and install, and I wonder if that is what is filling everything up.

---

