---
title: "nVidia Twinview"
date: 2005-09-04
forum: Desktop Environments
---

### Post by Sale on 2005-09-04
Hi everyone :)

I'm new to Ubuntu (and Linux), and I hope this is the right forum to ask this question.

Her is the relevant part of my xorg.conf file:

Option "TwinView" "true"

Option "TwinViewOrientation" "Clone"

Option "TVOutFormat" "SVIDEO"

Option "TVStandard" "PAL-G"

Option "SecondMonitorHorizSync" "30-50"

Option "SecondMonitorVertRefresh" "60"

Option "MetaModes" "1280x1024,1280x1024;1024x768,1024x768;800x600,800x600;640x480,640x480;  512x384,512x384"

However, in this configxuration, there is no picture on my TV, the picture only shows up when I remove the "1280x1024,1280x1024" section from the "meta modes" section. 

Can anyone tell me how can I have 1280x1024 resolution on my monitor, *and* a picture on the TV.

TIA

SAle

---

### Post by Lux Perpetua on 2005-09-04
Actually, this forum is for guides and howtos, not questions ;) Try [Hoary Hardware Help](http://www.ubuntuforums.org/forumdisplay.php?f=57).

---

### Post by poofyhairguy on 2005-09-04
Its not I moved it.

[http://www.ubuntuforums.org/showthread.php?t=23628](http://www.ubuntuforums.org/showthread.php?t=23628)

---

### Post by Iznogood on 2005-09-04
Try this

Option "MetaModes" "1280x1024,1024x768;1280x1024,800x600;1280x1024;640x480;1024x768,1024x768;800x600,800x600;640x480,640x480;  512x384,512x384"

As far as I know  1024x768 is the largest resolution you can get on a normal tv (not LCD)

Iz


Edit : Here is my modline

"MetaModes" "1024x768, 1280x1024 ;1024x768,1024x768;800x600,800x600;640x480,640x480"

---

