---
title: "[SOLVED] X Server"
date: 2008-10-04
forum: Desktop Environments
---

### Post by cocopeanut on 2008-10-04
I'm trying to install an NVidia Driver. According to the instructions, I have to stop the x server. This is what I have done so far:

1) CTRL + ALT + F2
2) Logged in
3) cd etc/init.d
4) sudo gdm stop

It says the server is already running on :0. I sounds like it's attempting to start the server in different consoles.

What am I doing wrong?

Thanks for your help.

-=-Oscar-=-

---

### Post by wd5gnr on 2008-10-04
The X server is named Xorg or sometimes just X.

From your console window try:

pgrep X

then if it returns 32333 try:
 
kill 32333

or

killall X

or 

killall Xorg

I suspected

/etc/init.d/x11-common stop

might work but looking at it, it looks like stop does nothing on Hardy.

You need to be root to do any of this, of course. So use sudo in front of all these commands or log in as root if you have a root account (which you shouldn't).

---

### Post by cocopeanut on 2008-10-04
> **wd5gnr said:**
> The X server is named Xorg or sometimes just X.

From your console window try:

pgrep X

then if it returns 32333 try:
 
kill 32333

or

killall X

or 

killall Xorg

I suspected

/etc/init.d/x11-common stop

might work but looking at it, it looks like stop does nothing on Hardy.

You need to be root to do any of this, of course. So use sudo in front of all these commands or log in as root if you have a root account (which you shouldn't).

Actually, for some reason it worked when I selected CTRL+ALT+F1 instead of F2. 

But thanks for your detailed and prompt reply. :)

-=-Oscar-=-

---

