---
title: "emacs with nice anti aliased smooth fonts"
date: 2009-05-12
forum: Desktop Environments
---

### Post by fr4nko on 2009-05-12
Hi all,

I was very happy when I finally succeeded to configure emacs to use smooth, anti-aliased fonts on my laptop. The goal was to let emacs use the same smooth fonts of the GNOME environment. Actually to achieve that there was some tricky passages.

First you have to install emacs-snapshot package in order to have the latest CVS version of emacs 23. Otherwise with emacs 22 you don't have support for Xft fonts. Xft is the rendering method of the fonts used by GNOME and also by other Xft-aware applications.

In order to configure Xft for the other applications you should configure the file .Xresources in your home directory like that:

Xft.antialias: 1
Xft.dpi: 96
Xft.hinting: 1
Xft.hintstyle: hintfull
Xft.rgba: rgb
Xft.lcdfilter:  lcddefault

[I]Explication:
[/I]the Xft.hinting: 1 actives the hinting, the Xft.hintstyle active the hinting style. can be hintnone, hintslight, hintmedium, hintfull. I prefere hintfull or hintmedium but your mileage may vary. The lines
Xft.rgba: rgb
Xft.lcdfilter:  lcddefault
are very important for LCD screens to obtain a really fine rendering. Depending on your laptop you should try: rgb, vrgb, bgr, vbgr. I believe that almost all the laptop should use "rgb" because this is the standard ordering of the pixels.

To made the changes effective you should do:

> xrdb -merge .Xresources

in the terminal.

Then, the most important thing is that in order to have the right hinting you have to look at the directory:
/etc/fonts/conf.d. If a file like:

10-hinting-slight.conf

is present you should remove it (it is a symbolic link to the same file in ../conf.avail) and, optionally, replace it with the file in conf.avail that corresponds to the hinting that you prefere. For example

> cd /etc/fonts/conf.d
> sudo ln -s ../conf.avail/10-hinting-full.conf

to activate the full hinting.

Then to finish you can add

Emacs.fonts: Monospace-10

to your .Xresources file in order to configure Emacs to use Monospace fonts. As a welcome side effects all modifications you have done will be automatically applied to all Xft aware applications.

Here some screenshots with the final results for emacs and for IDLE (the python shell):
[IMG]http://img528.imageshack.us/img528/1314/emacsfragment.png[/IMG]

[IMG]http://img134.imageshack.us/img134/4475/screenshotpythonshellfr.png[/IMG]
Enjoy,
Francesco

---

### Post by mbd128 on 2009-05-18
Thanks for posting this info.

Just wanted to add that I prefer setting the Xft.rgba to none.

Xft.rgba: none

Gives a nice clean font on my 24' monitor.  YMMV...

---

