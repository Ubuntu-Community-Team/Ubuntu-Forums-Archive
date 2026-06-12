---
title: "Where to define user's desktop environment for VNC connections"
date: 2014-03-31
forum: Desktop Environments
---

### Post by ccReynolds on 2014-03-31
I'm having trouble figuring out where the desktop environment a user wants is defined.  I have a headless workstation setup at home that is running x11vnc for the server and I connect to with TightVNC.  I can log in with different users and get a unique desktop for each.  However, I can't figure out where to define what environment the VNC connection uses.  It always defaults to Unity.  I have gnome-fallback installed and I would like to use that.

My original install was 12.04 LTS Desktop.  I have made the following changes:
/etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```

I have set the following in ~/.dmrc:
```
[Desktop]
Session=gnome-fallback
```
I have set the following in /etc/lightdm/lightdm.conf:
```
[SeatDefaults]
greeter-session=unity-greeter
user-session=gnome-fallback
```
~/.xsession
> gnome-session --session=gnome-fallback

---

### Post by slickymaster on 2014-03-31
[How to change to other desktop environment on VNC sessions]("http://askubuntu.com/questions/352232/how-to-change-to-other-desktop-environment-on-vnc-sessions")

---

### Post by ccReynolds on 2014-04-05
[FONT=Courier New]I tried the instructions and it did not help.  

I created a ~/.vnc/xstartup file as executable & added the following:

```
#!/bin/sh

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
if [ -r "$HOME/.Xresources" ]
then
        xrdb "$HOME/.Xresources"
fi

gnome-session --session=gnome-fallback &
```
[/FONT]

---

### Post by steeldriver on 2014-04-05
AFAIK the ~/.vnc/xstartup file is only used by independent VNC servers (vnc4server / tightvncserver) - x11vnc is intended as a 'desktop sharing' VNC server i.e. it doesn't start a session of its own, it just relays whatever desktop the user's 'real' X server is running on. That will be set when the user logs in via lightdm (and defaults to the user's previous session - saved via /var/lib/AccountsService/users/ I think rather than ~/.dmrc).

---

### Post by ccReynolds on 2014-04-05
Thanks for the info.  That was a detail I had not picked up on.  The VNC connection is not using what is set in /var/lib/AccountsService/users.  That file has a different desktop and wallpaper in its config file.

I am using xvfb with x11vnc.  Could that be forcing it to look somewhere else?

---

### Post by ccReynolds on 2014-04-07
I'm still baffled by where the system is looking to come up with the unity desktop.  It was still trying to pull up Unity after I completely uninstalled unity-desktop.  I was finally able to get the result I wanted by performing the following:

Original startup line from putty:
```
x11vnc -nofbpm -noxdamage -create -usepw -geometry 1280x1024 -auth ~/.Xauthority &
```

Started x11vnc with the previous command plus the following to clean out the previous session:
```
-gone 'killall Xvfb'
```

Closed the vnc connection.  Then removed the -gone 'killall Xvfb' bit and added the following:
```
-env FD_PROG=/usr/bin/gnome-session-fallback
```

Even after this is done, if I try to restart using the original string unity tries to come up.

Got the idea for the mods to the x11vnc command here:
[http://www.richud.com/wiki/Ubuntu_Fluxbox_GUI_with_x11vnc_and_Xvfb](http://www.richud.com/wiki/Ubuntu_Fluxbox_GUI_with_x11vnc_and_Xvfb)

---

### Post by steeldriver on 2014-04-07
What's the advantage of using x11vnc+Xvfb? if you install a standalone VNC server (like tightvncserver or vnc4server) you would be able to specify whatever session you want via ~/.vnc/xstartup

---

### Post by ccReynolds on 2014-04-08
I liked the fact that you had more than just one option for frame buffers e.g. Xdummy, and I liked the that it had the option to automatically close after you end your session.  However, it was probably based more on the fact that I found better examples for it than any sound technical reason.

> **steeldriver said:**
> What's the advantage of using x11vnc+Xvfb? if you install a standalone VNC server (like tightvncserver or vnc4server) you would be able to specify whatever session you want via ~/.vnc/xstartup

---

