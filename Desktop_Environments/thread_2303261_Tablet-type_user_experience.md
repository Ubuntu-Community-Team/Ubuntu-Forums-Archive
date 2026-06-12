---
title: "Tablet-type user experience?"
date: 2015-11-17
forum: Desktop Environments
---

### Post by steve234 on 2015-11-17
Afternoon all,

I have another post running on Openbox - which is being slow :( ...

The reason I looked into OB is that I want a minimal setup to use as daily computer (Atom-baset netbook - 1GB ram) - for browsing, email, youtube etc. I have a Mac for the more heavyweight stuff (photo/video edits etc).

Is there any way I can get a more tablet like experience - google searches just lead me to the Ubuntu tablet version. My netbook not having a touchdcreen doesn't aid the cause.

What I mean by tablet-like is:

(1) fast boot / wake / thaw whatever;

(2) Direct access to browser / emails / arduino / whatever quickly (my current thinking is use a launcher - Kupfer);

I thought OB with some keybindings would do the trick? Any other people got a lite/fast setup going on for daily use they'd like to share?

S

---

### Post by Dreamer Fithp Apprentice on 2015-11-17
ASFAIK, plain Openbox is your best bet for a very light gui environment using a 'buntu that is pretty traditional. There are some lighter window managers in the repo but they are all a little weird.

Try seeing what services are being started at startup and disable any you don't need. Try purging apt-xapian-index and manually rm'ing it's cache in  /var/cache.

Is part of your objective avoiding using your pointing device when you can? If so, yeah key-bindings are one way to go. Another is to have a single, easy to remember keybinding for the menu, and use letter keys, arrow keys, and the enter key to navigate the menu entries. The openbox menu is totally configurable. I start mine with the Debian menu as a submenu so anything I haven't added manually is often available through it automatically. Always back up your menu when editing it. It is easy to break it with a typo. There is also an openbox gui menu editor, but I haven't used it.

---

### Post by SurfaceUnits on 2015-11-21
[HR][/HR][IMG]http://distrowatch.com/images/yvzhuwbpy/chromixium.png[/IMG]
[LIST]
[*]**OS Type:** [Linux]("http://distrowatch.com/search.php?ostype=Linux")
[*]**Based on:** [Debian]("http://distrowatch.com/search.php?basedon=Debian"), [Ubuntu (LTS)]("http://distrowatch.com/search.php?basedon=Ubuntu%20%28LTS%29")
[*]**Origin:** [United Kingdom]("http://distrowatch.com/search.php?origin=United%20Kingdom")
[*]**Architecture:** [i386]("http://distrowatch.com/search.php?architecture=i386")
[*]**Desktop:** [Openbox]("http://distrowatch.com/search.php?desktop=Openbox")
[*]**Category:** [Desktop]("http://distrowatch.com/search.php?category=Desktop"), [Live Medium]("http://distrowatch.com/search.php?category=Live+Medium")
[*]**Status:** [COLOR=green]Active[/COLOR]
[*]**Popularity:** [31 (370 hits per day)]("http://distrowatch.com/dwres.php?resource=popularity")
[/LIST]
 Chromixium is an Ubuntu-based Linux distribution that attempts to  recreate the look & feel and functionality of Google's Chrome OS on a  conventional desktop. It combines the Openbox window manager with the  Compton desktop compositor, Plank dock and LXDE's LXPanel to provide the  desktop and menus. The Chromium web browser, equipped with the  PepperFlash plugin, is the main online application, although the  complete array of Ubuntu software can be easily added for  offline/desktop use. Ubuntu updates are installed automatically,  providing long-term security support.

---

### Post by SurfaceUnits on 2015-11-21
[HR][/HR][IMG]http://distrowatch.com/images/yvzhuwbpy/androidx86.png[/IMG]
[LIST]
[*]**OS Type:** [Linux]("http://distrowatch.com/search.php?ostype=Linux")
[*]**Based on:** [Android]("http://distrowatch.com/search.php?basedon=Android")
[*]**Origin:** [USA]("http://distrowatch.com/search.php?origin=USA")
[*]**Architecture:** [x86]("http://distrowatch.com/search.php?architecture=x86")
[*]**Desktop:** [Android]("http://distrowatch.com/search.php?desktop=Android")
[*]**Category:** [Desktop]("http://distrowatch.com/search.php?category=Desktop"), [Live Medium]("http://distrowatch.com/search.php?category=Live+Medium")
[*]**Status:** [COLOR=green]Active[/COLOR]
[*]**Popularity:** [12 (644 hits per day)]("http://distrowatch.com/dwres.php?resource=popularity")
[/LIST]

[LIST]
[*]Android-x86 is an unofficial initiative to port Google's Android mobile  operating system to run on devices powered by Intel and AMD x86  processors, rather than RISC-based ARM chips. The project began as a  series of patches to the Android source code to enable Android to run on  various netbooks and ultra-mobile PCs, particularly the ASUS Eee PC.
[/LIST]

---

### Post by SurfaceUnits on 2015-11-21
Here are some Puppy based distros for lighetwight Linux


**2. [Simplicity Linux]("http://distrowatch.com/simplicity") (19)**
Simplicity  Linux is a Puppy Linux derivative with LXDE as the default desktop  environment. It comes in four editions: Obsidian, Netbook, Desktop and  Media. The Netbook edition features cloud-based software, the Desktop  flavour offers a collection of general-purpose software, and the Media  variant is designed to provide "lounge" PC users with easy access to  their media.

**3. [Legacy OS]("http://distrowatch.com/legacy") (139)**
Legacy  OS (formerly TEENpup Linux) is a distribution based on Puppy Linux.  Although the original concept was to create a flavour of Puppy Linux  with more applications and a more appealing desktop aimed at teenage  users, Legacy OS has now grown to become a general purpose distribution.  It comes with a large number of applications, browser plugins and media  codecs as standard software. Despite these enhancements Legacy OS is  still perfectly suitable for installation on older and low-resource  computers, as well as modern hardware.

**4. [Toutou Linux]("http://distrowatch.com/toutou") (151)**
Toutou  Linux is an open-source Linux operating system based on the tiny, yet  powerful and popular Puppy Linux distribution, specially designed to be  compatible with old hardware. The system uses the lightweight Openbox as  its default window manager and LXPanel as its main taskbar. It features  various customisation options. Toutou Linux uses OCI, a custom-built  application that automates the installation, a first-boot assistant for  configuring several aspects of the desktop, and Opera as the default web  browser. Toutou Linux is distributed as a single live CD image  supporting the 32-bit architecture only. Its default language is French,  but other languages can be added.

---

### Post by Dreamer Fithp Apprentice on 2015-11-28
I may be wrong, but if I understand OP correctly he is probably already on track to a pretty light solution. Plain OB, no "desktop" per se, just a root window with no picture, no automatically launched panel or dock, maybe a conky clock. Conky is pretty handy in an environment like this because it can be set up to provide a "tunnel" to the root window so that the OB menus are always click-accessible with your pointing device.  But if you are trying to minmise the need for using your pointing device (being a confirmed trackball man, I hate to say "mouse") and want to bring the menu up with a kb shortcut, OB can do that, and then you don't really even need the conky. The OB menu is pretty good, and being able to incorporate the Debian menu as a submenu is a nice feature, but if you really want super light, you might like to look at 9-menu and see how it compares in resource usage.  If you'll  be running OB anyway, pro'ly the OB menu doesn't cost you anything resource-wise, but it is a question I haven't looked into. But if you like 9-menu and you won't be running too many apps at once and don't need too much fancy stuff from the WM in consequence you might want to look at TinyWM or 9WM instead of OB.  Those are so light you might need to put in an anchor line to make sure the comp doesn't float away.

---

### Post by steve234 on 2015-11-29
Thanks @Dreamer that's exactly what I'm after - I'm doing quite well with OB and some keybindings, tint2 panel and conky / feh for wallpaper. 

I try to use suspend a lot to get the "instant on" I want. I find that pm-suspend-hybrid works, but triggers a disk check on boot if the batt has run out.

I'll try to get better with the keys and terminal a that's where the speed really is. In terms of useability though I'm having real issues, getting things like videos (HTML 5 and flash) working are a massive headache - I have a thread on this but it has died a death. 

Sadly, i think I can fix the speed, but for ordinary use 'buntu sucks for browsers. The web experience is very poor for me, there are issues at every turn and no browser does all the "normal" things a Mac / Win user would expect them to.

---

