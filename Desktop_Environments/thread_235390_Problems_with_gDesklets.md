---
title: "Problems with gDesklets"
date: 2006-08-13
forum: Desktop Environments
---

### Post by mg3kc on 2006-08-13
I have installed gDesklets using apt and the shell has installed without any problems. Some of the desklets which I have downloaded work, and some don't. Most of the ones which don't come up with an error message that they are unable to find a control.

The one which I really wanted was the XMMS corner desklet... I have install python-xmms and the dependancies, but I still get the same error (I tried opening the desklet while XMMS was open, still no joy). 

Any help would be very much appreciated

---

### Post by justinjstark on 2006-08-13
[https://launchpad.net/distros/ubuntu/+source/gdesklets-data/+bug/52683](https://launchpad.net/distros/ubuntu/+source/gdesklets-data/+bug/52683)

GDesklets is really in a bad situation.  New website that sucks, no recent versions or news, deprecated desklets, etc etc.  On top of that, the gdesklets-data package contains a lot of outdated desklets which no longer work.  I think gdesklets should be dropped from the repositories all together until the gdesklets developers can get their shit together.

Also, because of

[https://launchpad.net/distros/ubuntu/+source/gdesklets-data/+bug/52684](https://launchpad.net/distros/ubuntu/+source/gdesklets-data/+bug/52684)

it is not possible to install gdesklets without gdesklets-data.

So, the only solution is to install gdesklets with gdesklets-data, delete /usr/share/gdesklets/Controls /usr/share/gdesklets/Sensors /usr/share/gdesklets/Displays, and then go to gdesklets.org and download desklets that actually work with the latest version.

---

### Post by Polygon on 2006-08-13
so all those deklets on gdesklets.gnome.org are outdated and dont work? cause there are some that arnt on the new site that i want...

---

### Post by justinjstark on 2006-08-13
> **Polygon said:**
> so all those deklets on gdesklets.gnome.org are outdated and dont work? cause there are some that arnt on the new site that i want...

Yep, the architecture of gdesklets-core has changed to the point that old desklets throw errors and most do not work.  I thought about starting up a project to update all of those old desklets but don't really have the time.

---

### Post by mg3kc on 2006-08-13
I have been investigating alternatives to gDesklets, and I came across aDesklets...

I think it has a few problems with Xgl/Compiz (desklet backgrounds display with artefacts of whatever windows were already open on the desktop... solution, open them over a blank desktop) but other than that they seem to work fairly well. This is the first time I have had a working volume control, weather widget and slideshow on my linux desktop!

I will be sticking with adesklets until gDesklets get their act together and update the gdesklets-data package with working desklets in it!

Warning - adesklets requires more knowledge than gdesklets as the majority of what you need to do has to run from a shell. However, the adesklets --help command is useful!

M

---

