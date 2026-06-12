---
title: "New Install - Questions"
date: 2009-03-18
forum: General Help
---

### Post by jtp755 on 2009-03-18
I have just finished a new installation of Kubuntu 8.10. Im coming over from Gentoo Linux. Have been using Gentoo for about 7 years now. Any way...i love how easy everything in Ubuntu is and i want to keep it that way. 

My Wants/Desires:

1. I want Fluxbox and not KDE or Gnome.
2. I want the wireless, external drives, etc to work like they do in a default install. Aka..pop up when inserted, easily view available networks, lock screen but using corner of the screen.
3. I want VMware Workstation or Player (very much required!)
4. Gotta have Firefox and Thunderbird!

My Questions:

Should i just uninstall all of the stuff from a default install that i will never use such as Kmail or use the ubuntu-minimal install and just add things?

Now a note: I do like the way KDE 4 looks and acts so i would like to be able to use both Fluxbox and KDE4 so i can play with KDE, but i dont want the bloat that i wont use in KDE4.

So what is the best way to accomplish the above? Thanks for your help in advance!


Jonathan

---

### Post by LowSky on 2009-03-18
I use Ubuntu and it has Firefox installed by default so bear with me 

there is a package manager called Adept, you can use that to install, Firefox, thunderbird, and VM... something called Add/Remove cna also do all this stuff... I think Fluxbox is availbe as well

Drivers, should be handled by something called Restricted drivers under the Menu

try these links for more help

[http://kubuntuforums.net/forums/index.php](http://kubuntuforums.net/forums/index.php)

[http://kubnewb.blogspot.com/2006/06/how-to-install-firefox-for-kubuntu.html](http://kubnewb.blogspot.com/2006/06/how-to-install-firefox-for-kubuntu.html)

---

### Post by Therion on 2009-03-18
> **jtp755 said:**
> Should i just uninstall all of the stuff from a default install that i will never use such as Kmail or use the ubuntu-minimal install and just add things?
I would go with a minimal install and work my way up.  That's just how I prefer to do things.  No residual "stuff" lingering about this way, everything is neat and tidy.

> **jtp755 said:**
> Now a note: I do like the way KDE 4 looks and acts so i would like to be able to use both Fluxbox and KDE4 so i can play with KDE, but i dont want the bloat that i wont use in KDE4.

So what is the best way to accomplish the above? Thanks for your help in advance!
Well if you want the KDE experience, even if it's only to play around with it, you'll have to install everything that goes along with it when you install the desktop environment.  I don't see any way around this; you take the bad with the good. Unless you want to reinstall (sans KDE of course) or are willing to experiment with KDE via the LiveCD.

---

### Post by jtp755 on 2009-03-18
Thanks for the response by both of you. At this point i think i would rather just get Fluxbox up and running and then play with KDE through livecd. How would i find out what packages i need to install to get the usb/wireless/lock screen working in fluxbox? Is that even possible?

I found: [http://disambiguation.wordpress.com/2008/08/17/a-minimal-ubuntu-install-the-basics/](http://disambiguation.wordpress.com/2008/08/17/a-minimal-ubuntu-install-the-basics/) and [http://wiki.dennyhalim.com/ubuntu-minimal-desktop#toc4](http://wiki.dennyhalim.com/ubuntu-minimal-desktop#toc4) for minimal installs and they look to be pretty solid "guides" for a minimal install.

Any thoughts?

---

### Post by jtp755 on 2009-03-18
I have finished the minimal install and installed xorg, gdm, and synaptics.

The menu in fluxbox has a TON of stuff in it and i just wanted to make sure that is normal. Has applications, games, etc. Seems to be mostly xorg related/installed, or fluxbox though.

Installing Firefox and Thunderbird now.

---

### Post by RedSquirrel on 2009-03-18
> **jtp755 said:**
> The menu in fluxbox has a TON of stuff in it and i just wanted to make sure that is normal. Has applications, games, etc. Seems to be mostly xorg related/installed, or fluxbox though.

Yeah, that should be normal. On Debian and Ubuntu, application menus are built from something called "The Debian Menu". The package for this is called... wait for it... **menu**. :P

It is pulled in automatically when you install fluxbox.

Naturally, you can redo the Fluxbox menu to suit yourself. Here's a [tutorial]("http://ubuntuforums.org/showthread.php?t=371144") if you want more info about that from an Ubuntu point of view.

---

### Post by jtp755 on 2009-03-18
Awesome!

Thanks..now im off to install VMWare and play..

---

