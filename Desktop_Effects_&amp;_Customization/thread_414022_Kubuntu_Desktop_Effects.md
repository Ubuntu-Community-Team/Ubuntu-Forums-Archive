---
title: "Kubuntu Desktop Effects"
date: 2007-04-19
forum: Desktop Effects &amp; Customization
---

### Post by hedgefighter on 2007-04-19
Ok, maybe this is a silly question. I was playing with the Ubuntu Feisty and found the Desktop Effects and Restricted Drivers programs. Now I'm trying out Kubuntu Feisty and I can't seem to find them. Anyone know what the issue is?

---

### Post by Chowderpilot on 2007-04-19
Hedge,

I found it under System Settings>Window Behavior

There are several tabs you can configure to your liking there, ie; Translucency.

CP

---

### Post by hedgefighter on 2007-04-19
Thanks, but that's actually not what I was looking for. Apparently the new restricted drivers and desktop effects programs are for gnome. I guess I could install them but I don't really need to. I was just wondering if I was not seeing it somewhere or if it in fact wasn't included. 

Those settings you're talking about are just KDE settings. In fact, I believe turning on the window translucency will conflict with Compiz/Beryl.

---

### Post by AusIV4 on 2007-04-19
I've been wondering the same thing. So far I've only run the Live CD, and I'm waiting for one of my computers to finish dist-upgrading. If I can get dist-upgrade to work on all my computers I think it's pretty much moot, because I already have bery configured.

---

### Post by Drek on 2007-04-22
I am SO glad I found this thread, I've been driving myself crazy poking through menus looking for this "Desktop Effects" thing.  As long as I know it's not there, I can stop looking. :biggrin:

---

### Post by Morientes on 2007-04-23
Was just looking for the same thing!

Isn't it a little strange that the "desktop effects" are only present in Ubuntu?

---

### Post by gmccreight on 2007-04-26
I've figured out how to get the desktop-effects to work in Kubuntu Fiesty Fawn.

Go to KDE Start Menu->"Add/Remove Programs", then once Adept Installer loads, you can search for "desktop effects".  A package called desktop-effects will be found.  Its description says that it's a "preferences applet for configuring desktop effects".  Install it.

Once it's installed, go to KDE Start Menu->System->Konsole.  Type in the command:

desktop-effects

then press enter.  It will bring up a wizard which allows you to choose which effects you'd like to enable.

Cheers - Gordon

---

### Post by gmccreight on 2007-04-26
I should add, though, that I can't seem to figure out how to turn them off.

---

### Post by shadowfx78 on 2007-04-26
drats wont work on my laptop i guess i have a crappy video card

---

### Post by lunamystry on 2007-08-10
> **gmccreight said:**
> I've figured out how to get the desktop-effects to work in Kubuntu Fiesty Fawn.

Go to KDE Start Menu->"Add/Remove Programs", then once Adept Installer loads, you can search for "desktop effects".  A package called desktop-effects will be found.  Its description says that it's a "preferences applet for configuring desktop effects".  Install it.

Once it's installed, go to KDE Start Menu->System->Konsole.  Type in the command:

desktop-effects

then press enter.  It will bring up a wizard which allows you to choose which effects you'd like to enable.

Cheers - Gordon

I have been playing around with my Kubuntu desktop gusty gibbon and I am trying to enable compiz fusion, do I need to download desktop effects to do it?

Gusty Gibbon does not have desktop-effects it appears. My search for desktop effects does not yield any results.

---

### Post by wireddad on 2007-08-18
Is this "desktop-effect" the same as in Ubuntu?  I want to load Kubuntu but hate to lose the Ubuntu effect to wow others.

---

### Post by Etheris on 2008-02-27
I am having problems setting up Compiz-fusion and emerald on my kubuntu 7.10 box (amd64, nvidia gforce).  Compiz is installed correctly (I think) and the graphical functions work fine, but I cannot get my window title bars to be displayed correctly.  When I start compiz ("compiz --replace") the screen restarts and I loose my title bars.  I have also noted that before I start compiz the displayed title bar is being taken from the KDE windows decorator instead of emerald and, even though I can open the emerald manager, emerald will not effect the menu display.  My guess is that when I activate compiz it is looking for an emerald theme, and since it is not active it displayes no menu.  Also, when I attempt "emerald --replace" it produces errors and stalls in the terminal.

I have tried changing my nvidia options, which appears to be working fine and I have also tried changing visual and rendering options in xorg......along with just about everything else I have been able to find online.  Please help if you can.

---

