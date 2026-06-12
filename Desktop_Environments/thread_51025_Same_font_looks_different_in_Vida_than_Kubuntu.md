---
title: "Same font looks different in Vida than Kubuntu"
date: 2005-07-22
forum: Desktop Environments
---

### Post by Circlotron on 2005-07-22
I have a dual-boot Kubuntu + VidaLinux setup. Kubuntu lives on /dev/hda and is there solely for the purpose of rescuing Vida :roll:  I have the fonts set the same for both distros Trouble is, the fonts look better in Kubuntu than Vida. Specifically, using Bitstream Vera sans the letters on menus look thicker and blurrier. I have the anti-aliasing set *exactly* the same for both. The screen shot should tell all. What can I do???
[http://photobucket.com/albums/a79/Circlotron/?action=view&current=Bothmenus.png](http://photobucket.com/albums/a79/Circlotron/?action=view&current=Bothmenus.png)

---

### Post by Footer on 2005-07-22
Dumb question maybe but ... Do you have the horiz/vert refresh rates set the same in each?  One other thought, perhaps one font is set to "bold" while the other isn't?

---

### Post by Circlotron on 2005-07-22
1024x768x75Hz both cases.
Not bold.

---

### Post by elsewhere on 2005-07-22
Just a shot, but are your dpi settings the same for X in each distro ? 96 dpi is optimal but I had to tweak mine in Kubuntu to get that.  It does impact the font quality.

Try running *xpdyinfo | grep resolution*

Cheers,
KV

---

### Post by Circlotron on 2005-07-23
It was 72 dpi in both distros. Fiddled it up to 96 dpi and set the fonts to the same apparent size and it was absolutely no different. 

Then.... after asking around at the Gentoo forum, I was told "Looks like freetype was compiled with bindist. Never used vida but in gentoo you'd type "USE="-bindist" emerge freetype" and the fonts would look like they do in kubuntu."

So I dragged /usr/lib/libfreetype.so.6.3.5 from the Ubuntu setup into Vida and *voila*. :D :D :D

---

