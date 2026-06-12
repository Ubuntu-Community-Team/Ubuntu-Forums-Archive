---
title: "[HOW-TO] [GUIDE] How to have a different wallpaper in each workspace!"
date: 2008-04-12
forum: Desktop Environments
---

### Post by s3a on 2008-04-12
**_[SIZE="5"]Installing:[/SIZE]_**

1) Go in the link on my signature and download: "wallpapoz-0.4.1.tar.bz2" **to your desktop.**
2) Right click on it and select extract. **Make sure that the extracted folder is on the desktop.**
3) Click Application-->Accessories-->Terminal
4) Now in the terminal, type the following commands:

       a) cd ~/Desktop/wallpapoz-0.4.1
       b) sudo python setup.py install

**IF YOU EXPERIENCE PROBLEMS WITH DEPENDENCIES, GO TO SYNAPTIC AND DOWNLOAD THE DEPENDENCIES AND THEN REDO ALL THE STEPS.**

**_[SIZE="5"]Configuring:[/SIZE]_**

1) Save all the wallpapers that you want to use in: "/home/_accountname_/Pictures" (the Pictures folder)
2) Click Applications-->Accessories-->Wallpapoz
3) On the workspace that you want to change wallpaper, click on the small arrow beside the number thats on the same line as rename this.
4) When that new line appears, right click on it and click "Change Wallpaper."
5) Locate your wallpaper (it should be in the Pictures folder) and select it.
6) Click both save and restart.

**_[SIZE="5"]Note:[/SIZE]_**
You will need to restart the daemon every time you reboot your computer. This was only tested and confirmed to work by me on Ubuntu 7.10 (32-bit).

*Edit: I also got it working under Ubuntu 8.04 LTS (64-bit).*

---

### Post by tzulberti on 2008-04-14
Great Tip, but i think that it should go on Tips And Turorial SubForum.

Nevertheles, thanks.

---

