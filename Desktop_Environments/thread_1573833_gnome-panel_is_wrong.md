---
title: "gnome-panel is wrong"
date: 2010-09-13
forum: Desktop Environments
---

### Post by ewientje on 2010-09-13
Hi everyone,
My problem is that my toppanel won't load automatically anymore when I reboot.
So far I get it restarted by typing in the terminal gnome-panel.
But then it appears in the middle of the screen. So I have to expand the panel to bring it to the top. ALso now the evolution applet has hung up. and I can't remove it from the screen.

The error message I get is:

corrie@corrie-desktop:~$ gnome-panel

(gnome-panel:9813): GConf-WARNING **: Directory `/apps/panel/toplevels/bottom_panel_screen1/screen' was not being monitored by GConfClient 0x8bcb170

(gnome-panel:9813): GConf-WARNING **: Directory `/apps/panel/toplevels/top_panel_screen1/screen' was not being monitored by GConfClient 0x8bcb170

If I close the terminal I lose gnome-panel

---

### Post by finny388 on 2010-09-13
If you are willing to go back to the default panel setup this script is a gem of a fix.

Find it at [starryhope]("chrome://speeddial/content/speeddial.xul")

It has saved my desktop many times in the past. You can even create a backup of your working panel so that if in the future it somehow corrupts you can then restore from back up.

It worked for me, I hope it works for you.

:D

---

### Post by ewientje on 2010-09-14
thank you, I'll check it out, the backup sounds great too.

---

### Post by dino99 on 2010-09-14
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure gnome-panel

---

