---
title: "Help!  Problems during/after using composite manager"
date: 2006-08-31
forum: Gaming &amp; Leisure
---

### Post by jdunn on 2006-08-31
I followed the composite manager "How To" written by PHG and used KDE's built in manager to try out transparency and dropshadows in KDE.  I used KDE's built-in composite manager.  Then, I played ut2004 and enemy-territory fullscreen at 1024x768 (my desktop res is 1280x1024).  Since then, I've had wierd X problems which have persisted even after I disabled composite mode.  Here are the problems:

* Sometimes I have no sound on ut2004 or enemy-territory
* Every time I exit enemy-territory, my desktop resolution comes up as 1024x768
* When I end a KDE session and return to the login manager, the login manager screen is 1024x768

How do I fix these problems?  They don't seem to be in xorg.conf.

---

### Post by jdunn on 2006-08-31
I followed the composite manager "How To" written by PHG and used KDE's built in manager to try out transparency and dropshadows.  Then, I played ut2004 and enemy-territory fullscreen at 1024x768 (my desktop res is 1280x1024).  Since then, I've had wierd X problems which have persisted even after I disabled composite mode.  Here are the problems:

* Sometimes I have no sound on ut2004 or enemy-territory
* Every time I exit enemy-territory, my desktop resolution comes up as 1024x768
* When I end a KDE session and return to the login manager, the login manager screen is 1024x768

How do I fix these problems?  They don't seem to be in xorg.conf.

---

### Post by slimdog360 on 2006-08-31
I could be wrong but I dont think there is much hope for your problems Im sorry. Maybe someone can fix them but I had similar problems when seing XGL/compiz myself and yes I was unabe to solve them. 
I put it down to the software being very new. I first noticed problems using frozen bubble. I do remember someone saying a quick was to turn off any effects for when launching a game so maybe there is some hope.

---

### Post by T.J. on 2006-09-03
The *technical* reason you are having a problem is the Composite extension to X11 is "relatively" new - on the order of two years (X11 v6.8.0 - Sept '04) this month, but is still considered unstable. 

No matter how you slice it, the truth is that support for the extension, and the extension itself, still need a lot of work.

*If you are unfamiliar with X, and want stability, my advice is don't use the Composite extension at all.*  


As for sound and resolution problems, here are a couple of suggestions, but as with all things changing the way X works, *use them at your own risk...*

1. Go into the "Display" subsection on your screen device and remove all of the other resolution blocks, thus preventing X from changing resolution modes, for example:

Section "Screen"
    Identifier  "Screen 1"
    Device      "NVIDIA GeForce"
    Monitor     "My Monitor"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1280x1024"
        ViewPort    0 0
    EndSubsection
EndSection

2. Sound.. Many desktop environments like KDE and GNOME launch a sound management daemon for event sounds (and other such nonsense :D ).  

The biggest problem you will discover on a Linux desktop is that some programs are not written to share the sound device, and it's highly likely that you don't have sound mixing support embedded in your hardware. 

You can fix this by altering the default settings for ALSA (Linux sound system) to enable the software mixer. You might find it easier and quicker to just disable the event sounds, if you dont know how to edit your alsa.conf manually.

*You (or anyone else reading this) are always welcome to post on the board to me, and I'll try to walk you through the process of tweaking your system, but I can't make any real promises.*

What I would do, is petition Xorg and your window manager project, to tell them you want support for Composite, so that development will be accelerated and tested with software that is used on the desktop.

The rest of what I'm going to say is mostly exposition to explain Composite, so you can stop here if you want. :cool: 

Cheers!
T.J.


Getting your video card to support Composite can be problematic.  Nvidia themselves only in the last couple weeks released a driver for X11 v7.1 with Composite specifically supported officially (although it has been in the proprietary driver a while).


My personal opinion is that the real reason that Composite hasn't stablized by now is that most of the major window manager projects haven't been adopting even "optional" support for developers.

Why should driver makers bother with support or Xorg place a priority on its development when 9/10 of the software doesn't even have support for *testing (much less using)* the Composite extension? 

To date, the only two I know of that have even partial support that can be easily tested are KDE and XFCE. GNOME's Metacity manager is being worked on. The last I investigated the  matter, it was supposedly highly unstable. I do not know for certain what its current state might be.

My advice to anyone -  if you decide to try to "bandaid" your manager with xcompmgr - know your hardware.  The xcompmgr program is a "reference implimentation", that isn't really intended for actual  day to day use.  

It has several issues, depending on hardware and driver.  On some video cards, it is known to crash when you alter the root window of X. An example would be loading an image into the "root window" for a wallpaper. (No, KDE and GNOME don't use the "root window".)

Other window managers, I recommend you use feh if you want a wallpaper.  The commonly used xli program is known to make xcompmgr crash, especially on Nvidia. 

Just an additional thought for the future (and apologies if some consider this comment off topic):

I think what would be of the greatest service to everyone involved is if and when X11 drivers are rebuilt around the OpenGL standard.   I believe things are headed in that general direction, but until they do, end users of X11 will continue to have issues like this.  Card makers know OpenGL well, and X supports it using Mesa.

It would hopefully improve driver quality, provide other 2D/3D benefits, and accelerate developments like Composite. 

Just another thing you can ask Xorg for when petitioning.

---

### Post by T.J. on 2006-09-03
Sorry if I double posted.  I had trouble with the connection.  The board is very slow today.

---

