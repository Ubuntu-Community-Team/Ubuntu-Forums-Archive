---
title: "installing xfce"
date: 2009-02-26
forum: Desktop Environments
---

### Post by ishiva42 on 2009-02-26
Hi. I just installed ubuntu 8.10. I want to install xfce too. I attempted to use the .run download from the xfce website, but that told me that I don't have glib 2.6.0 or higher. So, I downloaded the latest version of glib. I tried to install it, but it told me that it needed gettext support. So, I downloaded gettext and tried to install it, and it errored out on me. Said something about java, which I haven't downloaded yet. Do I really need java? And, is there a simpler way to install xfce? This seems way too complicated. Is it because I have it installed inside windows? Does it need its own partition to run xfce? is this the same for kde? thanks in advance.

---

### Post by taurus on 2009-02-26
Just install the xubuntu-desktop package.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```
You need to log out and choose which session you want to run at the GUI login screen.

---

### Post by 73ckn797 on 2009-02-26
Try the following:
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

