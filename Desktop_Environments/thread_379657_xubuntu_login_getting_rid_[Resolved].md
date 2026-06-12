---
title: "xubuntu login: getting rid [Resolved]"
date: 2007-03-08
forum: Desktop Environments
---

### Post by gasull on 2007-03-08
Hi.

I tried xubuntu-desktop and then uninstalled it, but I still see the XUbuntu login instead of the Ubuntu one.

How can I get rid of it?

TIA.

---

### Post by Tahir on 2007-03-08
Are you on about the bootsplash?  i.e when it boots into Linux (before you are shown the login screen)?  If yes, then look at some of my previous posts. If on the other hand if the login screen has xubuntu written on it then that is just the theme.

-Tahir

---

### Post by gasull on 2007-03-08
No, I mean the login screen, not the bootsplash.  But thanks.

---

### Post by gasull on 2007-03-08
I found the solution:
```
sudo gdmsetup
```

---

### Post by aysiu on 2007-03-09
> **gasull said:**
> I found the solution:
```
sudo gdmsetup
```
Or, better yet, ```
gksudo gdmsetup
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

