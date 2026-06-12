---
title: "Xubuntu-artwork package"
date: 2013-12-23
forum: Desktop Environments
---

### Post by Andrew_Lucas on 2013-12-23
Hi all,

I want to create a slideshow for the desktop wallpaper, on Xubuntu. xubuntu-artwork package is installed by default (I'm running 13.10), but I can't seem to find if/where it puts the wallpapers (to manually add to create a list for the slideshow).

It's not: /usr/share/xfce4/backdrops (only 4 in there, all the default), or /usr/share/xubuntu (a bunch of others I tried too; no luck, e.g. /usr/share/backgrounds).

If I'm mistaken, and this doesn't provided any wallpapers, can anyone recommend a package which does (and where it'll put those wallpapers when installed)?

Note: this install isn't actually mine, but something I'm doing for my 13 year old sister (I'm working on setting up a good looking base system, which she can then modify as needed according to her preferences, but I'd like to have something with a bit more sparkle as the default when I hand the system to her).

Cheers!

---

### Post by ajgreeny on 2013-12-23
You may need the **xfce4-artwork** package as it contains many more wallpaper files.  In fact the xubuntu-artwork package has no wallpaper files; I think they are in **xubuntu-wallpapers** package.

---

### Post by Andrew_Lucas on 2013-12-23
At least from the terminal, apt-cache search isn't especially illuminating as to the contents of those packages.

However, xubuntu-wallpapers, xfce4-artwork, and xfce4-goodies (which came up in the search result) only come to 19.7MB combined. Seems a little small if it contained numerous wallpapers?

---

### Post by Frogs Hair on 2013-12-23
The goodies package is usually installed along  with the XFCE stand alone session , below is the description from synaptic. ```
he "Goodies for Xfce" project includes additional software and artwork thatare related to the Xfce desktop, but not part of the official release.


This package will install the following Xfce4 related plugins:
  * Extra artwork (xfce4-artwork)
  * Battery levels monitor (xfce4-battery-plugin)
  * Clipboard history (xfce4-clipman-plugin)
  * CPU frequency management plugin (xfce4-cpufreq-plugin)
  * CPU utilisation graphs (xfce4-cpugraph-plugin)
  * Date and time plugin (xfce4-datetime-plugin)
  * Disk performance display (xfce4-diskperf-plugin)
  * Filesystem monitor (xfce4-fsguard-plugin)
  * Generic monitor, for displaying any command result (xfce4-genmon-plugin)
  * Mail watcher (xfce4-mailwatch-plugin)
  * Mount plugin (xfce4-mount-plugin)
  * Network load monitor (xfce4-netload-plugin)
  * Notes plugin (xfce4-notes-plugin)
  * Quick access to bookmarked folders, recent documents and removable
    media (xfce4-places-plugin)
  * Tiny launchers (xfce4-quicklaunchers)
  * Sensors plugin, frontend to lm-sensors (xfce4-sensors-plugin)
  * Smartbookmarks plugin (xfce4-smartbookmark-plugin)
  * System load monitor (xfce4-systemload-plugin)
  * Timer plugin (xfce4-timer-plugin)
  * Command line with history (xfce4-verve-plugin)
  * Wireless lan monitor (xfce4-wavelan-plugin)
  * Weather monitor (xfce4-weather-plugin)
  * Keyboard configuration (xfce4-xkb-plugin)
  * Archive management for Thunar (thunar-archive-plugin)
  * Media tags editor for Thunar (thunar-media-tags-plugin)


It'll install some standalone applications too:
  * Tiny text editor (mousepad)
  * Images viewer (ristretto)
  * Archive manager (squeeze)
  * CD/DVD burner (xfburn)
  * Frontend to dictionnaries (xfce4-dict)
  * Notification daemon (xfce4-notifyd)
  * Tool to take screenshots (xfce4-screenshooter)
  * Task manager (xfce4-taskmanager)
  * Terminal emulator (xfce4-terminal)



```

---

### Post by ajgreeny on 2013-12-24
I always use synaptic to install or remove packages and that gives you a chance to see exactly what files are installed and where they are placed in the filesystem.

Synaptic is so very much more informative, and much more flexible than the software-centre, which I **never** use.

---

### Post by Andrew_Lucas on 2014-01-17
> **ajgreeny said:**
> I always use synaptic to install or remove packages and that gives you a chance to see exactly what files are installed and where they are placed in the filesystem.

Synaptic is so very much more informative, and much more flexible than the software-centre, which I **never** use.

Yeah, me neither. I tend to prefer the terminal, though, it might be quite childish but hammering off commands is just incredibly satisfying. :D Clicking through a few menus just doesn't give the same buzz.

+1 about the software centre. I think I've looked into purging it before, but IIRC it's set as a dependancy for packages like xubuntu-desktop. I've satisfied myself with just hiding it from menus etc since.

---

