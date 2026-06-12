---
title: "launch firefox as another user"
date: 2004-12-29
forum: Desktop Environments
---

### Post by mrt on 2004-12-29
I want to launch firefox as another user, but this is what happens:

```
me@ubuntu ~ $ su otheruser
Password:
otheruser@ubuntu ~ $ /usr/local/firefox/firefox
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:7268): Gtk-WARNING **: cannot open display:
otheruser@ubuntu ~ $
``` 

is there a way around this?  I'm aware of firefox profiles, but that doesn't quite fit the bill here.  TIA

---

### Post by TekMate on 2004-12-29
xhost + typed before running su will allow anyone to connect to your xserver. To put it back xhost -

---

### Post by TravisNewman on 2004-12-29
[QUOTE=TekMate]xhost + typed before running su will allow anyone to connect to your xserver. To put it back xhost -[/QUOTE]
 That didn't work for me. You can use gnomesu instead of su though. You might have to apt-get it though, I don't think it's included in the default install.

---

### Post by mrt on 2004-12-30
I tried to apt-get gnomesu, but even with universe enabled, apt couldn't find it.  I downloaded the tarball from sf.net, only to get an error about not having GTK2 during ./configure (?).  At that point I became discouraged, and tried the xhost + method, which worked fine.

Perhaps I should have mentioned I'm using the earlier of Warty/Hoary ( I forget which is which, I guess numbers are not hip enough anymore).  Regardless, it's working as intended, thanks for the posts.

---

