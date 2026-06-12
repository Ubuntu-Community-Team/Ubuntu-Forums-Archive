---
title: "Desktop Effects, Widgets Broken with Update"
date: 2009-02-23
forum: Desktop Environments
---

### Post by Anlace on 2009-02-23
Greetings,

I was excited yesterday when I saw that KDE was (apparently) updating to 4.2.  After the update, which seemed to go off without a hitch, I first experienced a loss of window decorations (title bar, borders, etc) which was corrected by re-installing kde-window-manager.

However, I was left with hideous desktop effects, strange un-asked-for colors, and widgets that disappear after logout or that snap to random areas of the desktop.

One of the hideous desktop effects are drop shadows that are now stark white and opaque.

Un-asked-for colors are windows which now have about a 2 pixel blue border around them, as do buttons, scroll bars, etc and the Oxygen theme now produces a garish blue task bar.

Widgets will not position where I place them, instead "snapping" to apparently random locations on my desktop.  They also completely disappear after restarting the computer.

I can live with all the desktop effects turned off, a style other than Oxygen, and no widgets but these are the some of the things that give me a lot of satisfaction using KDE.

I have tried uninstalling and reinstalling everything I could think of - the Nvidia driver, anything having to do with Plasma and widgets.  Nothing has helped so far.  I also searched through bug reports and haven't seen anything there either.

I think that the problem with desktop effects and color is due to a configuration file(s) that needs to be purged but I don't know which ones or how to go about doing that.  I've tried all of the settings I could find and that hasn't made any difference either.  For example, drop shadow settings are all set to black, 75% alpha, etc and I still have opaque white drop shadows.

Any help with this would be very much appreciated.

Thanks,
Gail

---

### Post by SuperSonic4 on 2009-02-23
Have you rebooted and/or restarted X. Mine were dodgy until I rebooted.

The widgets in kde4.1 are incompatible with kde4.2 but you could use adept to bring some back

---

### Post by Anlace on 2009-02-23
Yes, I have rebooted many times.

All of KDE's widgets and plasma was uninstalled and reinstalled, so they are all KDE 4.2 and they still don't behave on the desktop.

---

### Post by Monsieur Gonzalez on 2009-02-23
were you upgrading from 4.1? Which graphics card? Plasma config files might need to be removed and recreated for it to behave. I know I had to do it because of incompatible widgets and whatnot. Files are located in the kde config folder (.kde/share/config) and are called plasma-appletsrc and plasmarc . 

You should do it while KDE is not running, so, if you don't feel confident with the command line, maybe try to do it with another window manager.

Backup things just in case.

---

### Post by Anlace on 2009-02-23
> **Monsieur Gonzalez said:**
> were you upgrading from 4.1?
Yes, I use Adept Updater to let me know when updates are available and Synaptic to actually do the updating.  When I saw all of the KDE stuff updating I figured that it was 4.2 though there was nothing to specifically indicate that it was.  My base system is Kubuntu 8.10.

> Which graphics card?
Nvidia GeForce 9800GTX

> Plasma config files might need to be removed and recreated for it to behave. I know I had to do it because of incompatible widgets and whatnot. Files are located in the kde config folder (.kde/share/config) and are called plasma-appletsrc and plasmarc.
Perfect, thank you.  This is the info I was looking for.  I think that a custom setting that I created was retained somehow and is hosing the works.  I also assumed that KDE 4.1 widgets would be removed if they were no longer compatible.

So when I remove the config files and restart KDE will they be automatically recreated?

> You should do it while KDE is not running, so, if you don't feel confident with the command line, maybe try to do it with another window manager.

Backup things just in case.c
Command line is no problem at all, and I back things up regularly anyway.  Good advice though, always!

Thanks again, I'll let you know if that does it.

---

### Post by mansonthomas on 2009-02-23
Hi,


I've the same issue : Kde has been udpated, then I was unable to login (back to login screen just after the hardrive icon begins to show up)

The first time not completely I had to run a aptitude -f upgrade (As far as I can Remember)

and then I'm able to login, but no window border, no close minimize button in the right upper hand corner.
The bottom taskbar takes only 2/3 of the screen. I'm not able to do alt+tab etc...

How did you reinstall kde-window-manager?

apt-get remove kde-window-manager
apt-get install kde-window-manager 

??

Thomas

---

### Post by mansonthomas on 2009-02-23
removing plasma configuration files didn't solve anything on my computer (indeed, it brings back some widgets I've removed as they shows errors).

---

### Post by Anlace on 2009-02-23
> **mansonthomas said:**
> Hi,
How did you reinstall kde-window-manager?

apt-get remove kde-window-manager
apt-get install kde-window-manager 

??

Thomas

Yes, that is exactly how I did it.

There were a number of updates this morning and included in that list was kde-window-manager.  Try running sudo apt-get dist-upgrade first and see if that fixes things.

---

### Post by Anlace on 2009-02-23
> **mansonthomas said:**
> removing plasma configuration files didn't solve anything on my computer (indeed, it brings back some widgets I've removed as they shows errors).
Make sure that you are not logging back into a saved or previous session.  The default is Restore Previous Session and I think that will try and load all of the widgets etc that were active on your desktop.

Go to System Settings > Advanced (tab) > Session Manager and change On Login to Start with an Empty Session.

Delete those config files and try again, maybe that will help.  It solved my widget problem.

---

### Post by Anlace on 2009-02-23
I still have interesting problems with desktop effects.  I narrowed it down to the drop shadow, everything else seems to be fine.  Drop shadow on my desktop is a blue glow effect now whereas it was an opaque white.  I'm not sure that's really progress . . . .

I noticed that the drop shadow configuration does not respond to any changes I try to make to it.  For example I changed the color to red, drop shadow stays a blue glow.

Also the Oxygen theme is still a truly awful shade of blue.

Would it help to post screen shots?

I read about drop shadow issues in the beta stage of KDE 4, it was with ATI video cards and Ubuntu/Gnome.  Could this be a similar issue?

---

### Post by Anlace on 2009-02-23
Ok, making a bit more progress here and I'm hoping this info will help others.

Playing more with drop shadows, if the opacity is brought all the way up to 100% the shadow looks like it should and changes "stick."  However, when the window is moved the shadow goes brilliant white and much stronger than normal, looking much like it did before opacity was changed to 100%.  It looks very weird and I've looked at some different settings to see what will change this move effect.

It's the Translucency setting, apparently translucency is brightening effects instead of fading them.  Niggling around with that setting produces acceptable shadow effects.

---

### Post by mansonthomas on 2009-02-24
well, it tells me kde-window-manager not installed.... :oP

Strange... 

I've installed it... window decoration are back ;)

Ouch... it was hardcore update ;o)


I hope that there will be no more surprises !

---

