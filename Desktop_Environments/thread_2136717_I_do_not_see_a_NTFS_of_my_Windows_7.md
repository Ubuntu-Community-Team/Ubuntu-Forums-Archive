---
title: "I do not see a NTFS of my Windows 7"
date: 2013-04-18
forum: Desktop Environments
---

### Post by eugene8211 on 2013-04-18
Hello,
I have a dual boot:
Before i select a OS i get a menu screen of ubuntu choosing me :
1) windows 7 loader
2) ubuntu
(I can use windows 7 from a menu list and my windows 7 is working.)

I chose ubuntu.
When i use ubuntu in my ubuntu OS i cannot see any NTFS partitions of my windows 7(when i enter the Home folder from the left menu of my screen),
what could be my problem and why i suddenly cannot see ant ntfs partitions when i use ubuntu?
any help will be appreciated!

---

### Post by sanderj on 2013-04-18
It's not in your home directory. There must be a seperate icon with a harddisk. Click on that.

---

### Post by eugene8211 on 2013-04-18
> **sanderj said:**
> It's not in your home directory. There must be a seperate icon with a harddisk. Click on that.

I used to have it before but something is happened and they are gone. What is weird is that i still can do a dual boot.

---

### Post by oldfred on 2013-04-18
Is this wubi, since you have Windows shown first?

It then is hosts in Nautilus left panel.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by eugene8211 on 2013-04-18
It is not wubi! the ubuntu is shown first! what is nautilus?

---

### Post by oldfred on 2013-04-18
Nautilus is the file browser.

Post these, you can copy & paste the terminal output here:

sudo fdisk -lu
mount

---

### Post by eugene8211 on 2013-04-20
How to install nautilus-3.8.1.tar.xz? or how to use it?

---

### Post by oldfred on 2013-04-20
It is installed by default.

I use gnome-panel, so it just is the places menu item in top panel, in Unity I think you just click on one of the buttons on the left. If not Ubuntu but one of the other flavors, you may not have Nautilus but other equivalent file browsers.

In Ubuntu you almost never download .tar files to install. New users should only install from Software Center or synaptic (which now is not installed by default) from the repository. In a few cases you might need special software, but that should be a .deb which installs more like Windows in just clicking on it.
The repository and ease of installing software is one of the real advantages of Ubuntu.

---

