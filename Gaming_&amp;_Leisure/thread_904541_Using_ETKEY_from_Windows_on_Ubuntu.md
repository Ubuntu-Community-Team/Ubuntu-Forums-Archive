---
title: "Using ETKEY from Windows on Ubuntu"
date: 2008-08-29
forum: Gaming &amp; Leisure
---

### Post by scalywag66 on 2008-08-29
Is it possible to use my ETKEY from Windows on the Ubuntu installment?  

I have lots of XP on various friendly servers on the Windows version that would suck for me to just forget about, and copying so will keep it going.  Since I think Ubuntu is going to be my main OS from now on, I'm going to try to minimize the need to go back to Windows unless necessary.  

I can't find/see any kind of 'etmain' folder on Ubuntu enemy territory folder, and wondering if there's a way to replace the ETKEY

---

### Post by anjilslaire on 2008-08-29
Check for it here: 
/home/youname/.etwolf/etmain/

---

### Post by scalywag66 on 2008-08-30
The thing was, I had to either press CTRL+H or click on option to view hidden files.

Now another problem....

I can't seem to paste it in the etmain folder.  .etwolf has a read only symbol over.  What gives?

---

### Post by anjilslaire on 2008-09-10
```

gksudo nautilus

```

**BE VERY CAREFUL**. 
That will open nautilus as root, allowing you to do very bad things to your system if you alter the wrong file/directory. Paste your ETKEY into the .etwolf folder, or better yet, remove the read-only attribute. And make sure you are assigned as Owner to /.etwolf/

---

