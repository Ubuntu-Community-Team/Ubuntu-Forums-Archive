---
title: "Different flavors of Ubuntu for different users?"
date: 2008-01-04
forum: Desktop Environments
---

### Post by anacaona on 2008-01-04
Hello all!

Been using Ubuntu as my primary OS for over two years now (almost never boot into Windows) and I'm very happy with it - asides from a few minor quibbles here and there.

I was wondering if there's anyway to use different flavors of Ubuntu for different users. For example.
User1: ubuntu
User2: kubuntu
User3: edubuntu

Was wondering cuz I wanted to install the edubuntu packages for my kids, but remember the last time I tried to do so (long time ago, 2 years ago it seems) it changed all the eyecandy and themes across the board.

I'm already a bit miffed that I can't seem to restore my ubuntu splash since I installed kubuntu-desktop (and yes, I've googled and searched the forum but none of the techniques seem to work on my Gutsy install)...

If anyone could point me in the right direction I'd be very grateful.

---

### Post by mojoman on 2008-01-04
I really don't know anything about edubuntu but I guess it's the same thing as with x/k/ubuntu, i.e. the core is the same, they only differ in desktop environment and applications. Ubuntu = core + Gnome + certain set of application, Xubuntu = core + Xfce4 + slightly other (lighter) set of applications, Kubuntu = core + KDE + oter set of applications. So, there is really no conflict inherent in having it all installed, though this will severely clutter your menus, as you will have TONS of applications on it, and a lot of these will simply do the same thing and eat up space. Also, some will be more memory intensive (for example, using Nautilius, the Gnome filemanager, when you use KDE will draw resources from a lot of Gnome libraries so that will slow down things, whereas Konqueror, the KDE file manager will use libraries that KDE already uses, thus allowing economy of resources).

I'd recommend that you go with a Ubuntu and Edubuntu setup (edubuntu uses Gnome I think so you'd get some economy of resource) and stay out of KDE. GDM login manager will remember what environment that is default. On top of your Ubuntu, install the edubuntu-desktop or perhaps a lighter variant. Use synaptic and search for edubuntu and you can see what options you have. IF you must use KDE, go with kde-core. That will install a minimal variant and you can add what more you'd like (there are some excellent KDE stuff that I use with fluxbox, just because they are SO good, such as K3B, Amarok and Soundkonvertor). 

/mojoman

---

### Post by icheyne on 2008-01-04
This tip might be useful: [http://lifehacker.com/software/linux-tip/hide-kde-apps-in-gnome-menus-280027.php](http://lifehacker.com/software/linux-tip/hide-kde-apps-in-gnome-menus-280027.php)

---

