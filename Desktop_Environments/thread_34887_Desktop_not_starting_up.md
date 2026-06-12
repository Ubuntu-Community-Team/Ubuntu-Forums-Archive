---
title: "Desktop not starting up"
date: 2005-05-16
forum: Desktop Environments
---

### Post by zivs on 2005-05-16
Hello.
I have a small problem with starting up Gnome - after I "installed" cedega (from .tgz file) I can't anymore get to the desktop - all the time I type in login name and password, it changes resolution and throws back to login screen. So I can try to get in all day long.. . So I come here for your help. Is there any way to remove extracted files from system? Or is there any other way how to fix this problem? 
P.S.
On linuxquestion said to try "sudo dpkg-reconfigure xserver-xfree86" but that didn't help.  :-|

---

### Post by Xian on 2005-05-16
[QUOTE=zivs]I type in login name and password, it changes resolution and throws back to login screen. On linuxquestion said to try "sudo dpkg-reconfigure xserver-xfree86" but that didn't help. [/QUOTE]
When you say "login screen" I'm assuming you are talking about the GDM and not just a command prompt. If this is the case then I'd be interested in seeing if there are any error messages when you attempt to begin a gnome session. From GDM hit Ctrl+Alt+F1. This will place you into a basic shell and then at the prompt after you login type this:

$ sudo  /etc/init.d/gdm stop

Now login again and type this:
$ startx

What is displayed when you finish?

---

### Post by Power`Pig on 2005-05-17
[QUOTE=Xian]When you say "login screen" I'm assuming you are talking about the GDM and not just a command prompt. If this is the case then I'd be interested in seeing if there are any error messages when you attempt to begin a gnome session. From GDM hit Ctrl+Alt+F1. This will place you into a basic shell and then at the prompt after you login type this:

$ sudo  /etc/init.d/gdm stop

Now login again and type this:
$ startx

What is displayed when you finish?[/QUOTE]
There are few times "Xauth: timeout in locking authority file /home/girts/.Xauthority"
and then
"Symbol __ glXactivescreens from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!"
and then as much as I remember was again "Xauth: timeout in locking authority file /home/girts/.Xauthority" and it ended up like all the time before - with no desktop :(

P.S. Password recovery somehow doesn't work...

---

### Post by Power`Pig on 2005-05-18
Well I could format hard disk drive but I have materials for school etc (and porn  :roll: ) so it would be very nice to know how to repair this problem.

---

