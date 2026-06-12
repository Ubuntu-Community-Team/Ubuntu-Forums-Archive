---
title: "Need help converting Mac fonts for use in ubuntu"
date: 2005-07-15
forum: Desktop Environments
---

### Post by secundar on 2005-07-15
Hi all,

I'm a recent switcher. From Mac to Ubuntu (and a little Windows  :? ).

I have a bunch of fonts that are still on my Mac. When I SSH or SAMBA over to it from my ubuntu machine the darn things read as zero kb because of the way the Mac stores certain files. I *hate* that!

Is there an easy peasy way to convert those fonts (otf, ttf and type 1) without opening each individually with fontforge?

---

### Post by doclivingston on 2005-07-15
You'll probably have to convert it on the Mac, there should be some programs floating around on the Internet for this (I had one about 10 years ago on my LCii).


From google (I haven't checked whether any of these work, or not):
[http://web.mit.edu/zudark/larabiefonts/arc/ttconverter.hqx](http://web.mit.edu/zudark/larabiefonts/arc/ttconverter.hqx)  - this is the program I had on my mac 10 years ago :)
[http://fondu.sourceforge.net/](http://fondu.sourceforge.net/)  - says it will work it from the Linux side, if you put macbinary encode or binhex the fonts.

---

### Post by maruchan on 2005-07-16
[http://ywwg.com/wordpress/?p=194](http://ywwg.com/wordpress/?p=194)

[http://wiki.scribus.net:81/index.php/Converting_Mac_fonts_for_use_with_Scribus](http://wiki.scribus.net:81/index.php/Converting_Mac_fonts_for_use_with_Scribus)

---

### Post by secundar on 2005-07-16
Thanks guys! I ssh'd into my mac and used fondu. It became a tedious endeavor when I had to do some pfb's separately - fondu wanted to write them all as Untitled.

There must be an easier way to carry the font name over to the converted pfb and batch them all.

---

