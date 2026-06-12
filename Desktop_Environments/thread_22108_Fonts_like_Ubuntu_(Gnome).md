---
title: "Fonts like Ubuntu (Gnome)"
date: 2005-03-25
forum: Desktop Environments
---

### Post by vvu on 2005-03-25
I have (1)  copied my TTF fonts from Windows and (2) enabled antialiasing - (3)  rebuilt the font cache - and it is still not as crisp or clean as Ubuntu (Gnome) version.

It did help that I did all of the above, but it is not as smooth.  I am using Arial 12 (best standard one) as my universal fonts for KDE.  Any other suggestions?

---

### Post by Ironi on 2005-03-26
Check out the GNOME font settings: run **gnome-control-center** and double click 'Font' then click 'Details...' (GNOME can render fonts at different DPI settings than the X server; KDE apparently can't). Note the DPI, smoothing, and hinting settings.

If you want to change the DPI (find the current with **xdpyinfo |grep dots**) and you're using KDM, open /etc/kde3/kdm/Xservers and add your DPI setting like so:

:0 local@tty1 /usr/X11R6/bin/X -nolisten tcp **-dpi 96**
 
 
As for the smoothing and hinting: run **kcmshell fonts**, click 'Configure...' and set them to match GNOME's.

---

### Post by chavo on 2005-03-26
I was a long time Mandrake user looking to find a new distro. I wanted something a little more up to date, or easy to update, and I love KDE. So I decided to install kubuntu. 
Well I had it running for about a week or so, and couldn't figure out why my fonts didn't look the same as on my Mandrake installs. I recompiled QT using Mandrake's source and patches, I rebuilt KDE, as I have been building from cvs anyway. But still the fonts didn't look as crisp. 
Then I finally tried building and installing freetype from source.  I logged out and back in and voila, my fonts are crisp and clean and I'm very happy.
So I'm no expert, but I do like to tinker. I don't know if ubuntu patches freetype in anyway, but these steps produced what I was looking for.
One other thing -> an easy way to adjust your DPI is to add this to ~/.Xresources ->
Xft.dpi: 96
Of course you can change it to whatever you like, I keep mine at 100 in KDE. For some reason 96 doesn't seem like enough.

Anyway, good luck. And thanks to the ubuntu folks for such a fine effort.

---

### Post by Ironi on 2005-03-26
[QUOTE=chavo]Then I finally tried building and installing freetype from source. I logged out and back in and voila, my fonts are crisp and clean and I'm very happy.
[/QUOTE]
Hmm, that shouldn't be necessary these days.

> 
One other thing -> an easy way to adjust your DPI is to add this to ~/.Xresources ->
Xft.dpi: 96

That's good to know.

> 
Of course you can change it to whatever you like, I keep mine at 100 in KDE. For some reason 96 doesn't seem like enough.

I use 96 instead because at 100, Bitstream Vera Sans 6 is a bit too small, and 7 a bit too large for "small" text. Whatever works. :)

---

