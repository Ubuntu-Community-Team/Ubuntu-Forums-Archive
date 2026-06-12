---
title: "All themes have gone..."
date: 2009-02-18
forum: Desktop Environments
---

### Post by scary_jeff on 2009-02-18
Hi

I was trying to get Gnomad to work with my mp3 player, which involved building it from source. To do this I ended up building and installing the following (I realised afterwards that I probably didn't need to do this):
atk 1.24
glib-2.18.4
gtk+ 2.14.7
pango 1.20.5
tiff 3.8.2

Only after this was all finished, and I opened a new window, did I realise that one of these broke all my themes. The gnome-appearance-properties shows only the Human theme, but says "This theme will not look as intended because the required GTK+ theme 'Human' is not installed."
If I try and install this with apt-get, it says it's already installed. If I remove --purge it, then install, it doesn't make any difference.

The themes seem to be present in /usr/share/themes and /usr/themes. I don't know which location they are supposed to be in.

Any help with this would really be appreciated, I've spent the last two extremely frustrating hours trying to solve it, without making any progress at all :( I don't have any custom themes so just restoring whatever the defaults are would be great.

Oops, it's Ubuntu 8.10

---

### Post by scary_jeff on 2009-02-20
Oh well, since the machine was so messed up by this, I ended up reinstalling 8.10 from scratch.
On the plus side, this wasn't that big a deal, because pretty much everything I need works out of the box.

---

