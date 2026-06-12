---
title: "Installed xdm xinit gnome-session-fallback"
date: 2013-09-29
forum: Desktop Environments
---

### Post by ibjsb4 on 2013-09-29
The exact command was:
```
sudo apt-get install xdm xinit synaptic gnome-terminal && sudo apt-get install --no-install-recommends gnome-session-fallback nautilus
```

And I get to the login screen, but it wants to boot ubuntu-desktop.  Don't have that option, need to be able to boot to gnome-session-fallback (gnome classic no-effects).

In the pass I just went with lightdm and it detects the classic install. Not so with xdm, this needs to be configured in console (tty).

Even though I installed xinit, Im not seeing a .xinit in ~/.  So my guess is I need to build one.

**[COLOR=#ff0000]Edit:[/COLOR]** In the end I went with startx and set it up for password at login.

---

### Post by raja.genupula on 2013-10-02
you marked as solved , did you solved ? 

I have seen your message. :D

---

### Post by ibjsb4 on 2013-10-02
Hi raja, haven't ran into you in a while :)

To answer your question.  I automated startx to boot to login.  Now I am not running a  DM.

EDIT:  This is how
[http://linuxexpresso.wordpress.com/2010/10/03/startx-automatically-on-login-ubuntu/](http://linuxexpresso.wordpress.com/2010/10/03/startx-automatically-on-login-ubuntu/)

EDIT2:  Sonething else worth note is boot to login is really not much faster than using lightdm.

[URL="http://linuxexpresso.wordpress.com/2010/10/03/startx-automatically-on-login-ubuntu/"]


[/URL]

---

