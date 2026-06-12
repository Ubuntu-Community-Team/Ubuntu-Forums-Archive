---
title: "where gnome-screensaver's configuration file/information?"
date: 2006-06-01
forum: Desktop Environments
---

### Post by netztier on 2006-06-01
On my SPARC machines, X11 crashes every time an OpenGL app is launched.
(why this is so, is not the question here...)

Trying to diagnose the problem i configured gnome-screensaver to run GLMatrix (DUH!) and now whenever I run the configuration applet again, X11 crashes because it tries to run the OpenGL-App in the preview window.

Xscreensaver used to have a .xscreensaver file in the home directory.

Where would I find gnome-screensaver's equivalent? I've tried purging (i.e. "complete removal" in synaptic) gnome-screensaver and reinstalling it, but that didn't help.

kind regards

Marc

---

### Post by netztier on 2006-06-01
[QUOTE=netztier]
Xscreensaver used to have a .xscreensaver file in the home directory.

Where would I find gnome-screensaver's equivalent?[/QUOTE]

I finally found **gconf-editor** again. All the config options for gnome-screensaver are in there.

I had been suspecting it might be in "the thing that looks somewhat like regedit on Windows" but just had plain forgotten that this program still existed and lost quite a bit of time searching for something I had vaguely remembered as "gnome-system-editor" - which does not exist, of course.

regards

Marc

---

### Post by jedibug on 2008-01-13
Hi Marc, 

Thanks for posting the follow up, I was in the same situation, except with Fedora8 x64 and with the older NON-gl screensavers (and further to that on pc's without any gl driver installed, I've also found as you did, that *certain* GL ssavers will crash X on occassion, but as you said, that's another topic.).

Seems like some older/leftover screensavers cause problems in the newer distributions, mainly the ones from the extras packs. Without looking too deeply it looks like they get stuck in some sort of loop, and start to endlessly fill memory with something, and then once physical memory is full, begin to fill the pagefile (lol). Next is to find out how to remove them from the gnomescreensaver display list so they aren't selectable.

Thx.

---

