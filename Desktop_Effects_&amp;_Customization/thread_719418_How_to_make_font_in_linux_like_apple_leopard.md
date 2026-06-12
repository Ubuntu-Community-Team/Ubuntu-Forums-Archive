---
title: "How to make font in linux like apple leopard ?"
date: 2008-03-09
forum: Desktop Effects &amp; Customization
---

### Post by solidsnake on 2008-03-09
Hi all, I've try a lot of customization in linux .fonts.conf but I can't have the font on my linux kubuntu to look like leopard (apple osx).

Anyone else have some tips to render the fonts like osx ?

I've try to apply turners patch, RGB on, off, hinting full, medium slight and none...

thanks :-)

here is now my fonts.conf :

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="dpi" >
   <double>100</double>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

---

### Post by raul_ on 2008-03-09
Just download them from a fonts site, place them in /usr/share/fonts/ttf (or something like that) and choose them in the System Settings -> Appearance -> Fonts (or something like that)

---

### Post by KStorm on 2008-03-09
You can come close to apple-type fonts by downloading apple fonts from here:

[http://www.osx-e.com/downloads/misc/macfonts.html](http://www.osx-e.com/downloads/misc/macfonts.html)

As root, extract them into your fonts folder.  I made a folder named ttf-apple in usr/share/fonts/truetype and just extracted them into there.

My screenshot illustrates my attempt with at least a couple of apple fonts (note: screenshot is only blurry because it's an 'exported' jpeg; I assure you your desktop will look much better than that).

---

