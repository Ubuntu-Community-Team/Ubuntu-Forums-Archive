---
title: "[SOLVED] Celestia installation &amp;amp; compilation problems"
date: 2008-01-29
forum: Education &amp; Science
---

### Post by John Harrington on 2008-01-29
I've tried to install Celestia several ways, none of which works properly, and am hoping somebody can give me a quick fix.

First, from the Gutsy repos., everything works except for 3-D models using cmod files.  cms models seem to work, and the repo. version doesn't have any 3ds models to test, although from what I've read they probably won't work if the cmod models don't work.  When I go to a moon or spacecraft represented by a cmod model, there seems to be something like a perfectly black hemisphere floating in space.  I read on another thread that this problem is a problem with the repo. version, and could be fixed by installing the Linux version of Celestia using the autopackage available here: [http://celestia.sourceforge.net/](http://celestia.sourceforge.net/)

The autopackage (which appears to be the same version number as the version in the Gutsy repository-1.4.1) installed smoothly.  However, when I tried to run it, I got the error, aborted (core dump).

Next, I tried installing the source package from the Celestia website.  This is version 1.5.0.  Configure seemed to run without a hitch until it stopped with the error message, "zlib not found."  I installed zlib1g and zlib1g-dev from the repositories, but got the same error message.  I tried the source package for version 1.4.1, but result was the same.  I read on another thread, in connection with configuring another package, that "zlib not found" may result from the fact that zlib and zlib1g have different names although they are the same thing.  If that's true, I don't know what to do about it since there's no zlib in the repositories and I can't figure out the syntax of the configure file.

I tried installing the windows version under wine, but that was a complete failure.

Each time I completely uninstalled the prior version including all directories before installing the next version.

I run 32-bit gutsy, standard kernel, AMD Sempron processor, Nvidia GEForce4 MX 4000 graphics card with proprietary driver, all desktop effects turned off.  I don't know whether this is relevant, but glxgears runs at about 600 fps in a small window, and about 25 fps fullscreen, although sometimes it jumps to 1000-2000 fps for short periods.  Penguin planet racer works fine.  Would appreciate any suggestions.  Thanks.

---

### Post by John Harrington on 2008-01-31
I found solution to this problem:

There is an Ubuntu package version of a recent cvs build of Celestia in this repository:

deb [http://ppa.launchpad.net/cteyssier/ubuntu](http://ppa.launchpad.net/cteyssier/ubuntu) gutsy main

It installs correctly and the cmod spaceship models display correctly for me.

---

