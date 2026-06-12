---
title: "How to remove Xfce?"
date: 2007-03-19
forum: Desktop Environments
---

### Post by XmaX on 2007-03-19
Hi, after I upgraded to Edgy, I am a bit short of disk space, and want to uninstall Xfce, as I use Gnome for 98% of the time. I tried removing xubuntu-desktop, but it just got me a copuple of kilobytes, and I can still see Xubuntu as a session choice. How do I remove it completely?

---

### Post by mykalreborn on 2007-03-19
go to synaptic and search for "xfce" then "xub" and check all the packages that come from xfce. don't mark all the packages for uninstallation without checking out if they are for xfce or not.
cheers!

---

### Post by Jedi Penguin on 2007-03-19
```
sudo aptitude remove xubuntu-desktop
```

should do it. check out psychocats tutorial and scripts also:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by twikletoes on 2007-03-21
I would say the best way to remove thing like xfce and xubuntu-desktop would be to type:
 

  sudo apt-get autoremove xubuntu-desktop xfce

---

