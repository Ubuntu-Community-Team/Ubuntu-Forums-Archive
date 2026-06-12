---
title: "xubuntu-core XFCE version on Ubuntu 14.04"
date: 2015-05-13
forum: Desktop Environments
---

### Post by lambdafox on 2015-05-13
I would like to run XFCE 4.12 on Ubuntu 14.04 LTS amd64.

If I use the minimal install disk and use sudo apt-get install xubuntu-core^

will it install XFCE 4.10 -- the default for Ubuntu 14.04 -- or XFCE 4.12, the latest and greatest?

Thank you.

---

### Post by Frogs Hair on 2015-05-13
See the linked page , I've used the 4.12 PPA in the past.  [http://www.webupd8.org/2015/03/install-xfce-412-in-xubuntu-1404-or.html](http://www.webupd8.org/2015/03/install-xfce-412-in-xubuntu-1404-or.html)

---

### Post by lambdafox on 2015-05-14
Unfortunately, that method appears to only work with the ***full version of Xubuntu***.  That is Plan B if the ubuntu-core will not install 4.12 on the minimal install of Ubuntu 14.04.  (Plan A would save me a lot of time, though!)

> **Frogs Hair said:**
> See the linked page , I've used the 4.12 PPA in the past.  [http://www.webupd8.org/2015/03/install-xfce-412-in-xubuntu-1404-or.html](http://www.webupd8.org/2015/03/install-xfce-412-in-xubuntu-1404-or.html)

---

### Post by Bucky Ball on 2015-05-14
Open software Centre> look for and install xfce4> log out> Choose 'xfce session' from the Sessions menu> Log in. That's it. You are now using xfce4 desktop environment. DON'T install xubuntu-desktop. That is going to drag in all of the Xubuntu apps and dependencies causing bloat and confusion. That approach equates to installing Ubuntu AND Xubuntu on the same box. You don't want that. You only want the desktop environment by the sounds, xfce4. That's simple.

---

### Post by lambdafox on 2015-05-14
This doesn't answer my question...

> **Bucky Ball said:**
> Open software Centre> look for and install xfce4> log out> Choose 'xfce session' from the Sessions menu> Log in. That's it. You are now using xfce4 desktop environment. DON'T install xubuntu-desktop. That is going to drag in all of the Xubuntu apps and dependencies causing bloat and confusion. That approach equates to installing Ubuntu AND Xubuntu on the same box. You don't want that. You only want the desktop environment by the sounds, xfce4. That's simple.

Since it seems people are getting confused, I will give a little more background...

Over the past few months I have been test driving linux as a replacement for XP Classic Desktop -- which MS recently killed.  I never went to Windows 7 or beyond, because as I have been saying for years, if I wanted a MAC I would just get a mac, LOL.

I have tried several distros from Ubuntu and Debian with different desktops, window managers, etc.

I prefer XFCE 4.12 to any that I have used so far.  The windows manager, desktop manager, panel, session manager, and thunar are my top choices.  I use a lot of multimedia; so, alsa is a must.

But my applications of choice are:

medit text editor
lilyterm terminal
palemoon browser
xarchiver
xchat
k3b burner
vlc media player
kodi
vmware player
openvpn
amule
audacity
inkscape
gimp
catfish
screenshot
udftools
boinc
conky
lm-sensors
calibre
okular
and a few others

I currently use transmission, but I have not taken the time yet to check out any other bt clients on Linux -- yet.

I do not really care for any of the current audio players / managers (on Windows or Linux).  I continue to use MusicMatch Jukebox 10 on an XP virtual machine in my linux system using FTP.  The main reason being that the root of my music collection is genre, not artist or title.  MMJB simply handles that better. (Way, way, WAY down on my to do list is to try to write a plug-in for Kodi / XBMC to give it the features I won't give up.)

I do not use a desktop email client, desktop contacts software, desktop calendar manager (other than looking at the dates), chat software (other than irc) or office software at all.

As I write this, I am using Xubuntu 14.10.  I am going to back down to 14.04, because I am adding a second radeon gpu and want to run the latest proprietary drivers from AMD.

I know that I can install Xubuntu 14.04 and update it via PPA.  But, if it would work, I prefer to use the minimal xubuntu-core, for now hopefully more obvious reasons.

---

### Post by Frogs Hair on 2015-05-14
I've also used the PPA to upgrade 4.10 installations on Ubuntu by installing xfce4 and adding the ppa.

---

### Post by lambdafox on 2015-05-14
> **Frogs Hair said:**
> I've also used the PPA to upgrade 4.10 installations on Ubuntu by installing xfce4 and adding the ppa.

xfce4 includes the entire desktop.  it is the same as using the xubuntu install disk.

My question is whether you can install the xubuntu-core on ubuntu 14.04, and get the xfce 4.12 components that come with it.

---

### Post by lambdafox on 2015-05-14
The answer is:

Ubuntu 14.04 minimal iso does not support the "xubuntu minimal" install option.

At the initial prompt, it does not understand the xubuntu-core install command, even after adding software-properties-common

I installed:

xorg
hwd

no recommends on these:
xfwm4
xfdesktop4 xfwm4-themes xfce4-panel
xfce4-session dbus-x11
xfce4-settings x11-utils
exo-utils
thunar

I was able to update all of these by:

    sudo add-apt-repository ppa:ubuntu-dev/xfce-4.12
     sudo add-apt-repository ppa:ubuntu-dev/extras
     sudo apt-get update
     sudo apt-get dist-upgrade

I did all of this on a vm.  I think I will use uck to create a custom installer, now that I know the ppa can update the components.

---

### Post by Frogs Hair on 2015-05-14
> it is the same as using the xubuntu install disk. Xfce4 excludes many applications such as abiword , media players and many other Xubuntu modifications and software.Xfce4 is just the bare-bones desktop. Glad you worked it out though.

---

### Post by Elfy on 2015-05-14
xubuntu-core isn't available pre 14.10 for installation from the mini.iso

From vivid there are community iso's available.

---

### Post by Bucky Ball on 2015-05-16
> **Elfy said:**
> xubuntu-core isn't available pre 14.10 for installation from the mini.iso

From vivid there are community iso's available.

I just found that out the hard way. Bought a new computer and I only go LTS and minimal installs with xfce4 generally, but this computer doesn't have an ethernet port, mini didn't recognise my wireless (nor did 14.04 xubuntu core) so 15.04 it was, and ... didn't recognise my wireless card. So, back to 14.04 desktop and killed a bunch of apps I don't use. 

Anyway, more about that on another thread later ...

To a previous poster, installing xfce4 is definitely NOT equivalent to installing Xubuntu! Installing xubuntu-desktop is. I think I outlined this earlier ...

---

