---
title: "Simon Tatham's Portable Puzzle Collection"
date: 2019-08-27
forum: Gaming &amp; Leisure
---

### Post by curbie1 on 2019-08-27
What installs, "Simon Tatham's Portable Puzzle Collection", and more importantly how do I un-install them, acts just like a virus, didn't install them (all 40 of them), they don't show in software>installed to remove them 
(i know, I when through every entry), I've completely reloaded my computer to get rid of them once already, very windows-ish mal-ware.

curbie
Xubuntu 18.04

---

### Post by PaulW2U on 2019-08-27
They seem to be part of a default Xubuntu installation.

The package that you want to uninstall is either sgt-puzzles or sgt-launcher.

Hope that helps.

---

### Post by curbie1 on 2019-08-27
A BIG thanks to Paulw2u!!!

this seemed to work for me:
```
dpkg&#8211;list            // to check for package name to remove/purge
sudo apt-get remove sgt-launcher
sudo apt-get purge sgt-launcher
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get remove sgt-puzzles
sudo apt-get purge sgt-puzzles
sudo apt-get autoremove
sudo apt-get clean
dpkg&#8211;list            // tomake sure package is gone
```

Thanks again
curbie

---

