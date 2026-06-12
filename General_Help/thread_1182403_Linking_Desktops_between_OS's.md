---
title: "Linking Desktops between OS's"
date: 2009-06-08
forum: General Help
---

### Post by fiveacez on 2009-06-08
I've dual booted my computer, and I wanted Vista and Jaunty to have the same desktops.

Here's what I tried to do:
```

rmdir ~/Desktop
ln -s /media/Data/Arun/Desktop ~/Desktop

```Instead of changing to the location of the desktop to my shared data drive (which worked for everything else), it just makes a shortcut to that folder on my data drive.

Is there a way to change the location of the Desktop, or am I stuck with just a link?

---

### Post by fiveacez on 2009-06-08
..ok i found out that Ubuntu made a new desktop directory by itself, but I got it to link to my shared partition.

But I have a new problem:  the directory isn't showing anything. (but the Terminal says there is plenty there!) ](*,)

---

### Post by fiveacez on 2009-06-08
bump

---

