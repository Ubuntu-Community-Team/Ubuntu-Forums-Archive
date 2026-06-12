---
title: "Silly question: how to identify Ubuntu version?"
date: 2009-03-31
forum: General Help
---

### Post by kpatz on 2009-03-31
Something I was wondering while responding to another thread.  Say you walk up to a machine running (k,x)Ubuntu, and sitting at a shell, or Gnome/KDE/xfce desktop, how to determine what version of Ubuntu it is (e.g. Hardy, Intrepid, Gutsy, etc)?

uname -a gives the kernel version but not the distro version.

The /etc/apt/sources.list shows the distro, but what if this file is missing/corrupted/incorrect (the topic of the thread I was replying to)?

Just curious...

---

### Post by iaculallad on 2009-03-31
Using terminal:

```
cat /etc/lsb-release
```

---

### Post by jo4hnc on 2009-03-31
Not using terminal, System>Administration>System Monitor.

---

### Post by 1clue on 2009-03-31
This is a big problem sometimes.  I used to use **cat /etc/issue** to identify the distribution of a *nix but while that used to work fine it no longer does.  Almost nobody honors that anymore.

I wonder if there is another standard way to identify the details of the distribution, no matter if it's Linux or FreeBSD or AIX or Mac OS?  Anyone know?

---

### Post by kpatz on 2009-03-31
Thanks guys... /etc/lsb-release does the trick.  /etc/issue also shows the Ubuntu version (8.04) on my Hardy boxes and 8.10 on my Intrepid box. :)

---

### Post by 1clue on 2009-03-31
HAH!  A little bit of time with Google and all questions are answered.

No matter what distro you are on, you can type **cat /etc/*-release** to find out what it is.  At least with Linux distributions, not sure about FreeBSD or any of the commercial variants.

On my Gentoo box there is an /etc/gentoo-release file containing distribution details.  CentOS has /etc/redhat-release, but the contents say CentOS.

---

### Post by Fujik on 2009-04-13
Does anyone know from which file **cat /etc/lsb-releas**e take info?

oh. I found )

---

