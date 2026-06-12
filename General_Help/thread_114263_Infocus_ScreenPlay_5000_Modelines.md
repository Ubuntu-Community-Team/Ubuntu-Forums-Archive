---
title: "Infocus ScreenPlay 5000 Modelines"
date: 2006-01-08
forum: General Help
---

### Post by Tal on 2006-01-08
I had another thread asking about the Screen Play 5000 and valid Modelines for getting 720P (it's native resolution) working with Ubuntu. I picked up an M1A to DVi cable off of ebay and was able to see fglrx report (in my xorg log) some valid modelines for this projector, so I thought that I would post them for others in case they are curious. I had a lot of trouble finding them myself, and had motion blur and other issues when using the standard ATSC and other modelines discussed on other pages. Here they are!
-------------------------------------------
Modeline "1920x1080"  172.80  1920 2040 2248 2576  1080 1081 1084 1118
Modeline "1280x720"   74.20  1280 1390 1430 1650  720 725 730 750 +csync
Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806
-------------------------------------------

you'll note the +csync, which I haven't checked to see what it does exactly, but I know that I hadn't seen this in any other modelines listed elsewhere. Give these a try and see what you think.

---

### Post by nerval on 2006-01-08
This might be helpful too for hdtv;
[http://gentoo-wiki.com/HOWTO_Xorg_HDTV](http://gentoo-wiki.com/HOWTO_Xorg_HDTV)

---

