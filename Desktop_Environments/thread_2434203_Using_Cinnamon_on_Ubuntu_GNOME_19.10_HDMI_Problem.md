---
title: "Using Cinnamon on Ubuntu GNOME 19.10 HDMI Problem"
date: 2020-01-01
forum: Desktop Environments
---

### Post by kennycm on 2020-01-01
I installed Cinnamon desktop in Ubuntu 19.10 on my Dell 5570 laptop using sudo add-apt-repository ppa:embrosyn/cinnamon and sudo apt update && sudo apt install cinnamon. All went well and I was able to set up and use Cinnamon as my goto desktop with only one problem. HDMI quit working in both GNOME and Cinnamon and no tweaking would make them work again and as I need to stream to a TV I decided to uninstall Cinnamon using sudo ppa-purge ppa:embrosyn/cinnamon and then cleaned up with autoremove. This removed Cinnamon Desktop but did not restore HDMI function so went back in and removed every Cinnamon app and file I could find and HDMI was restored. Wish I could supply better information but I was in a hurry and needed the HDMI working. Was wondering if anyone else had this difficulty and what they did to fix it, would like to reinstall Cinnamon if possible.

---

### Post by CelticWarrior on 2020-01-02
A PPA isn't an official repository. On top of that, the one you used doesn't have (yet) support for 19.10.

---

### Post by kennycm on 2020-01-14
Thank you CelticWarrior. I will close this thread.

---

