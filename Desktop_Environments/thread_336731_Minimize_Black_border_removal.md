---
title: "Minimize Black border removal"
date: 2007-01-12
forum: Desktop Environments
---

### Post by andrewjb123 on 2007-01-12
Hi,

this is a bit of a strange request but here is my scenario:

Currently i have wine 0.9.29 installed to get Slingplayer to work (its a streaming media player software [www.slingbox.com](www.slingbox.com)) ... Ive managed to get everything working on wine and the stream plays fine, but whenever a gnome window is over the display (for example the home directory) and is minimized, the black borders which cascade to the toolbar are making the video choppy. Is there anyway i can i remove the black borders when minimizing. Ive searched the forum and the internet and have found fixes for things like compiz and beryl, but i use neither, im using the standard gnome interface which comes with ubuntu edgy eft.

Thanks in advance.

Andrew

---

### Post by HadroLepton on 2007-01-12
start gconf-editor and enable /apps/metacity/general/reduced_resources. that will disable the minimize animation and some other eye candies.

---

### Post by andrewjb123 on 2007-01-12
your a true gentleman, worked perfect,

one thing to note though, when i drag windows it displays a pretty ugly wire frame, is there anyway to have it still display the window contents, without the minimize border?

---

### Post by HadroLepton on 2007-01-12
the wireframe is part of the reduced resources. as far as i know there is no way to disable one without the other.

---

### Post by kelbizzle on 2007-03-14
> **HadroLepton said:**
> the wireframe is part of the reduced resources. as far as i know there is no way to disable one without the other.

[QUOTE=Aysiu]Yes, go to Applications > System Tools > Configuration Editor > Apps > Metacity > Reduced Resources and tick / check that box. That'll do two things: 1. It'll make it so that you don't see that god-awful zoom in/zoom out when you minimize and restore windows. 2. It'll draw a wire frame when you drag windows instead of showing the contents. If you hate the wire frame, go to System > Preferences > Assistive Technology Support and enable it.[/QUOTE]
 this should help anyone with this annoyance.

---

### Post by Mach1US on 2007-06-07
> **andrewjb123 said:**
> Hi,

this is a bit of a strange request but here is my scenario:

Currently i have wine 0.9.29 installed to get Slingplayer to work (its a streaming media player software [www.slingbox.com](www.slingbox.com)) ... Ive managed to get everything working on wine and the stream plays fine, but whenever a gnome window is over the display (for example the home directory) and is minimized, the black borders which cascade to the toolbar are making the video choppy. Is there anyway i can i remove the black borders when minimizing. Ive searched the forum and the internet and have found fixes for things like compiz and beryl, but i use neither, im using the standard gnome interface which comes with ubuntu edgy eft.

Thanks in advance.

Andrew
How did you get the audio driver to work ???
i tried this forum and still have audio problem.
[http://www.slingcommunity.com/article/17253/How-To-Run-SlingPlayer-on-Linux-OS/](http://www.slingcommunity.com/article/17253/How-To-Run-SlingPlayer-on-Linux-OS/)
I have got it up and running , just need to figure out the audio driver problem.
if any body knows  the fix for that issue please post to this thread , will be much appreciated . ):P

---

