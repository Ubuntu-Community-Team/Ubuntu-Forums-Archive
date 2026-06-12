---
title: "where is?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by noobgr on 2005-10-26
i did my first install but i don't find the program.

i downloaded the xine(dvd player)

i did all that it need ./configure, make, sudo checkinstall

in sudo checkinstall i answered to be Debian pachage.
and i take this:

/home/name/xine-lib-1.0.3/xine-lib_1.0.3-1_i386.deb
You can install it in your system anytime using:

dpkg -i xine-lib_1.0.3-1_i386.deb

ok i put this text in command and i take:

name@ubuntu:~/xine-lib-1.0.3$ sudo dpkg -i xine-lib_1.0.3-1_i386.deb
Selecting previously deselected package xine-lib.
(Reading database ... 73623 files and directories currently installed.)
Unpacking xine-lib (from xine-lib_1.0.3-1_i386.deb) ...
Setting up xine-lib (1.0.3-1) ...
name@ubuntu:~/xine-lib-1.0.3$

what i must to do next?

thx

---

### Post by jasay on 2005-10-26
Looks like the install went alright.  Try "xine" in the commandline and if that works you might want to make a launcher in the menu.

Right click the applications menu, select Edit Menus, click sound and video on the left and then new entry on the bottom right/middle.  Then fill it in something like this
Name: Xine
Comment: Video player
Command: xine
icon: click and search for something like xine.xpm or xine_36x36.png

---

### Post by noobgr on 2005-10-26
it tells bash: xine: command not found

nohing else?

---

### Post by noobgr on 2005-10-26
anybody knows?:confused:

---

### Post by rickon on 2005-10-26
Try the xine site info below:  you can do a xine check in the terminal to see if everything is ok.  Got mine to work but playback is a bit jerky.

[http://xinehq.de/index.php/faq#BUILDING](http://xinehq.de/index.php/faq#BUILDING)

Rickon

---

