---
title: "Compiz wont work right"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by Siege Bot on 2007-11-10
Hello all. Just upgraded from linux mint to gutsy, and so far I am enjoying it aside from one mildly annoying issue. After I finished installing neverwinter nights I wanted to install the restricted drivers, since I was getting pretty poor performance in game. Anyway, once I did this compiz didn't feel like working any more and I can't enable any of my fancy desktop effects. I read from the sticky that there is some sort of compatibility issue with my line of video cards, but I was wondering if there is any way to get things working. I am running it on a dell inspiron 6000 with a ati mobility x300.

---

### Post by Forlong on 2007-11-10
If you installed the proprietary (restricted) ATI driver, you need Xgl now:
```
sudo apt-get install xserver-xgl
```

---

### Post by Siege Bot on 2007-11-10
It worked, thanks!

---

