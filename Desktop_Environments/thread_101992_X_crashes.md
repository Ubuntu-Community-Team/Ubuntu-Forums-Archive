---
title: "X crashes"
date: 2005-12-11
forum: Desktop Environments
---

### Post by mihaita on 2005-12-11
after I install ubuntu i can see the login screen, i enter my username and password, and after that i see an empty background and the curssor. nothing else starts.. what can i do?

---

### Post by rubinstein on 2005-12-11
Try to login at gdm with the failsafe mode under session (or something similar).

---

### Post by tauko on 2005-12-11
I've a similar problem. When I start the computer and try to loguin directly to Gnome it loads the background image (wallpaper), but when it should appear the starting panel (where it tells that it's loading metacity, etc...) it stops reading the HD and remains there doing nothing. You only have the wallpaper and the mouse loaded. Nothing else works.

I can enter Gnome only if I have been inside before (without rebooting) or if I start IceWM, open there a GTK2 & Gnome application (for example GTKwifi and gnome-panel) and then I log of and log in again with Gnome.

It's like it needs something to be loaded before starting Gnome, and it isn't on the /etc/rcX.d or  /etc/init.d folders....

If I'm not mistaken, the ony things I did in the last sesion where Gnome started alright was removing wpasupplicant.

Any ideas?

---

### Post by mihaita on 2005-12-11
that's exactly my problem too!

---

### Post by tauko on 2005-12-11
I've read something about the bonobo package, it seems it gave this error in a earlier version. I don't think it has anything related with what it's happening to us.

Tried to loguin (I've gdm) with Gnome and Gnome failsafe, these two don't do anything. IceWM works and the one that opens a terminal window also works.

Does Gnome log somewhere what happpens when it starts a session?

---

### Post by tauko on 2005-12-11
Wel... it seems it was a networking fault!

Try doing ```
ifconfig
``` and then check if you have the loopback interface running. If it is, then you should see something like this:
*lo        Link encap:Local Loopback* (with more lines below)

If you don't have it there... then I think I can help... Check your interfaces configuration:

```
cd /etc/network
```
```
nano interfaces
```

In there you should see a line like this: *iface lo inet loopback*
If it isn't there write it, save and restart. Then it should work.

In my particular case I already had it, but I had hotplug with bad configuration. I have done something like this to get it working:

1. add *auto lo* in the interfaces file, just before this *iface lo inet loopback*   (and save)

2. reconfigure hotplug
```
dpkg-reconfigure hotplug
```

I choosed the *auto* option and after the *No* one.

Hope it helps!

---

