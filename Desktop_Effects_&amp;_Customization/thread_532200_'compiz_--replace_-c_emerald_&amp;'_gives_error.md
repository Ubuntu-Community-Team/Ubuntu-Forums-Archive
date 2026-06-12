---
title: "'compiz --replace -c emerald &amp;' gives error"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by QwUo173Hy on 2007-08-22
I get this error when running that command

> martin@ubuntu:~$ compiz --replace -c emerald &
[1] 5534
martin@ubuntu:~$ Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'

(gtk-window-decorator:5558): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5558): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5558): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5558): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5558): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5558): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5558): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5558): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop


Can anyone help me get this working? I'm using Nvidia drivers from their website as the ones I downloaded from the repos didn't work.

---

### Post by njknight on 2007-08-22
Take a look at
[http://ubuntuforums.org/showthread.php?t=528237](http://ubuntuforums.org/showthread.php?t=528237)
and [http://ubuntuforums.org/showthread.php?t=525712](http://ubuntuforums.org/showthread.php?t=525712)

The command compiz --replace -c emerald & should be started from an Alt +F2 command window and not from the terminal.

looking at your output thou, I'm not sure that you have graphics installed correctly!! - still I'm relatively new to Ubuntu myself and there are plenty of people on the forum with far more knowledge than me - I'm sure that this issue will get solved for you..

best wishes

---

