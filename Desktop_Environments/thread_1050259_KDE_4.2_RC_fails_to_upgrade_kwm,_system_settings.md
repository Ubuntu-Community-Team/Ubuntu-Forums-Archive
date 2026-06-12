---
title: "KDE 4.2 RC fails to upgrade kwm, system settings"
date: 2009-01-25
forum: Desktop Environments
---

### Post by gnuvistawouldbecool on 2009-01-25
Well, this worked for me before, but since then I've had to reinstall my system, and now these two packages won't install, and obviously kwm is necessary to use KDE.

So I'm not entirely sure why it isn't working, but here's what it comes up with.  I'm tempted to delete the packages it's using and redownload them, but I don't know if thats advisable or not.

```
Preparing to replace kde-window-manager 4:4.1.3-0ubuntu1~intrepid1 (using .../kde-window-manager_4%3a4.1.96-0ubuntu4~intrepid1~ppa1_i386.deb) ...
Unpacking replacement kde-window-manager ...
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.1.96-0ubuntu4~intrepid1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/share/kde4/apps/kconf_update/plasma-add-shortcut-to-menu.upd', which is also in package kdebase-workspace-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace systemsettings 4:4.1.3-0ubuntu1~intrepid1 (using .../systemsettings_4%3a4.1.96-0ubuntu4~intrepid1~ppa1_i386.deb) ...
Unpacking replacement systemsettings ...
dpkg: error processing /var/cache/apt/archives/systemsettings_4%3a4.1.96-0ubuntu4~intrepid1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/kcm_fonts.so', which is also in package kdebase-workspace-bin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.1.96-0ubuntu4~intrepid1~ppa1_i386.deb
 /var/cache/apt/archives/systemsettings_4%3a4.1.96-0ubuntu4~intrepid1~ppa1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm currently using 8.10, standard install with Kubuntu-desktop added.

---

### Post by gnuvistawouldbecool on 2009-01-26
I used the apt-get clean command to get rid of the packages, and redownloaded them.  They still fail to install.  Why?

---

### Post by wieszti on 2009-01-28
a have this bug too, ubuntu 8.10

---

### Post by alpho2k on 2009-01-29
Same bug here!

---

### Post by alpho2k on 2009-01-31
I finally removed completely kubuntu with this command in this topic : [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

and reinstall kubuntu-desktop and upgrade again to kde to 4.2.

This time, it worked very well. I think the problem was that I had kaffeine and amarok-kde4 already installed on my ubuntu.

---

### Post by gnuvistawouldbecool on 2009-02-01
Yeah, uninstalling and reinstalling worked for me, too.

---

