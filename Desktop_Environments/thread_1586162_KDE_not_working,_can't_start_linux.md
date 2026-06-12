---
title: "KDE not working, can't start linux"
date: 2010-10-01
forum: Desktop Environments
---

### Post by WingedDrant on 2010-10-01
I had GNOME working fine, but wanted kde. This is only about a week after first getting ubuntu, and the first time I've ever used linux. Anyway, I installed the kubuntu plasma desktop and when prompted accepted kde being the startup desktop, then restarted. Now, though, when I start ubuntu, the kubuntu name comes up with the 5 or so loading dots underneath, all in a weird colour scheme you get from really old games, and then it goes black and nothing happens.
I didn't remove gnome yet, and have a dual boot with windows going on, so is there anyway to change the startup desktop from the grub menu? Is there any way at all to start it up with GNOME so I can remove KDE or at least get it to work properly?

---

### Post by WingedDrant on 2010-10-05
I just want to bump this, I kinda need a reply soon so I can use my computer again (Windows 7 is a pain to work with for what I need).

---

### Post by Dustin2128 on 2010-10-06
hm, sounds like yet another plymouth problem; not a kubuntu problem. Why canonical chose to put it in an LTS release I'll never know.... Anyway, my recommendation would be to boot from your ubuntu disc and edit your grub list to disable quiet boot. You won't have a bootsplash anymore; just lines of console output, but it'll at least be working. You'll have to run this command (terminal)
```
gksu gedit /etc/default/grub
``` then change this line by deleting the words quiet splash, leaving everything else (including quotes)
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"                      
```that should do the trick.

---

### Post by WingedDrant on 2010-10-08
> **Dustin2128 said:**
> hm, sounds like yet another plymouth problem; not a kubuntu problem. Why canonical chose to put it in an LTS release I'll never know.... Anyway, my recommendation would be to boot from your ubuntu disc and edit your grub list to disable quiet boot. You won't have a bootsplash anymore; just lines of console output, but it'll at least be working. You'll have to run this command (terminal)
```
gksu gedit /etc/default/grub
``` then change this line by deleting the words quiet splash, leaving everything else (including quotes)
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"                      
```that should do the trick.
 
I did this, but nothing  has changed. After it didn't work, I went back to see if I did something wrong, and the "quiet splash" was back. Even after doing it again, and reopening it to make sure it saved, nothing works.

---

