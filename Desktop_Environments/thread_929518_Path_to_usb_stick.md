---
title: "Path to usb stick"
date: 2008-09-25
forum: Desktop Environments
---

### Post by utnubuuser on 2008-09-25
hello -  anybody know how to find the path to a usb memory stick in terminal?

tried to transfer some files from a memory stick I use for Feisty Fawn to Hardy Heron and lost ownership of the memory stick.

Now I get read-only permission irregardless of which system I plug the memory into.

I've encountered this problem before, but I can't remember how to solve it.

Any suggestions?

---

### Post by phoenix49 on 2008-09-25
You can find you usb stick usually mounted on /media/<usb-stick-name>

---

### Post by kpkeerthi on 2008-09-25
Type **mount** in command line to find where your memory stick is mounted. 

To change the permission of the mount point, we need to know what filesystem your memory stick is formatted with.

---

