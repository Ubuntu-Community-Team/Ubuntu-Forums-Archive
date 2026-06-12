---
title: "Adding Fonts Locally"
date: 2006-01-07
forum: Desktop Environments
---

### Post by orev on 2006-01-07
So....I have a directory of .TTF and .PFB fonts on my desktop that I saved from another computer.  I now need to know how to add these fonts to my locally usuable fonts.  I have located my currently usuable fonts in /usr/share/fonts/ but I am unable to directly copy the fonts from the destop directory to this ../fonts/ directory.  I also assume (scary) that I will need to regenerate (?) the fonts cache too.

Any kind words or advice would be most appreciated...

10000 thanks.

---

### Post by manubreizh on 2006-01-07
hi,
you can use system settings > system administration > fonts settings (or something like that) ; you must click superuser (and add your user password (like for sudo in shell)), then click "add", then browse to your location where the font files are and add them. after restarting kde (ctrl+alt+backspace), they must be installed.
hope that help

---

### Post by orev on 2006-01-07
Can't believe I missed that....I guess I've never looked at that before in the system settings!!!


Thanks!

---

### Post by angrykeyboarder on 2006-01-08
[QUOTE=orev]So....I have a directory of .TTF and .PFB fonts on my desktop that I saved from another computer.  I now need to know how to add these fonts to my locally usuable fonts.  I have located my currently usuable fonts in /usr/share/fonts/ but I am unable to directly copy the fonts from the destop directory to this ../fonts/ directory.  I also assume (scary) that I will need to regenerate (?) the fonts cache too.

Any kind words or advice would be most appreciated...

10000 thanks.[/QUOTE]

The simplest thing to have done would have been move that directory to ~/.fonts

Then all the fonts in it would be installed locally. Sometimes this requires a restart of KDE in order for the fonts to show up in KDE apps, but sometimes not. I've never quite figured out that one.

---

### Post by orev on 2006-01-09
funniest thing about all of this is that when I added the fonts through system setting and then did a CTRL ALT BACKSPACE to restart x, somehow x did not restart...and would not restart....

I tried startx, startkdm - and got errors about x connection failures each time

So, I then tried to reinstall x and kdm through the command line...nothing....just dependancy problems with kdm and continued xserver connection issues....

I reinstalled kubuntu....but wow.....:confused:

---

