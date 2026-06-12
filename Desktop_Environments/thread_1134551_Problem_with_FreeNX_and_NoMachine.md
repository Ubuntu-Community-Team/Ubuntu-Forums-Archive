---
title: "Problem with FreeNX and NoMachine"
date: 2009-04-23
forum: Desktop Environments
---

### Post by swietowid on 2009-04-23
I am currently running Jaunty with FreeNX installed.  When I connect remotely to my box an try to start some apps (gedit for example) I get following warning:

Xlib:  extension "Generic Event Extension" missing on display ":1000.0".

Gedit still runs but I am not sure if there are some other problems.  This was not happening in intrepid.

Anyone has any ideas?

---

### Post by walkingsp on 2009-04-25
I have exactly the same problem on the two machines that I am using. I searched on the web, but had no luck. I guess it is freeNX's problem. Maybe the only solution is to wait for the next release of freeNX.

---

### Post by freakalad on 2009-10-04
Same issue (standard apps like gedit's fine; issues with video-heavy apps like glxgears); I'm trying to work a video issue when connecting to VM (libvirt/KVM) clients (boxee, NBR, etc)

Using FreeNX server with QtNX client.

Already getting pretty good performance & other benefits (pointer-lock, etc), so overall I'm pretty happy thus far

---

### Post by urimax on 2009-10-13
I have the same problem. I don't know why when I login with NX client my gnome lost all apearance and ubuntu theme. Besides, Nvidia control panel thinks that X are not configured but I can run glxgears, very slow but runs...
----

Hi, I just found a solution for theme problem: [http://hydtech.wordpress.com/2009/08/19/freenx-problems-in-ubuntu-gnome-theme-screensaver-lock-screen-show-desktop-nxclient-and-nxserver/](http://hydtech.wordpress.com/2009/08/19/freenx-problems-in-ubuntu-gnome-theme-screensaver-lock-screen-show-desktop-nxclient-and-nxserver/)

but this don't repair nvidia control panel problem and Xlib extension on display 1000:0 problem

---

### Post by surgin on 2009-12-08
I have got the same problem, and fixed it following the introduction of this link:
[http://hydtech.wordpress.com/2009/08/19/freenx-problems-in-ubuntu-gnome-theme-screensaver-lock-screen-show-desktop-nxclient-and-nxserver/](http://hydtech.wordpress.com/2009/08/19/freenx-problems-in-ubuntu-gnome-theme-screensaver-lock-screen-show-desktop-nxclient-and-nxserver/) 
"""
[I]Run gconf-editor.
Navigate to /apps/gnome_settings_daemon/plugins/keyboard.
Uncheck the “Active” box on the right.
Log out and log back in.”[/I]
"""
hopefully It helps.

> **swietowid said:**
> I am currently running Jaunty with FreeNX installed.  When I connect remotely to my box an try to start some apps (gedit for example) I get following warning:

Xlib:  extension "Generic Event Extension" missing on display ":1000.0".

Gedit still runs but I am not sure if there are some other problems.  This was not happening in intrepid.

Anyone has any ideas?

---

