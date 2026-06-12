---
title: "How do I start Xfce without GDM?"
date: 2009-07-22
forum: Desktop Environments
---

### Post by Hetor on 2009-07-22
I want to get rid of GDM to increase my system performance. GDM is pretty useless for me, as I have no other users on my PC. I can start Xfce with "startxfce4" command, but it only works if I run it as root. I have tried "dpkg-reconfigure x11-common" to allow anyone to start the X server, but it still says that I have no proper permissions. Please help me. Also how do I make Xfce start automatically after I boot? (without GDM).

---

### Post by mojoman on 2009-07-22
> **Hetor said:**
> I want to get rid of GDM to increase my system performance. GDM is pretty useless for me, as I have no other users on my PC. I can start Xfce with "startxfce4" command, but it only works if I run it as root. I have tried "dpkg-reconfigure x11-common" to allow anyone to start the X server, but it still says that I have no proper permissions. Please help me. Also how do I make Xfce start automatically after I boot? (without GDM).

I don't know what the permissions trouble might be but I think .xinitrc is the correct file to put the command to start xfce in. Then I think the correct way is to end your .bash_profile with the command startx (to get .xinitrc to be run). At least that's how I remember it, it was quite some time ago that I fiddled with this type of setup so I'm not 100% but trying this won't make your computer explode or anything.
/mojoman

---

### Post by kerry_s on 2009-07-22
> **Hetor said:**
> I want to get rid of GDM to increase my system performance. GDM is pretty useless for me, as I have no other users on my PC. I can start Xfce with "startxfce4" command, but it only works if I run it as root. I have tried "dpkg-reconfigure x11-common" to allow anyone to start the X server, but it still says that I have no proper permissions. Please help me. Also how do I make Xfce start automatically after I boot? (without GDM).

not recommended with the move towards policykit a lot of stuff will not function right. you will have lots of permission problems.

with that said, just put startx in ~/.profile on the end.
you can use ~/.xinitrc to control what starts up if you want, but if you only have xfce4 it should be started automatically. 


gdm uses a paltry 1.2mb thats not much & the savings is not worth the hassle, you can cut corners elsewhere & it's safer.

---

### Post by kelvin spratt on 2009-07-22
Just keep GDM and goto admin, login window click on security enable auto login with your user name if done correctly when you reboot it will boot straight to your desktop.

---

### Post by durand on 2009-07-22
You won't be improving your system performance by much. GDM doesn't really do anything after you login so there's nothing to lose by keeping it.

---

### Post by kpkeerthi on 2009-07-23
> **kerry_s said:**
> 
gdm uses a paltry 1.2mb 
Its 1.2**%**, not 1.2 mb as I read from your screenshot :P

---

### Post by kerry_s on 2009-07-23
> **kpkeerthi said:**
> Its 1.2**%**, not 1.2 mb as I read from your screenshot :P

:lolflag: 

okay, then i have 250mb, so:

250-1.2%= 247-250= 3mb

is that right?

---

### Post by Hetor on 2009-07-23
> **kelvin spratt said:**
> Just keep GDM and goto admin, login window click on security enable auto login with your user name if done correctly when you reboot it will boot straight to your desktop.

I already have the autologin on, I just don't want useless processes to eat my RAM (even if it doesn't use much).

And I'm not sure that messing with .xinitrc and .profile will help, since I have permission problems with X server.

---

### Post by kpkeerthi on 2009-07-23
> **Hetor said:**
> 
And I'm not sure that messing with .xinitrc and .profile will help, since I have permission problems with X server.
I'm not sure what you mean here.

If you want to start XFCE using the **startx** command, you need to add the xfce4 startup command to ~/.xinitrc.

If you want to start X instantly upon login, you need to add **startx** to your ~/.bash_profile or ~/.profile file.

---

### Post by Hetor on 2009-07-23
But I can't start X using the startx command nor startxfce4, it says that I don't have proper permissions. They work when I run them as root, though.

---

### Post by themtx on 2009-07-23
You could try slim.  I had some success w/that on an older box.  It's not as aesthetically pleasing as GDM's pretty screen(s), but it presents a login dialog and starts XFCE just fine.

slim - desktop-independent graphical login manager for X11

Install via apt, configure as your dm, off you go.

---

### Post by durand on 2009-07-23
I'd vouch for slim. I'm using it on two computers, one old and one new and there is no noticable difference in performance between them.

---

### Post by johnraff on 2009-08-06
GDM might not take up a lot of resources once you're up and running, but it can add a few seconds to your bootup time on an older machine, if that bothers you.

I've no idea why you're getting the permission problem trying to run startx, but for what it's worth, here's how I'm starting xfce on an old laptop (260MHz, 196MB) running jaunty without gdm.

my .profile file (irrelevant complications removed)```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# set language - needed if not using gdm
export LANG=en_GB.UTF-8
export LANGUAGE=en_GB:en

# start X automatically if not already running, and using tty1
if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ] ;
then
    startx
fi

```
and my .xinitrc, likewise slightly cleaned up:```
#!/usr/bin/bash

# all messages added to .xsession-errors
exec >> $HOME/.xsession-errors 2>&1

# Set a background color during bootup
xsetroot -solid "#94A6B5"

# start scim daemon - needed for Japanese, for example, and usually started by gdm
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
scim -d &

exec startxfce4

```To be honest, I'm not quite sure if the "exec" is necessary or not, but it's usually recommended. Anyway this is working for me.

---

