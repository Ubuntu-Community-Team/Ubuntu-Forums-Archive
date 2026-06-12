---
title: "Deleted The Contents Of Pixmaps How To Restore???"
date: 2008-07-16
forum: Desktop Environments
---

### Post by kaola_linux on 2008-07-16
Hello, i need help in restoring my icons...Some of the icons are missing (firefox,hardware testing,emerald,etc).  It seems I've accidentally deleted the contents on my /usr/share/pixmaps.....Please help me, this is very annoying coz some icons are missing...thanks in advance

---

### Post by Wolki on 2008-07-16
> **kaola_linux said:**
> Hello, i need help in restoring my icons...Some of the icons are missing (firefox,hardware testing,emerald,etc).  It seems I've accidentally deleted the contents on my /usr/share/pixmaps.....Please help me, this is very annoying coz some icons are missing...thanks in advance

First, in the future please be more careful when doing things with administrator priviledges - not all problems that come from such mistakes are easy to fix.

Fortunately, this one should not be too difficult. If I'm not mistaken, the following command should reinstall all packages that put files in /usr/share/pixmaps:

```
sudo apt-get install --reinstall $( dpkg -S /usr/share/pixmaps | sed "s/: \/usr\/share\/pixmaps$//" | sed "s/,//g" )

```

I hope this works, it does on my computer. Good luck!

---

### Post by Merlintrix on 2010-07-22
Worked like a charm!

---

