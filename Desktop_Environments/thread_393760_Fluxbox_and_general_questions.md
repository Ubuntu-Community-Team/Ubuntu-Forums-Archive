---
title: "Fluxbox and general questions"
date: 2007-03-26
forum: Desktop Environments
---

### Post by eggmanpete on 2007-03-26
First of all I'd like to say hi again, I haven't visited in a while, nor have I used Linux for a long time. But id like to "put the fun back into computing".
I've installed Ubuntu 6.10 AMD64 version and I am planning on installing fluxbox instead of gnome to get that old school feeling and that little performance boost.
I have a few questions on; if and how fluxbox deals with all the system configuration i.e: on gnome System > administration / preferences

I am asking because when I last used fluxbox, i had to revert to gnome to change my **IP, resolution, mouse settings, sessions, login window** etc..
I also had trouble mounting a **windows network share** in fluxbox so i had to use gnome's places > connect to server 

If anyone can tell me how I administrate the above using fluxbox (if its configuration files, program shortcuts) I'd be grateful.

Pete.

---

### Post by Xappe on 2007-03-26
if you don't mind using the gnome tools and settings (it's quite handy, though takes some system resources) you could, like me, run gnome-settings-daemon and gnome-volume-manager at fluxbox startup to have the gtk-settings etc. and the automounting of drives from that. 

Then you can use gnome tools for whatever settings you need to change: gnome-theme-manager, gnome-cups-manager etc.

---

### Post by eggmanpete on 2007-03-26
Thanks, can you point me to a list of all the gnome-*-manager if there is one?
I'm guessing all of this is also possible with configuration files? Can someone start me off with these?

Cheers, Pete.

---

### Post by Xappe on 2007-03-26
I made a quick short list of commands/programs and textfiles to get you started:
(just so you know where to start, and kind of where to look for settings)

programs/commands:
------------------------
fluxconf
fluxmenu
fluxkeys
gnome-mouse-properties
gnome-keyboard-properties
gnome-volume-manager
gnome-power-manager
gnome-cups-manager
gnome-network-preferences
time-admin
users-admin
ifconfig
man

-------------
textfiles:
-------------
FLUXBOX:
~/.fluxbox/menu
~/.fluxbox/init
~/.fluxbox/startup

NETWORK
/etc/hostname
/etc/hosts
/etc/host.conf
/etc/network/interfaces
/etc/iftab
/etc/resolv.conf

X
/etc/X11/xorg.conf

---

