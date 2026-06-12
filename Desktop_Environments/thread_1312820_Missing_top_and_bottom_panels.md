---
title: "Missing top and bottom panels"
date: 2009-11-03
forum: Desktop Environments
---

### Post by blx_286 on 2009-11-03
I hope someone can point me in the right direction. I have managed to trash my top and bottom panels (they are missing). I think it may be related to removing Evolution.

I am running 9.04 (upgraded from 8.10) on a Dell Latitude D630 w/4GB of RAM.

I never could get Evolution to work right with Exchange and I got tired of the appointment notification appearing up by the clock. So I uninstalled Evolution. I then powered the machine down, upgraded the memory from 2GB to 4GB and powered it back up.

When Gnome comes back up, I get the wallpaper and my desktop icons, but no panels (top or bottom). After searching, I tried the following:

```
laptop:/$ gconftool --recursive-unset /apps/panel
laptop:/$ sudo rm -rf ~/.gconf/apps/panel
laptop:/$ sudo killall gnome-panel
gnome-panel: no process killed

laptop:/$ gnome-panel
The program 'gnome-panel' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel
bash: gnome-panel: command not found
laptop:/$
```

I then installed gnome-panel.

```
laptop:/$ sudo aptitude install gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  evolution-data-server{a} evolution-data-server-common{a} gnome-applets{a} 
  gnome-panel indicator-applet{a} indicator-messages{a} 
  libedataserverui1.2-8{a} 
The following packages will be REMOVED:
  epiphany-browser-dbg{u} evince-dbg{u} gimp-dbg{u} 
  gstreamer0.10-plugins-base-dbg{u} gstreamer0.10-plugins-good-dbg{u} 
  gstreamer0.10-plugins-ugly-dbg{u} libatk1.0-dbg{u} libatspi-dbg{u} 
  libfontconfig1-dbg{u} libgail-gnome-dbg{u} libgda3-3-dbg{u} 
  libgda3-sqlite{u} libglib2.0-0-dbg{u} libgnomedb3-4{u} 
  libgnomedb3-4-dbg{u} libgnomedb3-bin{u} libgnomedb3-common{u} 
  libgnomeui-0-dbg{u} libgnomevfs2-0-dbg{u} libgoffice-0-6{u} 
  libgoffice-0-6-common{u} libgoffice-dbg{u} libgsf-1-114-dbg{u} 
  libgsf-gnome-1-114{u} libgsf-gnome-1-114-dbg{u} libgstreamer0.10-0-dbg{u} 
  libgtk2.0-0-dbg{u} libgtkhtml3.14-dbg{u} libloudmouth1-0{u} 
  libloudmouth1-0-dbg{u} libnspr4-0d-dbg{u} libnss3-1d-dbg{u} 
  liboobs-1-4-dbg{u} libopal3.6.1{u} libpango1.0-0-dbg{u} libpt2.6.1{u} 
  libpt2.6.1-plugins-alsa{u} libpt2.6.1-plugins-v4l2{u} libxft2-dbg{u} 
  libxml2-dbg{u} nautilus-dbg{u} rhythmbox-dbg{u} totem-dbg{u} 
0 packages upgraded, 7 newly installed, 43 to remove and 0 not upgraded.
Need to get 1286kB of archives. After unpacking 152MB will be freed.
Do you want to continue? [Y/n/?] y
```

I then launched gnome-panel and get a pop-up box error:

```
The Panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".
Do you want to delete the applet from your configuration?
```

This is what the Terminal window is showing:

```
laptop:/$ gnome-panel
** (gnome-panel:8722): DEBUG: Adding applet 0.
** (gnome-panel:8722): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:8722): DEBUG: Adding applet 1.
** (gnome-panel:8722): DEBUG: Adding applet 2.
** (gnome-panel:8722): DEBUG: Adding applet 3.
** (gnome-panel:8722): DEBUG: Adding applet 4.
** (gnome-panel:8722): DEBUG: Adding applet 5.
** (gnome-panel:8722): DEBUG: Adding applet 6.
** (gnome-panel:8722): DEBUG: Adding applet 7.

** (gnome-panel:8722): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_FastUserSwitchApplet:
(null)
** (gnome-panel:8722): DEBUG: Adding applet 8.
** (gnome-panel:8722): DEBUG: Adding applet 9.
** (gnome-panel:8722): DEBUG: Adding applet 10.
** (gnome-panel:8722): DEBUG: Adding applet 11.

(gnome-panel:8722): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:8722): DEBUG: Adding applet 12.
```

If I keep the Terminal window open, the panels reappear. But Gnome is not completely loading and returning to a prompt. If I Ctrl-C, the panels disappear.

While I had the panels visible, I used Synaptic Package Manager to install Evolution. But I still have the same panel problem.

Any help would be greatly appreciated.

Tim

---

### Post by realzippy on 2009-11-03
When kicking your evolution you probably have kicked 

evolution-data-server-common,what kicked gnome-panel and so on.
Try:

sudo apt-get install evolution-data-server-common

or this:

sudo apt-get install fast-user-switch-applet gnome-applets libedataserverui1.2-8 gnome-panel

---

### Post by blx_286 on 2009-11-03
> **realzippy said:**
> sudo apt-get install fast-user-switch-applet gnome-applets libedataserverui1.2-8 gnome-panel

That did the trick. Thanks for the help and the fast response.

Tim

---

### Post by realzippy on 2009-11-03
When uninstalling with synaptic always watch the dependency packages
that get kicked also,synaptic does that without warning...

---

