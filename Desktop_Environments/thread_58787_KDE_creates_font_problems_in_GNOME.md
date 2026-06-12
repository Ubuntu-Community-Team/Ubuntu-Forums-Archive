---
title: "KDE creates font problems in GNOME"
date: 2005-08-21
forum: Desktop Environments
---

### Post by dodongo on 2005-08-21
OK, first off, apologies if this isn't in the correct thread -- but I'm 100% sure something I did in KDE / Kubuntu caused this problem.

Essentially, the top panel in GNOME (as well as Gaim, for reasons I've not yet ascertained) have kept the way-too-big-for-GNOME KDE font settings.  In every conceiveable menu I can find to adjust font settings (System -> Preferences -> (Font, Theme, QtConfiguration), as well as in Kconfig itself, I can fiddle with the settings, and those settings *do* take effect in preview & open windows using that toolkit.  Nothing I've found, however, seems to be able to touch the uppermost panel (with Applications, Places, System, etc.).

I've tried googling for this, but I can't come up with the right way to describe it.

Any assistance is appreciated -- help me get my fonts back!!

Thanks

-Chuck

---

### Post by dodongo on 2005-08-21
[QUOTE=dodongo]OK, first off, apologies if this isn't in the correct thread -- but I'm 100% sure something I did in KDE / Kubuntu caused this problem.

Essentially, the top panel in GNOME (as well as Gaim, for reasons I've not yet ascertained) have kept the way-too-big-for-GNOME KDE font settings.  In every conceiveable menu I can find to adjust font settings (System -> Preferences -> (Font, Theme, QtConfiguration), as well as in Kconfig itself, I can fiddle with the settings, and those settings *do* take effect in preview & open windows using that toolkit.  Nothing I've found, however, seems to be able to touch the uppermost panel (with Applications, Places, System, etc.).

I've tried googling for this, but I can't come up with the right way to describe it.

Any assistance is appreciated -- help me get my fonts back!!

Thanks

-Chuck[/QUOTE]
 Thanks to the following ~/.gtkrc-2.0 file, my fonts were screwed up:

> # This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Qt/gtk-2.0/gtkrc"

style "user-font"
{
	font_name="Bitstream Vera Sans 12"
}
widget_class "*" style "user-font"

gtk-theme-name="Qt"
gtk-font-name="Bitstream Vera Sans 12"

I simply changed the font sizes (in the above quote, 12) to 10, and the problem was resolved.  Hope maybe that'll help somebody along the way!

---

### Post by flipkick on 2005-11-10
Lovely.I just wiped that damn file right into the gutter ;)

---

### Post by dodongo on 2005-11-10
[QUOTE=flipkick]Lovely.I just wiped that damn file right into the gutter ;)[/QUOTE]
Yes, but did that fix it?!  :)

---

### Post by robstoffers on 2005-11-28
I removed the file, now I can configure my fonts from System->Preferences->Font as per normal again. So yes, removing it works.

---

### Post by dkbg on 2007-03-13
I believe that file is created by KDE to store the settings of GTK+ apps run under KDE. I just deleted it, although it'll probably be recreated the next time I log into KDE (I guess I'll just change the values for font size if that happens). I am very grateful for this thread, that damn file caused me a lot of trouble!

As a sidenote, interestingly enough, Firefox **was** responding to the changes I was making in the GNOME Font preferences, while everything else wasn't, so apparently Firefox wasn't honouring the contents of that file. This makes some sense since it isn't a true GTK+ app, with the chrome widgets and text being drawn by Gecko and styled to emulate GTK+'s appearance, although that doesn't explain why it honours the built-in Font prefs but not that file. Hmm...

---

