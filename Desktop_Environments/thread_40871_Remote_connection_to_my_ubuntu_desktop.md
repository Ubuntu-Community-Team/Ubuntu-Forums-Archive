---
title: "Remote connection to my ubuntu desktop?"
date: 2005-06-10
forum: Desktop Environments
---

### Post by aeromaverick on 2005-06-10
hi guys

i have ubuntu installed on my desktop in my office. i have windows xp on my laptop. how can i remotely connect to my linux desktop in my office from my laptop using windows. i have all the address i need to connect. 

thanks

aeromaverick

---

### Post by dtessier on 2005-06-10
On your Ubuntu PC, go to "System -> Preferences -> Remote Desktop", to ensure that desktop sharing is enabled.

Then, on the WinXP side, you can use [TightVNC](http://tightvnc.org/) to access it.

---

### Post by spudley on 2005-06-10
Just wondering if there is a quick and easy way to allow for multiple VNC connections to 'virtual' desktops...

ie: vncviewer hostname:0 (is the current 'remote desktop'), but I'd like
vncviewer hostname:1
vncviewer hostname:2
etc

to be available... I had this setup on a RedHat install quite some time ago, but that was a 'painful' experience for me (linux-newbie).  Ubuntu seems so much simpler so far.

---

### Post by cwaldbieser on 2005-06-11
I am not sure exactly what you have in mind, but if you are using the vncserver program (instead of vino, which is built into Gnome), I believe you can run it for as many different displays as you want.  Each creates a "psuedo desktop" which is almost like a user just logging into a new session.

So for example, you could ssh into the Ubuntu server (with PUTTY, for example) and:

$ vncerver :1
$ vncserver :2
$ vncserver :3

and then from various VNC clients (Windows, Linux, Macs, or whatever), you could VNC into those different displays.

---

