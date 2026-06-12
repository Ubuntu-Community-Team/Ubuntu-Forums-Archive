---
title: "black screen after suspend"
date: 2006-06-17
forum: Desktop Environments
---

### Post by swank on 2006-06-17
With a fresh install I tried to suspend and that seems to work fine, only when waking up I get a black screen and no responce (I can't even ssh in...)

The box is a HP t3330 with a RC410-M (Asterope)/ECS RC410-M motherboard with an integrated ATI Radeon Xpress 200 for Intel Processors.

Can anyone please point me in the right direction?

---

### Post by cledezma on 2006-11-27
I have the same problem with suspend or hibernate. Mine is a Toshiba A75-S229 notebook. Any ideas?

---

### Post by identitet5000 on 2006-12-01
same here. oddly enough, it worked under dapper, but now when I'm using a clean install of edgy and xubuntu-desktop on my thinkpad z60t, it's blank. :/

any clues anyone?

---

### Post by u-foka on 2006-12-02
same with clevo m3sw (pentium m 1.7 ghz sis chipset)
network, keyboard and anything work, but the screen always black, 1 try to switch to tty1 and back and anything

---

### Post by niller on 2006-12-02
Same here :-(

Ubuntu 6.10
ATI Radeon X700, Samsung Syncmaster 940BF.

Cant even use:
CTRL+ALT+BACKSPACE
CTRL+ALT+F1-F7

My systems just hangs until I have to do a hard reset ! It's a shame though, always liked to work in the console :-(

Searched almost every forum on these pages, it seems to be a common problem  but still no solution. A workaround is highly appreciated !

---

### Post by greg.hagen on 2006-12-03
I had this problem after fresh loading edgy on a thinkpad x24, but I think I've fixed it.

1. Run gconf-editor

2. Go to /apps/gnome-power-manager/

3. Uncheck lock_on_blank_screen, lock_on_suspend, lock_on_hibernate

It's worked for me since I made the changes today. Good Luck!

---

### Post by u-foka on 2006-12-05
Hy! Thanks for the reply! But it doesn't worked for my :S
I can unlock my laptop, or switch to the tty1 and login there, so anything works just the screen still in the dark :(

---

