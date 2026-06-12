---
title: "I made a boo boo"
date: 2006-01-17
forum: Desktop Environments
---

### Post by Chemical Storm on 2006-01-17
So upon editing my xorg.conf file I left 3 extra words and now my graphical interface wont load, can I go to the recov mode and edit that file so it will boot?

---

### Post by dcstar on 2006-01-17
[QUOTE=Chemical Storm]So upon editing my xorg.conf file I left 3 extra words and now my graphical interface wont load, can I go to the recov mode and edit that file so it will boot?[/QUOTE]
sudo dpkg-reconfigure xserver-xorg

---

### Post by RAOF on 2006-01-17
Yes.  But you'll need to do it in a command-line editor (like nano or vim) because the GUI still won't load, even if you use recovery mode.

Edit: Or, even better, use the above command.

---

### Post by Omnios on 2006-01-17
You can go into recover mode and open it with sudo nano /etc/X11/xorg.conf.

 Nano is a command line text editor that you can more the coursor around with the errow keys etc. Works supprisingly well

---

### Post by taurus on 2006-01-17
It's always a good practice to make a backup copy first before you edit system's files...  :) 

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

---

### Post by ardchoille on 2006-01-17
It is my opinion that everyone should learn how to use cli, that way if anything fails, you're not stuck or intimidated by the command line. I did something recently that made X fail to load. Five years ago I would have panicked and been stuck. But now I just opened irssi and started chatting while I went into the command line and fixed xorg.conf. Huray for cli, irssi and screen :)

---

### Post by bikeman on 2006-01-17
Or, you could use a Linux Live CD version.  I'm not familiar with the ubuntu Live CD, but Knoppix has always worked for me (fixed a boo boo I made in my Grub menu.lst file - oops).  Heck, Knoppix even allowed me to rescue some really important files from a totally farked Windows PC!  (Which then got a new hard drive and Windows re-installed for my Windows-impaired friend).

---

### Post by ardchoille on 2006-01-17
Agreed, I use knoppix as a rescue environment. MEPIX is good for this too as is system rescue cd.

---

