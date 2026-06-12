---
title: "Sharing files between WinXP and Ubuntu?"
date: 2008-12-20
forum: General Help
---

### Post by ReyJavikVI on 2008-12-20
I'm going to get a new computer, and I'm going to dual-boot Ubuntu 8.10 and XP. I'd like to have three partitions: Ubuntu OS, WinXP OS, and my personal files. So how do I get XP to read Ubuntu's files. I have an old PC with 8.04 and XP right now, and I can't access the Ubuntu home folder from Windows.

---

### Post by ReyJavikVI on 2008-12-20
BTW, how do I check disk space left and total?

Right-clicking->Properties on Filesystem tells me space left, but not the total space, and the Windows partition is all unknown data. I could restart and boot into Windows, but it's still useful to know.

---

### Post by Open-SuSe-A-Me on 2008-12-20
I just figured out how to do this myself...

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

if you install that driver you can read/write to ubuntu from xp.

the only thing i have not figured out yet is how to read/write from an external ext3 (linux) hard drive, but it doesnt seem like you will be using one anyway.

oh and make sure you restart windows after installing that driver.

also you can use this program

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

which can READ and copy from the linux partition, but not WRITE to them.

---

### Post by ReyJavikVI on 2008-12-20
Thanks. Do you know about the total/free space thing?

---

### Post by Open-SuSe-A-Me on 2008-12-20
well i just checked my ubuntu partition (i'm in xp at the moment) from "my computer" and a right click > properties works fine and shows the space available and space used on the "pie graph".  checking the xp partition from ubuntu i dont remember, but i am pretty sure if you open it in nautilus it will say "space available" at the bottom like it does normally.  if that doesnt work you could try the "disk usage analyzer" in applications > accessories.

---

### Post by albinootje on 2008-12-20
> **ReyJavikVI said:**
> Thanks. Do you know about the total/free space thing?

In a terminal it's : ```
df -h
```

---

### Post by ReyJavikVI on 2008-12-20
OK, thank you. One little more thing: Do you know how much space XP and Intrepid Ibex use? I'm wondering whether to get a bigger HD.

---

### Post by albinootje on 2008-12-20
> **ReyJavikVI said:**
> OK, thank you. One little more thing: Do you know how much space XP and Intrepid Ibex use? I'm wondering whether to get a bigger HD.

A fresh default installation of Ubuntu Gutsy needed about 1.2 Gb for the data i think.
Not sure about Hardy and Intrepid, but probably not that much more.

---

