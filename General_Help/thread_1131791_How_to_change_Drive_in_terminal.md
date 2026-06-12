---
title: "How to change Drive in terminal?"
date: 2009-04-21
forum: General Help
---

### Post by mubbashar on 2009-04-21
there are four drive on my pc like c , d , e , f in terminal how i move to these drive???

---

### Post by 3Miro on 2009-04-21
[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

[http://tldp.org/HOWTO/Partition/](http://tldp.org/HOWTO/Partition/)

Those contain some explanations. There are no drive letters under Linux. You mount a drive to a folder and in that case the content of the folder becomes the content of the drive.

---

### Post by kwakhyok on 2009-04-21
> **mubbashar said:**
> there are four drive on my pc like c , d , e , f in terminal how i move to these drive???

I suppose you have a Windows/ubuntu dual OS computer.

Try to go through /media/sda(x)/ (here x represents you harddisk)

---

### Post by coffeecat on 2009-04-21
> **kwakhyok said:**
> Try to go through /media/sda(x)/ (here x represents you harddisk)

That will only work if they're already mounted.

**mubbashar**, are you using Ubuntu gnome and, if so, which version? If so, go to the Places menu and have a look through there. Your Windows partitions should be listed there but unmounted. Simply click on the one you want, put in your password where prompted and the system will mount the partition and open a Nautilus file manager for you.

Are you using Windows XP or Vista? Be careful writing to a Vista C: drive from Linux. Better still, don't. I've read reports of Vista reacting badly after a Linux write to the C: partition. You shouldn't get this problem in XP. Unless you do something unwise in C:\Windows that is. :wink:

---

### Post by mubbashar on 2009-04-21
i used ubunto 8.1 and window xp..

---

