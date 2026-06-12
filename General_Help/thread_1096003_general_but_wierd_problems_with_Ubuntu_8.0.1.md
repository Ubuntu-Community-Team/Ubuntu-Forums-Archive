---
title: "general but wierd problems with Ubuntu 8.0.1"
date: 2009-03-14
forum: General Help
---

### Post by selekt89 on 2009-03-14
Hello All, 

This is my first time every posting on Ubuntu forums. First off, I love the new Ubuntu .. it has everything I can imagine in an OS, and appreciate the development effort from the community. 

However, there have been some wierd issues I have been having with the OS, and I am wondering if I am the only one with these issues .. I dont know  if they are valid bugs, or maybe I need to fresh re-install .. 

After months of using Ubuntu extensively, I faced the following issues on a regular basis:

- Sometimes when I click on the status bar to maximize a window, or minimize it, the session ends and I am logged out .. this happens regularly, and is sometimes frustrating when I am in the middle of something .. 

- If I use the "Standby" feature to put the OS on standby, and come back to revive the computer, I am not able to play any mp3 files anymore .. Banshee and Rhythmbox just hang on the mp3 files 


These issues are not rare, but happen regularly on my laptop ... Is there a tracing utility indigenous to Ubuntu that I can use to track down these bugs and maybe try to figure out why this happens ? In particular, when the GNOME session is randomly killed, it is very frustrating, as I have to re-login and restart all the applications ... 

Any help or guidance is appreciated !

---

### Post by taurus on 2009-03-14
First, there is no version 8.0.1.  It's either 8.04 or 8.10.

Second, how much RAM do you have and how large is the swap partition?

Applications -> Accessories -> Terminal
```
free -m
```

Third, did you install Ubuntu on it own partition (ext3) or did you install it through windows--wubi?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

