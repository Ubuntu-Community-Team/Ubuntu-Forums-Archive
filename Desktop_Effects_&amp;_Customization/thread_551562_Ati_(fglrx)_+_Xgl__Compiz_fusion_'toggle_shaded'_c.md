---
title: "Ati (fglrx) + Xgl : Compiz fusion 'toggle_shaded' crash"
date: 2007-09-15
forum: Desktop Effects &amp; Customization
---

### Post by OriginalAndTheBest on 2007-09-15
Hi guys,

As mentioned in the thread title, I'm running an Ati X800XL video card, fglrx driver with an XGL session for compiz fusion. Starting compiz and emerald at login with compiz --replace and emerald --replace.

My problem is kinda strange. I'm getting the following error mostly after i guess you could saw a lot of compiz activity, like spinning the desktop cube incessantly. However it also happens when I'm just using it normally:

> frank@frank-desktop:~$ compiz --replace
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
...
... (more of this exact same line)
...
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (group) - Warn: No compatible text plugin loaded.

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

Now i'm using the apparently less stable build of compiz fusion, but I don't know where to disable the screensaver plugin like another poster has suggested. Is there anything I could try to fix this? Another thing, I have the two lines

> 
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "on"


in the Device section of my xorg.conf file. I don't know what they do, but it was in the compiz fusion guide I read. The OpenGLOverlay was originally 'off' but I changed it to test if it was doing anything to compiz and nothing seems to have changed.

Any help at all is appreciated :)

Thankyou in advance!

---

### Post by OriginalAndTheBest on 2007-09-15
bump.

a little help please? :)

---

### Post by OriginalAndTheBest on 2007-09-16
Never mind, just changed to the amarath packages, and it seems stable now :)

---

