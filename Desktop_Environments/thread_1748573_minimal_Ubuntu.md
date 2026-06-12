---
title: "minimal Ubuntu"
date: 2011-05-03
forum: Desktop Environments
---

### Post by tubunu on 2011-05-03
Hello,
I've been trying to install a minimal Ubuntu using mini.iso and have a couple of questions to you, wise heads :)


```
sudo apt-get install xorg gdm gnome-core
``` 

gives me gnome without all "unnecessary" applications, but it also gives me things like evolution and a couple of others which I don't need/want. Is there a way to install the bare minimum of gnome, but without **any** of these applications? 

Thanks for any insight.

---

### Post by tubunu on 2011-05-04
I'm actually surprised gnome-core depends on Evolution, etc. So technically speaking it's not really possible to install "your very own" minimal version as there will always be dependencies that depend on other dependencies... mmm.. am I right to assume that?

---

### Post by nothingspecial on 2011-05-04
Evolution is part of gnome, as are evince nautilus and gedit.  Just as thunar is part of xfce.

If you want truly minimal, go with openbox or similar.

---

### Post by Frogs Hair on 2011-05-04
Yes , I learned this with my first Ubuntu installation . I began removing application I did not use such as Evolution and others .

I was going remove the Gnome system monitor and use Htop instead and I got a message that this would remove Gnome desktop.

I'm not using mini so now I leave well enough alone and remove the unused items from the main menu and my last three installations have been very stable.

---

### Post by gatewayasteroid on 2011-05-04
> **tubunu said:**
> Hello,
I've been trying to install a minimal Ubuntu using mini.iso and have a couple of questions to you, wise heads :)


```
sudo apt-get install xorg gdm gnome-core
``` 

gives me gnome without all "unnecessary" applications, but it also gives me things like evolution and a couple of others which I don't need/want. Is there a way to install the bare minimum of gnome, but without **any** of these applications? 

Thanks for any insight.

apt-get accepts the "--no-install-recommends" option, use it (at your own risk) ;)

---

### Post by urukrama on 2011-05-07
> **gatewayasteroid said:**
> apt-get accepts the "--no-install-recommends" option, use it (at your own risk) ;)

Evolution is a dependency of [gnome-core]("http://packages.ubuntu.com/natty/gnome-core"), not just a recommended package, so that command won't help the OP.

You could install [Xfce]("http://packages.ubuntu.com/natty/xfce4"), which comes with very few additional applications (other than a file manager and a calendar), or Openbox, which is just a window manager without anything else (power management tools, theme settings controls, panels, desktop, etc.), though you can easily add those yourself. If you're interested in Openbox, have a look at the guide linked to in my signature (it is a little outdated, but should be of some use).

---

### Post by gatewayasteroid on 2011-05-07
> **urukrama said:**
> Evolution is a dependency of [gnome-core]("http://packages.ubuntu.com/natty/gnome-core"), not just a recommended package, so that command won't help the OP.

You could install [Xfce]("http://packages.ubuntu.com/natty/xfce4"), which comes with very few additional applications (other than a file manager and a calendar), or Openbox, which is just a window manager without anything else (power management tools, theme settings controls, panels, desktop, etc.), though you can easily add those yourself. If you're interested in Openbox, have a look at the guide linked to in my signature (it is a little outdated, but should be of some use).

Ok sorry, I should have read better.
Anyway I'm using openbox all the time, together with tint2, wbar, conky and pcmanfm. ;)

---

### Post by tubunu on 2011-05-12
Thank you everyone for great tips.

---

### Post by Sylslay on 2011-05-12
Very good topic:

So if I like install bare xserver with with lxde desktop and network-manager

and list of apps:

pidgin, skype, firefox, document viewer, mc,

vlc for media player or something smaller

and codec (What is bare mininume for codecs in linux?/ mp3, avi, rmvb )

ffmpg and flash player?


Please wrote absolute minimum how install that:

1. Setup cable eth0 and connect to router

network settings All DHCP or static

gate: 192.168.0.1
ip : 192.168.0.11
netmask: 255.255.255.0

dns: 8.8.8.8

2. list here all:

sudo apt-get install ???

 - sudo apt-get install xorg lxde

Anyone seen similar post on Ubuntu/Debian forums?

[http://www.wikihow.com/Install-Minimal-Ubuntu-Linux](http://www.wikihow.com/Install-Minimal-Ubuntu-Linux)

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

