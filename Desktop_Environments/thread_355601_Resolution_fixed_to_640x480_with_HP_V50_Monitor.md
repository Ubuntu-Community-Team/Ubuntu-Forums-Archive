---
title: "Resolution fixed to 640x480 with HP V50 Monitor"
date: 2007-02-07
forum: Desktop Environments
---

### Post by taxi.cab on 2007-02-07
[http://h10025.www1.hp.com/ewfrf/wc/product?product=60988&lc=en&cc=us&dlc=pt](http://h10025.www1.hp.com/ewfrf/wc/product?product=60988&lc=en&cc=us&dlc=pt)

This is the culprit. The Ubuntu install worked fine with the monitor I was using before I swapped it with my mother (it was a Dell TFT, she needs the space more than I do, heh!) but now the resolution is fixed to a butt-ugly 640x480 and that's the only option available in 'Preferences > Screen Resolution'. I've tried looking in the 'xorg.conf' doohickey and faffing about, but in all honesty I'm a complete n00b and I doubt my deletion of unsupported resolutions from this file did anything. Nah, it really didn't.

Help?

If anyone needs any info on other hardware I can boot up in XP and get a Belarc profile.

EDIT:

Section "Monitor"

            Identifier         "Generic Monitor"
            HorizSync 28 - 57
            VertRefresh 50 - 100

EndSection

Editing xorg.conf with that instead of the previous entry did the trick. Special thanks to l_bratch of the PC Gamer forum.

---

### Post by krotaz on 2007-02-09
hi there.

I've got the same problem and I was able to solve it.

First of all, install the drivers for your video card, if it's a Nvidia use [Automatix]("http://www.getautomatix.com/"), it's great.

After that, check this page

[http://www.html4.com/mime/txt/linuxGoodies/MonitorsDB](http://www.html4.com/mime/txt/linuxGoodies/MonitorsDB)

There you'll see that your monitor has this specs

Compaq; Compaq V50 Color Monitor; cpq1322; 30.0-60.0; 50-125.0; 1

where cpq1322 is the identifier, 30.0-60.0 is the H-Sync, 50-125.0 is the V-sync and DPMS supported is 1.

Now you just have to edit the /etc/X11/xorg.conf file and put this data instead the "GENERIC" one.

Ok now you 've  to add the resulution you want in the options in the display part and that's it

Check that in the display part you've to change the "Generic Monitor" for "cpq1322"

Hope it works

---

