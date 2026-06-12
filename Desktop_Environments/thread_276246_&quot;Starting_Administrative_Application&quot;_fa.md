---
title: "&quot;Starting Administrative Application&quot; fails"
date: 2006-10-12
forum: Desktop Environments
---

### Post by gcreedon on 2006-10-12
For some reason, today, when I click on an administrative function, like the Update Manager, instead of being asked for my password, there is a message in the lower left hand part of the screen stating: "Starting Administrative Application". This stays on briefly, then closes and my application then fails to launch.

Thoughts? Thanks in advance!

---

### Post by David Corrales on 2006-10-13
Try launching it from the command line. You'll get a lot more information that way.

---

### Post by Tomosaur on 2006-10-18
I was also having this problem, but a little tinkering finally solved it. There were actually two problems, and it took me a while to find and fix both.

I can't remember exactly what the method to solve it was, but I remember downloading lots of packages - these I remember were included (all latest versions available, but DO NOT DOWNLOAD FROM ANYWHERE OTHER THAN UBUNTU REPOS, because that just gave me a whole load more problems)
bonobo
libbonobo
glade (and all related packages)
libglade
libc6
glib

you also need python2.4, and all packages relating to launchpad-integration.

To get gnome-app-install to work again, you need to do the following:
```

cd /usr/lib/python2.4/site-packages/AppInstall/
sudo cp -r ../gtk-2.0/LaunchpadIntegration ./
sudo cp ../gtk-2.0/gtkhtml2.* ./

```

Hope that helps you out a little.

---

