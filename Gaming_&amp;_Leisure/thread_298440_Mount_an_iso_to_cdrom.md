---
title: "Mount an iso to cdrom?"
date: 2006-11-12
forum: Gaming &amp; Leisure
---

### Post by casperiv on 2006-11-12
I am at work so I can't try it at the moment, but what is the process for mounting an ISO to the cdrom?  It is for some games I'm trying to get working, but I got sick of dealing with the wine eject bug.  If I can just mount the isos and unmount them again it will go much faster.  The only reason I need to mount to the cddrive is because that's where it was installed to, and it seems to be looking directly at that device.

Since I don't know much about emulation of devices in linux, it's possible there is a much easier way to do this.  Feel free to provide me with any info that may help.

PS: If there are nocd hacks for these games that work with the newest versions I could use those instead.  The two games I'm trying to get working right now are Civilization IV and Diablo II: LoD (1.11b).

---

### Post by s_h_a_d_o_w_s on 2006-11-12
[http://www.ubuntuforums.org/archive/index.php/t-14895.html](http://www.ubuntuforums.org/archive/index.php/t-14895.html)

Also try google. If your emulating windows solely for gaming i'd suggest cedega, or if u still have windows cd vmware, a virtual pc. good luck

---

### Post by aeon on 2006-11-12
open a terminal and:

```
sudo mount -o loop /location_of/file.iso /media/cdrom
```

change the mountpoint if neccesary, and to release it just do a 

```
sudo umount /media/cdrom
```

---

### Post by s_h_a_d_o_w_s on 2006-11-12
EDIT: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Diablo2](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Diablo2)

much better site. Also has help for that wine bug, about ejecting cd. So i am not sure about loading an iso (thats usually what software pirates do). So on the link i gave you it says:

wine eject

in terminal will open cd tray. Hope that helps!

---

### Post by casperiv on 2006-11-12
My problem is that the CD spinning up is really screwing with my ability to play.  The game runs fantastic, much faster then in windows, but when it reads the CD it comes to a hault for 20-30 seconds or more.  If I can mount the iso of my cd as the cd, it will be a ton faster.

aeon:
I tried that, but it mounts it as cdrom0 and doesn't read it when I run the game.

---

### Post by Antonlacon on 2006-11-13
Symlink?

The game's cd path is most likely in the registry for a better solution.

---

### Post by casperiv on 2006-11-13
How do you access the registry for a windows app with wine?

---

### Post by Antonlacon on 2006-11-13
wine regedit

---

