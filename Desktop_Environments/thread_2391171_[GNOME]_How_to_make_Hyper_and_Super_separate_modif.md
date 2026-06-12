---
title: "[GNOME] How to make Hyper and Super separate modifiers?"
date: 2018-05-06
forum: Desktop Environments
---

### Post by jonathan90 on 2018-05-06
Hi, I've remapped caps lock to Hyper, but it does the same thing as Super. I've looked in [this post]("https://askubuntu.com/questions/423627/how-to-make-hyper-and-super-keys-not-do-the-same-thing"), which said that Super and Hyper are both set to Mod4, and you can just change one to Mod3 using setxkbmap to differentiate the keys. However, the local changes to xkb reset after a suspend, so I'd have to run the command again after I log back in. Comments in that post also mentioned that you can directly modify the file /usr/share/X11/xkb/symbols/pc, which will make the changes stick through reboots and suspend/wake up, but that's not exactly ideal since I'd be modifying system files (and an system update might overwrite my changes). Any suggestions are greatly appreciated!

---

