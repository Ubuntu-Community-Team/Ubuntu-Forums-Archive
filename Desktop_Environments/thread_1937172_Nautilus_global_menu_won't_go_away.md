---
title: "Nautilus global menu won't go away"
date: 2012-03-07
forum: Desktop Environments
---

### Post by trelirodia on 2012-03-07
Hi there, 

I recently updated and all of a sudden the nautilus global menu appeared on top of the screen.

I am running unity and I've modified it using CCSM and I really don't want to have the global menu.

I've tried removing it by:
1) sudo su
echo "export UBUNTU_MENUPROXY=0" > /etc/X11/Xsession.d/81ubuntumenuproxy

and then reboot, but no joy.
When I echo $UBUNTU_MENUPROXY it still says libappmenu.so 

2) removing appmenu-gtk appmenu-gtk3 appmenu-qt indicator-appmenu
and then reboot, but still no joy. 
There is no libappmenu.so under /usr/lib/gtk-3.0/3.0.0 or /usr/lib/gtk-2.0/2.10.0

That nasty thing is still on top of my screen.

The only way to make it disappear is to start nautilus --no-desktop
But then I lose the desktop icons and functionality, which I'd rather keep.
 
Any ideas what else I could do?

Many thanks for the help
xxx

Ps. I'm running ubuntu 11.10 64bit version

---

### Post by Frogs Hair on 2012-03-07
Run the following command  and  restart .```
echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && [ "$DESKTOP_SESSION" != "ubuntu-2d" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```

---

### Post by trelirodia on 2012-03-07
Thanks for taking the time to respond Frogs Hair.

As I mentioned in my original post, I've already tried this solution and it doesn't work for me (fyi I am actually using the ubuntu, aka unity 3D, session, so the first part of your command is irrelevant here)

For some reason creating the file under Xsession.d is not unsetting/setting to zero UBUNTU_MENUPROXY. As soon as I reboot UBUNTU_MENUPROXY is set back to libappmenu.so

The fact that this file no longer exists makes me think that the recent update to Nautilus changed the way the global menu works and it no longer uses libappmenu.so ... 

Any other ideas?
Thanks,
M

---

### Post by Frogs Hair on 2012-03-07
Sorry about that ! 
 
I think the Unity potion of the command can be changed to ubuntu-3d . Turning off the nautilus handle desktop option is not practical . Sliding the panel transparency setting in the unity plugin will hide the nautilus panel , but it is only a work around. I don't know of anything else to try at the moment .

---

### Post by aok on 2012-03-19
I got this problem too but had been ignoring it. I had thought it was my Firefox menu but the Nautilus menu makes more sense.

---

### Post by Koala Kid on 2012-03-19
same here... tried all of the proposed solutions, no luck.

---

### Post by trelirodia on 2012-03-24
Since I removed the packages relating to the global menu, I now just have a black strip on the top of my screen, where the panel used to be.

This strip has nothing on it and I can't seem to find a way to remove it as long as Nautilus manages the desktop. 

The only alternative I can think at the moment is to ditch Nautilus and use other file managers e.g. dolphin. 

We'll see how that goes. 
What a disappointment though ... :-(

---

### Post by Frogs Hair on 2012-03-25
I have been testing Marlin for a month or so . There is an option to set it as default in preferences . I don't if this would solve the problem though .
Marlin has crashed occasionally for some but I have had no problem.

[http://www.unixmen.com/how-to-install-marlin-file-manager-on-ubuntu-and-linuxmint-nautilus-alternative/](http://www.unixmen.com/how-to-install-marlin-file-manager-on-ubuntu-and-linuxmint-nautilus-alternative/)

---

### Post by trelirodia on 2012-03-29
I admit defeat ... :-(
The problem with replacing nautilus with other file managers, is that I am left with an unusuable desktop.
I actually use my desktop quite a bit and would rather keep using it.

With a heavy heart I decided to dump gnome and more on to KDE ... I never thought I'd ever return to KDE, but here it goes.

It's still more buggy and heavier than gnome, but hey I got rid of that silly bar and KDE has much more flexibility in terms of customization :-)

Thanks for all your responses,
M

---

