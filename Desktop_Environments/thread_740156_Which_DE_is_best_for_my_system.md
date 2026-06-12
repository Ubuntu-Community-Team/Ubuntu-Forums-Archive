---
title: "Which DE is best for my system?"
date: 2008-03-30
forum: Desktop Environments
---

### Post by Masteroc on 2008-03-30
Here are some of the main stats of my system: 1.7ghz celeron, 512mb memory, 60gb hard drive, 64mb video card. I am trying to find a good DE that i can use for my school work/ internet browsing. I dont think that this computer can handle the full blown Gnome or KDE install of (K)Ubuntu, so i was thinking more along the lines of Xgce4 or Fluxbox or Openbox. I think that it has enough memory for Xfce4, but i want it to run responsively and i dont want it to feel like im running xp on it again... As a secondary part of this post (if i decide to go with xfce4) can someone please tell me what i would need to install to get Xfce4 to look like the Xubuntu desktop. I dont want to install Xubuntu because i hate all the other stuff that they put in there....games and stuff that i dont need. I want to be able to choose everything that goes into my system, but i still want to have a taskbar and menu type thing like xubuntu. Any help would be greatly appreciated!!

---

### Post by NightwishFan on 2008-03-30
You could run Ubuntu or Kubuntu on those specs quite comfortably. I have 895mb ram and my computer can run ever program installed on it at once. Xubuntu looks great and runs fast although they should make it faster. I would say install Xubuntu because it is simple, modern, fast, and great looking. It would run on half your ram. I say Xubuntu when I mean XFCE4.

---

### Post by urukrama on 2008-03-30
It all depends on what you like. Openbox is great, but needs a little more work to set it all up than Xfce does. (For help with Openbox, see the guide in my signature)

Xfce should run fine on that computer; I occasionally use it on lesser systems with no difficulties.

If you want to go for Xfce, install xfce4 (sudo aptitude install xfce4) rather than Xubuntu-desktop if you have already an ubuntu installation. If you want a fresh install, use the alternative install CD and go for a command line install with xfce4 (see [here]("http://psychocats.net/ubuntu/minimal") for help, and then replace icewm with Xfce4 in the 'Getting a usable home desktop' section at the end of that page).

Installing [Xfce4]("http://packages.ubuntu.com/gutsy/xfce4") will give you a lighter and faster xfce than xubuntu-desktop. To get the xubuntu look, you could install the package [xubuntu-artwork]("http://packages.ubuntu.com/gutsy/xubuntu-artwork"), [xubuntu-artwork-usplash]("http://packages.ubuntu.com/gutsy/xubuntu-artwork-usplash") and [ xubuntu-default-settings]("http://packages.ubuntu.com/gutsy/xubuntu-default-settings").

If you have a current ubuntu installation, I suggest you install Openbox, Xfce and Fluxbox, try them out and see which one you like best, before you go for a fresh install with the window manager and/or Desktop environment of your choice.

---

### Post by Masteroc on 2008-03-30
I would probably go with the fresh install through the alternate install disc. I am hesitant to install and run Ubuntu on this machine however because i have it installed on another machine of higher specs and it still runs slight slow (although this is content for another thread) so i really would like to stick to anything below Ubuntu/Kubuntu. So if i do an apt-get install xfce4 and then the xubuntu artwork and default settings i will have a full desktop that looks like xubuntu without all the extra apps. What about configuration utilities like printing and networking, will those be installed with xfce4 as well?

Thanks

---

### Post by urukrama on 2008-03-30
> **Masteroc said:**
> So if i do an apt-get install xfce4 and then the xubuntu artwork and default settings i will have a full desktop that looks like xubuntu without all the extra apps. What about configuration utilities like printing and networking, will those be installed with xfce4 as well?

Here is what Xfce4 (which is really a metapackage, like xubuntu-desktop, but much smaller) will install:

> **gtk2-engines-xfce (>= 2.4.1) **
A GTK+-2.0 theme engine for Xfce 
**thunar (>= 0.8.0) **
File Manager for Xfce 
**xfce4-icon-theme (>= 4.4.1) **
Xfce Standard icon theme 
**xfce4-mcs-plugins (>= 4.4.1) **
Special modules for the xfce4-mcs-manager 
**xfce4-panel (>= 4.4.1) **
The Xfce4 desktop environment panel 
**xfce4-session (>= 4.4.1) **
Xfce4 Session Manager 
**xfce4-utils (>= 4.4.1) **
Various tools for Xfce 
**xfdesktop4 (>= 4.4.1) **
Provides desktop background and root menu 
**xfwm4 (>= 4.4.1) **
window manager of the Xfce project 
**xfwm4-themes (>= 4.4.1) **
Theme files for xfwm4

The following packages are recommended, but not necessary:

> **desktop-base **
common files for the Debian Desktop 
**orage** 
Calendar for Xfce Desktop Environment 
**xfce4-mixer **
Xfce4 Mixer frontend 
**xfce4-terminal **
Xfce terminal emulator 
**xfmedia** 
Xfce media player 
**xfprint4 **
Printer GUI for Xfce4

(Taken from the [Ubuntu packages site]("http://packages.ubuntu.com/gutsy/xfce4"); this is based on Ubuntu Gutsy)

If you want printing utilities, etc. you'll have to install those separately. To make things easier, you could install [gnome-system-tools]("http://packages.ubuntu.com/gutsy/gnome-system-tools") (which, if I remember correctly, doesn't require Gnome installed) for users and groups management, date and time, network configuration, bootloaders and runlevels. For printing there are several options; perhaps [xfprint]("http://packages.ubuntu.com/gutsy/xfprint4"), [system-config-printer]("http://packages.ubuntu.com/gutsy/system-config-printer") or [printtool]("http://packages.ubuntu.com/gutsy/printtool") is what you are looking for.

Just installing xfce4 will, in other words, give you only the desktop environment. Everything else you'll have to add yourself: terminals, internet browser, word processors, image viewers, etc.

---

### Post by Masteroc on 2008-03-30
Thanks for the info!! That is most likely what i'll do. It will take some time, but i think it will be worth it in the fact that my system will be faster.

---

### Post by aquinashub on 2008-04-02
I have two computers at the moment: One running straight up Ubuntu on a 1.8ghz with 2 Gigs of RAM - runs quite responsively (like, as fast as Windows XP after you've removed extra components and shut down needless services), and another - this is the one I think you'll like - a 733Mhz system with 256Mbs of RAM running Xubuntu! A standard install and STILL runs as fast as XP does (not to mention more stable and it actually does what I WANT it to do)!

I love Linux, it's so good to my computer.

I've since turned that old computer into a server running Debian Etch with Fluxbox: Hah! It runs faster than my 1.8! You could go that route and install the extra packages for XFCE4, like what urukrama posted above.. although yep, the printer'n'stuff will take a little configuring (but with all this help on the forums, a newbie can do it)

Good luck finding the perfect desktop!

---

