---
title: "X Server problem"
date: 2007-08-20
forum: Dell  Ubuntu Support
---

### Post by sparkin88 on 2007-08-20
Hello everyone,
I am completely new with linux and ubuntu. I am getting the familiar error: Cannot start x server blah blah blah. I have read how to fix it and it involves typing in "sudo dpkg-reconfigure xserver-xorg"
I don't even know how to enter code. I am using the Live CD and after the error I have a command line at the bottom of the page but if i type the code and press enter it starts a new line without doing anything. Can someone tell me how to do it?? Thanks

---

### Post by Corbin on 2007-08-21
It is a little bit more complicated to fix the X server problem while using a bookable CD. 

What you should do tho, is boot Ubuntu (from your hard drive) and when you get the X server error type/press    (alt+f4)    While will take you to the command line. 

And then fallow the steps that you said you had... 

But after you get it up on running i would make a copy of the x server (best choice you can ever make).

Fallow by

In terms of graphical way:
Go to (Places>Computer>File System>etc/X11) and then find the xorg.conf file and then right click copy and then rename the copy xorgbackup.conf

In terms of terminal/command line way:
type: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.<my_backup_name>

And then in the future if you mess something up... simply type:
sudo cp /etc/X11/xorg.conf <my_backup_name> /etc/X11/xorg.conf 

Hope this all helps
-Cheers mate.

---

