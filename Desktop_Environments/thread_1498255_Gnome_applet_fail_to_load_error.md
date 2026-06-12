---
title: "Gnome applet fail to load error"
date: 2010-05-31
forum: Desktop Environments
---

### Post by cyrylski on 2010-05-31
I've encountered a strange error, it doesn't seem very common on this forum (at least search didn't give results).

It was a bug on launchpad, though.

The problem: Gnome Applets Fail to Load on startup. 

Issue does not repeat after log out/log in.

The message is: 

> gnome-panel failed to load applet OAFIID:GNOME

and then it gives the applet name. The ones that freeze are
Desktop Switcher, Notifications Applet, WiFi connection indicator and a couple of other ones which have been installed by default. 

What may be the problem? It occurs regularly on startup, disappears if I log out and log in back again.

---

### Post by timcredible on 2010-06-21
i have the same issue - does it quite often.  i enable ctrl-alt-backspace to be able to quit gnome, but i'd rather find a solution for the problem.

---

### Post by DZ* on 2010-06-21
> **cyrylski said:**
> It occurs regularly on startup, disappears if I log out and log in back again.

This seems to be related to slow disk access. I had this error popping up every time I'd boot one of two laptops, one Ubuntu, the other one Fedora. Had to log out and log back in. Very annoying.

What they had in common was full disk encryption and ext3.

First, I added noatime to fstab options, but that alone was not enough. The problem went away completely after I migrated ext3 to ext4 following instructions from [http://www.debian-administration.org/article/Migrating_a_live_system_from_ext3_to_ext4_filesystem](http://www.debian-administration.org/article/Migrating_a_live_system_from_ext3_to_ext4_filesystem)

I also migrated files in /home, /usr, /opt to extents as described on that page.

I've never seen that error again on either of the machines. It's been several months now since I made the migration.

---

### Post by akwala on 2010-10-10
On Lucid (10.04.1), a varying number of gnome-panel applets fail to load at startup. My file system is /ext4.

'kill-all gnome-panel' (via keyboard shortcut) after startup fixes the panels, but I'd rather not have to do it.

---

### Post by Brzhk on 2010-10-11
i'm experiencing the same as akwala. Although, i'm on Karmic. I have no idea if this is relevant, but i have compiz & docky running as well.

---

### Post by rdhedgepath2 on 2010-11-06
I had a the same issue this morning.  Yesterday I had some hard drive errors that caused files to be corrupted.  I had to reinstall several packages to fix numerous issues. 

To fix this particular issue I ran the following command.  Basically reinstalled all packages that were dependent on libbonobo*.  I know it was overkill, but it worked for me.

```
sudo apt-get install --reinstall at-spi brltty-x11 gdm gdm-guest-session gnome-about gnome-applets gnome-dictionary gnome-mag gnome-orca gnome-panel gnome-panel-dbg gnome-power-manager gnome-utils gok indicator-applet indicator-applet-session libatspi1.0-0 libbonobo2-0 libbonobo2-bin libbonobo2-common libbonoboui2-0 libbonoboui2-common libgail-gnome-module libgnome-speech7 libgnome2-0 libgnome2-perl libgnome2.24-cil libgnomepanel2.24-cil libgnomeui-0 libpanel-applet2-0 mousetweaks nautilus-share python-gnome2 python-gnomeapplet python-pyatspi rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store system-config-printer-gnome tomboy tsclient ubuntu-desktop usb-creator-gtk vinagre libbonobo2-0 libbonobo2-bin libbonobo2-common libbonoboui2-0 libbonoboui2-common
```

---

