---
title: "wm problems"
date: 2005-11-29
forum: Desktop Environments
---

### Post by hollowhead on 2005-11-29
I've tried to solve the first of these problems myself but not managed to hence the post and the second is baffling and I've not managed to google anything so here goes....

I downloaded enlightenment wm using synaptic dr16.6 and installed it fine.  I tried following poofyhairyguys howto to get it to communicate with gnome but although it loads- no app not even a terminal is visible.

This bit I managed

sudo gedit /usr/share/xsessions/Enlightenment.desktop  


Then put this in the new file:


Quote:
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=
Exec=enlightenment
Icon=
Type=Application  

and E still loads

Its the next bit that I didn't understand but I tried this

sudo cp /usr/share/gnome/default.session cp /usr/share/gnome/.gnome2.session  


Then I replaced the line in the gnome2.session  


as below
1,RestartCommand=gnome-wm --sm-client-id default1  


Change the like to look like this:


Quote:
1,RestartCommand=gnome-wm --default-wm enlightenment --sm-client-id default1  

No joy though E still loads what have I done wrong.

Second question downloaded FVWM-gnome thinking in my ignorance it would work happily with gnome.  If I selected it as wm for that session to try I get a blank brown screen and thats it.  I have to ctrl-alt-backspace to get back to GDM login screen.  Again how do I get it to work?

Cheers.

---

### Post by kairu0 on 2005-11-29
Not what you asked for but xfce+gnome is sweet:

[http://www.ubuntuforums.org/showthread.php?t=88393](http://www.ubuntuforums.org/showthread.php?t=88393)

---

