---
title: "Kicker Crashing Once or Twice A Day"
date: 2007-07-12
forum: Desktop Environments
---

### Post by LordKelvan on 2007-07-12
Hi:

I recently switched to KDE on my Ubuntu box just to test it out, and I must say I rather like it.  The look is gorgeous (especially love the icons) and the overall functionality is great.  There is only one problem: kicker seems to crash at least once a day.  Usually when this happens, I am trying to open movie files (one time it happened when I tried to open a music file by right-clicking the file and selecting "open with", but I rarely listen to music this way so that is why it is only once).

**Ideally I would like to find out the reason for the crashing and fix it**.  The next best thing would be if someone could tell me an easy way to restore my KDE system tray.  What I mean is that when my kicker crashes, I lose all (or most) of my icons in the system tray, but the actual programs are still running.  For example, I will have amarok minimized to the system tray, kicker crashes, and now the amarok icon is no longer in the system tray, but amarok is still running.  Right now, I am forced to use the terminal to kill all programs which were minimized to the system tray, then start each one up again, which is extremely annoying.  Anyone know of an easier way?

Cheers,
LK

---

### Post by Raineer on 2007-07-12
This is pretty much a known bug :(  It's the reason why I had to switch back to Gnome.  I'm hoping the bug will disappear in version 4.0 later this year.

It's not really know why it occurs, I typically see it when I have 10-15ish windows open (something I can surpass easily in Gnome).  I think it's just a multi-tasking bug, and pretty much every forum and comment I read about it said "just deal with it, that's what KDE does"

---

### Post by LordKelvan on 2007-07-13
No offense intended, but I find it hard to accept that "that's what KDE does".  Surely I can look somewhere on my system (e.g. error log file) to ascertain the error that comes up when Kicker crashes?  Can someone tell me where I might look?

I understand that no software is perfect, and they will crash.  But at least if I know the error message, I might be able to do something.  Maybe its codec related, or a particular multimedia backend is causing this problem.  It cannot be the case that all Kicker crashes are due to the same reason - surely some must be resolvable by uninstalling some things or changing configurations?

---

### Post by dehmmy on 2007-07-27
Same thing happens to me. 
Practically everytime I leave my cpu, upon my return, kicker is gone. So  I manually go through the motions of running konsole (yes I like consoles) and run it manually "kicker &" (close konsole).

When kicker bombs out, it doesn't leave an error message. It just displays the default KDE error window explaining that there was an error but it could not get the details.

As for the screenshot, I'm sure there's one on google images. If not I'll try and grab one if I get really really bored.


I'm running (replace ubuntu w/ kubuntu)::

Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:         7.04
Codename:     feisty

obtained via the command:: # lsb_release -a



Xorg version::


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux warcrime 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present

via the command::  # Xorg -version

And KDE v3.5.7 ("stable")

peace,

dehmmy

---

