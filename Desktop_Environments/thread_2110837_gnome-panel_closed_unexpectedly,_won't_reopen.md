---
title: "gnome-panel closed unexpectedly, won't reopen"
date: 2013-01-31
forum: Desktop Environments
---

### Post by netopalis45 on 2013-01-31
I have posted about this before but it got lost in other things I had going on at the time. Everything was working fine and then my gnome panels closed and I got an error saying that they closed unexpectedly. When I try to relaunch it from terminal I get an error saying "segmentation fault (core dumped)". I purged and reinstalled with the same results. i purged again and found that it doesn't remove all files so I did manually.
Any ideas as to what is going on with it? I really don't want to have to wipe my system again.

---

### Post by ibjsb4 on 2013-01-31
Is this Gnome Classic or Gnome Shell?

---

### Post by netopalis45 on 2013-01-31
Sorry should have said that it is Classic Gnome on Ubuntu 12.04

---

### Post by ibjsb4 on 2013-01-31
> **netopalis45 said:**
> Sorry should have said that it is Classic Gnome on Ubuntu 12.04

I have not had this problem with metacity, but got some hits here.

[https://www.google.com/search?client=ubuntu&channel=fs&q=segmentation+fault+gnome+classic&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=segmentation+fault+gnome+classic&ie=utf-8&oe=utf-8)

---

### Post by tgalati4 on 2013-01-31
* I really don't want to have to wipe my system **again**.*  Does this imply that you had to wipe your system recently due to a hardware problem?  Perhaps your disk is failing?  Many times we point to software problems that are really hardware problems.

The fact that you tried to reinstall and got a core dump for a vital part of the operating system implies that something serious is happening.  What does your dmesg look like?

```
dmesg | more
```

Spacebar to page forward, "q" to quit.

What is the SMART status of the drive?

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

Also check your RAM with memtest.

---

