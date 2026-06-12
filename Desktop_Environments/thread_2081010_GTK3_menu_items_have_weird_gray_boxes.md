---
title: "GTK3 menu items have weird gray boxes"
date: 2012-11-05
forum: Desktop Environments
---

### Post by notanimposter on 2012-11-05
After upgrading my laptop to (x64) 12.10, I noticed weird gray boxes behind all menu items. Some other things seem messed up, too. Certain black borders are really bold, and the bottom of WingPanel menus are transparent. Interestingly, some icons (namely the discharging battery icon in the tray) are affected as well.:confused: I was and still am using the elementary gtk theme and the elementary icon theme.

No matter what I did, I couldn't seem to fix the issue, and found 1 other person who had this issue, who fixed it by basically deinstalling /all the things/. I completely reinstalled Ubuntu. I am now on (x64) 12.04 (technically, an alpha of elementary OS Luna), and something I installed/upgraded/screwed up made the problem happen again. I have absolutely no idea how to proceed. Any help would be greatly appreciated.


Update: I figured out that the problem is related to the GTK programmers deciding it was time to break everyone's themes again with 3.6.

---

### Post by omshivaprakash on 2012-12-10
I have the exact issue with 12.10.

---

### Post by soccnut on 2012-12-11
I face the same problem with 12.04. Sometimes, instead of boxes, wierd symbols appear.

I solved the issue by restarting gnome.
Ctrl-alt-F1 to go into tty.
Login and run 'sudo /etc/init.d/gdm restart'

---

