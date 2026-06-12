---
title: "Robin Hood installation"
date: 2008-06-04
forum: Gaming &amp; Leisure
---

### Post by lammergeir on 2008-06-04
Hi there, I´m unsuccessfully trying to install the Linux version of Robin Hood.
I get the following error: Grateful for assistance
-en 
Welcome to the Robin Hood installation script 

Select the directory where you want to install the game, 
the default is [/home/justin/robinhood], press return only if it's ok for you: 
/home/justin/robinhd/ 
-e 
Installing to: /home/justin/robinhd/ 

/media/cdrom0/setup.sh: 41: cannot create robin.kdelnk: Permission denied 
/media/cdrom0/setup.sh: 43: cannot create robin.gnome: Permission denied 
mv: try to overwrite `/home/justin/.kde/share/applnk/Robin Hood.desktop', overriding mode 0555 (r-xr-xr-x)?

---

### Post by KIAaze on 2009-05-31
Do you still have problems installing the game?

The installation script is relatively simple: It just extracts an archive and then creates the necessary menu shortcuts.
If you have basic command-line experience, you shouldn't have problems understanding it.

I had to copy the contents of the CD to my hard-disk because the archive extraction (about 600-700MB) was freezing my PC.
I then made some modifications to the script to work around the problems you mentioned.

Unfortunately, I'm not at home right now, but I'll post the script modifications I made as soon as I can. (It's mostly just changing the extraction command and adding sudo in front of commands requiring sudo.)

Note: Found your post while googling for problems with the game. It keeps segfaulting for me in the mission where you have to meet prince John.

---

