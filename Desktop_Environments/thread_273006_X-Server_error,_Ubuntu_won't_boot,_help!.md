---
title: "X-Server error, Ubuntu won't boot, help!"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Ryuujin on 2006-10-07
Hello:

I tried to install xgl/compiz and screwed up some files.

Now x-server wont boot, so I cant get into ubuntu it just gives me an error and a terminal (can't use wedit from that terminal).

So I booted from the live cd, mounted my drive but I cant edit any files (they're all read-only). 

How can I identify myself? It doesn't ask me for my user or pass on that drive, just says that I cant edit.

Further more, were can I find the file that has the boot commands (I added two entries) and I need to delete them.   

This is my first time using linux, so any commands, help, links, etc. that will help fix my problem are really appreciated!

Thanks!

---

### Post by pay on 2006-10-07
Make sure you have your 3d drivers setup before you install xgl. What guide where you using? The file that was edited probably was /etc/X11/xorg.conf or /etc/gdm/gdm.conf-custom.

---

### Post by El Menda on 2006-10-07
Hi man. Why dont u edit them from terminal? I dont need to use graphics to edit your file.
Try to boot your linux, u'll get that error, and the system will ask u for the username and pass. Then u can edit the file using:
```
$sudo nano xxxx
```
where xxxx is the path of the file

When u finish write: 
```
$startx
```

---

