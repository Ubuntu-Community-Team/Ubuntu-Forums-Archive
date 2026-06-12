---
title: "How do I execute a binary when X starts?"
date: 2006-01-20
forum: Desktop Environments
---

### Post by ardchoille on 2006-01-20
I installed Docker from the repos on Ubuntu 5.10 (gnome) and I would like to use docker in gnome, openbox and blackbox. I have tried to execute docker when X starts and I tried the following, one at a time:

echo exec /usr/bin/docker > ~/.xinitrc  (this didn't work)

echo exec /usr/bin/docker > ~/.xsession  (this caused X to hang while starting)

sudo echo exec /usr/bin/docker > ~/etc/X11/xinit/xinitrc  (this did not work)

but none of those ideas worked. How do I execute a binary when X loads?

---

### Post by ptmurphy on 2006-01-20
Have your tried...

System/Preferences/Sessions and click on the Startup Programs tab.  You should be able to launch whatever you wish.

---

### Post by ardchoille on 2006-01-20
[QUOTE=ptmurphy]Have your tried...

System/Preferences/Sessions and click on the Startup Programs tab.  You should be able to launch whatever you wish.[/QUOTE]
Will that work with other window managers when I am not running gnome?

---

### Post by ardchoille on 2006-01-23
Any idea about getting a binary to start when X starts? I really need to learn how to run a binary when X starts.

---

### Post by Tichondrius on 2006-01-23
put it in your ~/.xinitrc

do "man xinit" for more info

P.S.  like the man page says, make sure you start the programs in the background (use &)
  cause otherwise if the program doesn't exit quickly, it will stop the window manager from
  loading.

---

### Post by ardchoille on 2006-01-24
[QUOTE=Tichondrius]put it in your ~/.xinitrc

do "man xinit" for more info

P.S.  like the man page says, make sure you start the programs in the background (use &)
  cause otherwise if the program doesn't exit quickly, it will stop the window manager from
  loading.[/QUOTE]
Thanks, works when you put the "&" in there :)

---

