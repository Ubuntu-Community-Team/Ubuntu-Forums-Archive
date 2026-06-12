---
title: "Some apps not doing anything..."
date: 2005-07-03
forum: Desktop Environments
---

### Post by fernandomiranda on 2005-07-03
Hi,
I've been trying ubuntu after installing it, but i'm having problems as when i click on some menus, nothing happens. It just appears as if it were loading, and then nothing happens (?).

I'm not very sure, but i suppose this could be because user hasn't got privileges, or isn't root, but for logging in as root i've read i need to enable something at "Login Screen Setup", which is one of the apps not loading. Is this happening because of that?

I know how to became su at terminals, but not how to do it at gnome. ](*,) 

I also want to change screen resolution but only 640x480 and 60Hz appear as options, i suppose root will be able to see other options, will it?

I know this will be a silly question, but perhaps of that, i can't find it on any guides or howtos...

Thanks.

---

### Post by traherom on 2005-07-03
[http://www.ubuntuforums.org/showthread.php?t=22348](http://www.ubuntuforums.org/showthread.php?t=22348) - Look at the stickies!

Of course, I'm now violating [this](http://www.ubuntuforums.org/showthread.php?t=37151)... ;)

---

### Post by poofyhairguy on 2005-07-03
[QUOTE=fernandomiranda]
I also want to change screen resolution but only 640x480 and 60Hz appear as options, i suppose root will be able to see other options, will it?
[/QUOTE]

sudo dpkg-reconfigure xserver-xorg

Try that command to fix that problem. If it doesn't work the sudoers file is messed up (search forum for "sudoer").

I moved this to the right place.

---

