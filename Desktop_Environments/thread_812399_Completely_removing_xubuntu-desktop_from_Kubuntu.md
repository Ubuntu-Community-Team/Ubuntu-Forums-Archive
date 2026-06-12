---
title: "Completely removing xubuntu-desktop from Kubuntu"
date: 2008-05-29
forum: Desktop Environments
---

### Post by julyski on 2008-05-29
So, I'm fairly new to Linux.  I've been running Kubuntu 8.04 for a month or so (since it was released).  I was feeling a bit adventurous and installed the package *xubuntu-desktop* to give Xubuntu a quick test drive.  I decided that I would just stick with the KDE after all.

I have completely removed and purged *xubuntu-desktop* as far as I know.  However, all of the programs that *xubuntu-desktop* came with are still installed.  Is there an easy way to purge everything that came with *xubuntu-desktop*?  Of course, if Xubuntu and Kubuntu happen to use some of the same things, I would like to be able to keep those for use in Kubuntu.

Am I asking the impossible?  I wouldn't be too worried, but hard drive space is limited in the Kubuntu partition.  Every little bit will help.  The addition of xubuntu-desktop added roughly 500mb.  After removal, in only reduced it by about 250mb.

Thanks in advance.

---

### Post by kpkeerthi on 2008-05-30
What command did you use to remove xubuntu-desktop?

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by julyski on 2008-05-30
Since I used Adept to install it, I used Adept to remove it.  After I realized everything was not removed, I used **sudo apt-get purge xubuntu-desktop** command hoping that would remove the remaining components.

---

### Post by benerivo on 2008-05-30
Try```
sudo apt-get autoremove
```If that doesn't work, open adept and search for xfce, and from there you can carefully remove these xfce named packages (make sure you don't remove something that takes out half your system!).

---

### Post by Xiong Chiamiov on 2008-05-30
You can actually use regex pattern matching to get rid of everything that has a certain thing in its name.  I'm at school right now, so I can't experiment around, but [this]("http://forums.debian.net/viewtopic.php?p=131853") gives a good description you should be able to get started from.

---

