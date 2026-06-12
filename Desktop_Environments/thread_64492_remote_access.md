---
title: "remote access"
date: 2005-09-11
forum: Desktop Environments
---

### Post by fig_jam_uk on 2005-09-11
Hi all, just hopeing somebody can help. im looking to gain remote access to my Linux box over the internet from an XP machine (hissssssssss) does anybody have any idea how i can acomplish this? ive seen linux to linux but not realy anything windoze to linux  any help would be greatly appreciated  :razz:

---

### Post by dc2447 on 2005-09-11
SSH using [Putty](http://www.google.co.uk/url?sa=U&start=1&q=http://www.chiark.greenend.org.uk/~sgtatham/putty/&e=10342)

---

### Post by Swerver on 2005-09-12
im sure you are probably looking for a GUI remote?

sudo apt-get install vncserver

run vncserver and setup the port and password etc, then connect via the vnc client from another machine.

---

