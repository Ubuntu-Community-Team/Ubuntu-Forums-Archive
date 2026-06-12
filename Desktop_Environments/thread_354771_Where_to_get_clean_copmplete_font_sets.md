---
title: "Where to get clean copmplete font sets?"
date: 2007-02-06
forum: Desktop Environments
---

### Post by shareMenaPeace on 2007-02-06
Hi, 
i useing gimp to create some text i installed allready the msttcorefonts but nearly each single font i choose under gimp is either not complete (lacking characters) or looks not clean.

Does anyone can point me to a font pack which has complete clean fonts for linux?

Thx

---

### Post by jmc1 on 2007-02-06
I don't know if this is any help or not, but I was able to copy all my Windows fonts to Linux. I simply copied all the fonts from the Windows/Fonts folder to a folder in Linux, and then I copied them into the Fonts folder in Linux by going to System>Preferences>Font, clicking "Details" and clicking "Go To Font Folder." You have to reboot and then go to the terminal and run** sudo fc-cache -f -v** to rebuild the font cache. They should show up.

Hope this helps, but they aren't technically "linux" fonts are they? They seem to work just fine though.

---

### Post by shareMenaPeace on 2007-02-06
thx!

great info will try this, cheers.

---

### Post by jmc1 on 2007-02-06
Well since you helped me out with my Beryl issue I kinda felt obligated...
Shame I can't get it to work but that's the price of having a system barely over a month old, and with a brand new video card too, which I found out via Digg.com that XGL and Beryl are both unsupported on my ATI Xpress 1150 despite what the tutorials say.

---

### Post by shareMenaPeace on 2007-02-06
Thanks, well i guess you got a xorg.conf problem ... try out some "device" and "Screen" settings  from another user relative to your hardware specs. - check the offical forum too.
[http://www.beryl-project.org/](http://www.beryl-project.org/)

If this not help try with the next release or try compiz (beryl is a fork).


Cheers

---

