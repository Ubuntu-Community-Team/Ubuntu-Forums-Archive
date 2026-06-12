---
title: "Fusion: Not working - XGL/fglrx"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by Decline- on 2007-09-20
Hi,

I've had CF running for some time on my laptop with an ATI card and fglrx and XGL session. Today I figured I wanted some new effects, so I installed some new CF-packages... should never have done that, as it broke CF. And while trying to fix it, I broke almost everything :P Well, I have restored a lot to the correct settings, but some parts are still missing, and I need some help now!

I can't get fglrx to work with direct rendering:

$ glxinfo | grep direct
Xlib: extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

Composite IS disabled in xorg.conf, fglrx.ko is gone, depmod -a has been run and so on. I am running XGL, with this output:

$ fglrxinfodisplay: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6334 (8.34.8)

Should be correct? Only no direct rendering...

Xorg.0.log shows this:
[http://norskwebforum.no/pastebin/9563](http://norskwebforum.no/pastebin/9563)

(dont care about the colourcodes...)

A lot of successful messages, like this one: fglrx(0): DRI initialization successfull!

I have also follow some guides, among them the help provided to me by adamk the first time I tried running CF on this pc.. tho this time it wont work: [http://forum.compiz-fusion.org/showt...?t=3504&page=2](http://forum.compiz-fusion.org/showt...?t=3504&page=2)

And this is my xorg.conf :
[http://norskwebforum.no/pastebin/9564](http://norskwebforum.no/pastebin/9564)

And when trying to launch compiz from terminal::

~$ compiz --replace gconf
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :1.0

If I try to run fusion-icon I get this:

$ fusion-icon
* Detected Session: gnome
* Searching for installed applications...
* No GLX_EXT_texture_from_pixmap with direct rendering context
... nor with indirect rendering, this isn't going to work!
* Non-mesa driver on Xgl detected
... exporting: LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa
* Using the GTK Interface
* Metacity is already running
....
* Setting window manager to Compiz
... executing: compiz --replace --sm-disable --ignore-desktop-hints ccp
compiz (core) - Error: Couldn't load plugin 'ccp'

Then the windows borders disappear etc. (you know the deal).

HELP!! :O

---

