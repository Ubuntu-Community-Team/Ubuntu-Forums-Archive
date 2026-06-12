---
title: "ati mobility m4 (inspiron 8000) and xubuntu resolution"
date: 2006-08-18
forum: Desktop Environments
---

### Post by zip22 on 2006-08-18
on a dell inspiron 8000 (ati mobility m4 graphics) with the live cd, if i booted in the normal mode, i would get a really messed up display once i got to the desktop.  it was like there were 3 desktops stacked on top of each other and i could only see one edge of each (when i moved my mouse into that edge, i could see it 3 times).  booting in the safe graphics mode worked, and i installed while in safe graphics mode. 

now i only have a couple very low resolution options.

i found instructions here how to fix the resolution issue here
[http://ubuntuforums.org/showthread.php?t=167670&highlight=mobility+m4](http://ubuntuforums.org/showthread.php?t=167670&highlight=mobility+m4)

i attempted to edit xorg.conf, but i don't have permission to edit the file.  what do i need to do to edit the file?

---

### Post by jj26 on 2006-10-10
From inside gnome open the terminal and type

sudo gedit ../../etc/X11/xorg.conf


or from the recovery console type

sudo sensible-editor ../etc/X11/xorg.conf


Each of these will ask you your password then allow you to open and edit the document.


I was having this problem too, which is why I ran into this post. Thanks for the redirect to the solution. :-)

---

