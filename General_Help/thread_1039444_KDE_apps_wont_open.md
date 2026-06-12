---
title: "KDE apps wont open"
date: 2009-01-14
forum: General Help
---

### Post by rmausser on 2009-01-14
Hi, I am having a weird issue with KDE applications

Im running ubuntu 8.10 with the Ubuntu Studio repos installed and restricted updates also enabled.

When I try to open a KDE program I get this error

"Will not save configuration.
Configuration file "/home/robmausser/.kde/share/config/kisorc" not writable.
Configuration file "/home/robmausser/.kde/share/config/kdeglobals" not writable.
Please contact your system administrator."

It seems like its running the apps as root and thus cannot get permission to write to my home folder. 

Anyone encounter this?

Thanks

---

### Post by Titan8990 on 2009-01-14
What format is your root filesystem partion? eg - ext3 ntfs

---

### Post by rmausser on 2009-01-14
ext3

I did an automatic partition install of 8.10, so it did what it wanted to.

---

### Post by taurus on 2009-01-14
Do you have any problem writing to your $HOME, /home/robmausser?

What happens when you run this command from a terminal?

```
touch ~/testing
```

---

### Post by rmausser on 2009-01-14
nothing happens when I enter that into terminal

---

