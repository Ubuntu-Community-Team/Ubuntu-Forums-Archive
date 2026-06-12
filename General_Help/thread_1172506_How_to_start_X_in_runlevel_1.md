---
title: "How to start X in runlevel 1"
date: 2009-05-28
forum: General Help
---

### Post by gjbob on 2009-05-28
Ubuntu 8.04

I would like to have have Ubuntu running with only X.  No KDE, GNOME or any other desktop or windows manager.  I want to do this to see what X looks like alone and then add different window managers and/or desktops one by one for comparison purposes.

I set runlevel to 1 via # telinit 1 and indeed it did go down to runlevel 1
then I
# startx

It looked like it tried to startup GNOME again and then it hung in what looks like a rebooting state.  I didn't see anything in the log files.  The only way to get out of this is to reboot.

Any ideas on how I can start X all by itself form shell?

---

### Post by clonne4crw on 2009-05-28
the command is 
# xinit
and from there, you
# GDM

What I'm not sure about is if it will work in single mode. Part of me doubts it.

---

### Post by sisco311 on 2009-05-28
at the gdm screen select the gnome failsafe session.

it will start an x session with an xterm.

---

### Post by clonne4crw on 2009-05-28
OH. now I get it. yeah. From the command line, just run
#xinit
to start a bare-bones X session.

---

### Post by irv on 2009-05-28
> **clonne4crw said:**
> OH. now I get it. yeah. From the command line, just run
#xinit
to start a bare-bones X session.

Did this work? inquiring minds would like to know!

---

### Post by clonne4crw on 2009-05-28
Lol. it works perfectly for me. But it doesn't have to be single mode. It can be any mode where an X session is currently nonexistent.

---

### Post by sisco311 on 2009-05-28
in runlevel 1 you are root. starting the X server as root is a very bad idea and a major security risk.

> Any ideas on how I can start X all by itself form shell?
starting X by itself makes no sense, you need at least a terminal. 

the gnome failsafe session starts the X server (and an xterm) as a normal user. 

from the xterm you can run the window manager of your choice (in the background)

i.e. 
```
xfwm4 & 
compiz &

```

---

### Post by gjbob on 2009-05-29
xinit seems to do the job just fine.  Doing research on this I always see startx.  What is starx for anyway.
 
Thanks

---

### Post by gjbob on 2009-05-29
gnome and Xorg are still running in gnome failsafe

---

### Post by anarchyinc on 2009-05-29
The process of starting x is starting the X server with the desktop environment.

---

### Post by gjbob on 2009-05-29
yep see my above comments

---

### Post by baseface on 2009-05-29
or you could create a .xinitrc and add xterms at various areas of the screen and have a little window manager of your own... consisting of just xterms.

---

