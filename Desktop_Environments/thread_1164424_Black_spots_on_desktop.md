---
title: "Black spots on desktop"
date: 2009-05-19
forum: Desktop Environments
---

### Post by mauro24 on 2009-05-19
I have an asus eee box computer with ubuntu 9.04.  I was messing with compizconfig window mannager, to get my computer to do a lot of the window effects, most of them worked, but when I tried to activate the blur effect, the computer froze and the screen went black. When I restarted, the desktop loaded up without panels and bunch of black spots, they only thing that was visible was the mouse cursor and the background image. I try failsafe gnome, it happened the same way too.  I read some posts that gave me these codes to reset the xorg from the failsave terminal:
sudo dpkg-reconfigure -phigh xserver-xorg
startx
 &
sudo dpkg-reconfigure xserver-xorg
startx

I tried both, however nothing happened, something came out about a warning of a back up in the xorg folder or something, I couldn't print it out because I didn't know how to do it.

I also try the recovery mode, I did the xfix, but the same warning came out.

I just need someone to tell how to fix this without reinstalling ubuntu.  Thanks in advance.:popcorn:

---

### Post by mauro24 on 2009-05-19
I got it fixed. After a long search I found 2 code lines that worked for me, I don't know which one worked but you can try both.  First log in the failsafe terminal and type either or both of this lines:

gconftool-2 --recursive-unset /apps/compiz

or

rm -rf .gnome .gnome2 .gconf .gconfd .compiz

log out and log back in as normal.  That did it for me.:D):P

---

