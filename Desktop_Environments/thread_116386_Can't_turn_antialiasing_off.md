---
title: "Can't turn antialiasing off"
date: 2006-01-12
forum: Desktop Environments
---

### Post by el3ktro on 2006-01-12
I don't know what happened. I always had antialiasing turned off because it is so incredible slow, but now, it is suddenly turned on again. I opened kcontrol, which showed antialiasing deselected. I activated it, deactivated it again, but it's still there. I can't turn it off anymore. Does somebody know in which config file antialiasing is controled? I really want to get rid of it, it's so damn slow on my NVidia card.

Tom

---

### Post by obibok on 2006-01-14
Try renaming **~/.fonts.conf** to something else, like *.font.conf.old* and log out and back in to KDE. Then, see if you can turn off antialiasing through the KDE GUI tool.

---

### Post by el3ktro on 2006-01-15
Hello,
thanks for this tip but I'm afraid it didn't work. My fonts.conf only has two config options for font hinting, but not font antialiasing. Do you have such an option in your fonts.conf? I've also searched all KDE config files, but can also only find options for font hinting, but not antialiasing. This is so weird, especially because this behaviour started from one day to the next, and I always had antialiasing turned off.

Well another thing: I'd like to have antialiasing on actually, if it was just not so damn slow. Is there something I can do about this? I have a recent NVidia card & the nvidia drivers installed.

Tom

---

### Post by obibok on 2006-01-15
My *.fonts.conf* is heavily customized, so the answer is *yes*. This is how you can turn off anti-aliasing:

```
<match target="font">
  <edit name="antialias" mode="assign">
   <bool>false</bool>
  </edit>
 </match>
```

[SIZE="1"]* if you want to take a look at my entire *.fonts.conf*, check out the link in my sig[/SIZE]

As for anti-aliasing being slow, I'm not sure about this one.

---

### Post by el3ktro on 2006-01-15
Thanks a lot, I now have it turned off. I just don't know how it happened that it suddenly was turned on. I wonder if you know a font that looks good w/o antialiasing? I'm using Bitstream Vera Sans currently, but it doesn't look so good w/o ntialiasing.

Tom

---

### Post by obibok on 2006-01-15
IMHO the best-looking non-antialiased fonts are **Arial** and **Veranda**. Some people also use *Tahoma*.

---

### Post by mgor on 2006-01-15
re-configure fontconfig,
```
sudo dpkg-reconfigure fontconfig
```
and turn-off antialiasing.

---

### Post by jferrando on 2006-01-15
You can copy windows TTF fonts. They are the best no doubt, and you can have "Courier New", "Times New Roman", "Tahoma", "Verdana", "Arial", etc.
I don't know about legal aspects and licensing.

---

### Post by el3ktro on 2006-01-16
I'm using Arial now. I also remembered Tahoma, and installed the msttcorefonts from apt, but Tahoma wasn't in, so I'm using Arial now, looks very good. I hope X gets replaced soon - this is so crappy technology. Throws Linux behind all other OSes when it comes to graphics :-( I'm looking forward to XGL, perhaps we can then have SVG-fonts which are rendered+antialiased by the graphics hardware :-D

Tom

---

