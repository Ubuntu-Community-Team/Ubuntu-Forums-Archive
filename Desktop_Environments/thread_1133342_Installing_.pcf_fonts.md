---
title: "Installing .pcf fonts"
date: 2009-04-22
forum: Desktop Environments
---

### Post by Grievous on 2009-04-22
I'm a newbie in installing fonts.  Never had installed fonts in Windows before as well.  I had downloaded some artwiz fonts and couldnt find a fonts folder even though I have tried viewing the hidden items. How about for mouse themes? :confused:

---

### Post by Grievous on 2009-04-23
Anyone? :confused::confused:

---

### Post by smudi on 2009-04-25
This seems to be an issue for a long time now.

While this used to work:
[http://www.nazgum.com/2007/12/09/ubuntu-pcf-fonts/](http://www.nazgum.com/2007/12/09/ubuntu-pcf-fonts/)
There is one more step which works for me on Jaunty.

I looked into a xfont-terminus pkg, which is comprised of pcf fonts, and works just fine.

The package installed this suspicious file:
/etc/fonts/conf.d/50-enable-terminus.conf

It seems as fontconfig can accept bitmap fonts even when it is configured not to.
The same directory holds:
70-no-bitmaps.conf
A link to 
/etc/fonts/conf.avail/70-no-bitmaps.conf
which explicitly rejects loading of bitmap fonts, even if we fontconfig-ured otherwise.
Next to it resides:
70-yes-bitmaps.conf
so I deleted the 70-no-bitmaps.conf into a 70-yes-bitmaps.conf link. 

fc-cache command now recognized the pcf fonts, and after restarting xserver, I could see all the forsaken bitmap fonts.

Bear in mind though, that there was a good reason to discard bitmap fonts, as it made all sorts of havoc with applications like firefox. 
You can be more prudent by mimicking the behaviour of terminus, and explicitly allowing a specific bitmap font to load instead of a few dozens.

---

