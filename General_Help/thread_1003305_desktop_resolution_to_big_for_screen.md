---
title: "desktop resolution to big for screen"
date: 2008-12-06
forum: General Help
---

### Post by swiftarcon on 2008-12-06
Iv looked through alot of similar discussions that were solved but the only one that i haven't been able to try involves using xvidtune, when i do this i get the message: Unable to query monitor info. im using a Polaroid TLA-01911C 19" LCD tv as a monitor.my correct native resolution is detected and used as default but it goes off the screen on every side, in windows Nvidia had a rescaling tool that fixed this with a click and drag

iv searched in my manual and on their site for the required info with no luck. as for my xorg.conf it is unmodified since first install, everytihng iv tried with it wouldnt allow me to boot and i had to return to defaults. plz help

---

### Post by thotmos on 2008-12-07
I had a similar problem with my HPL1706 LCD, which i solved by restoring to factory settings. If you have some sort of auto adjustment in your monitor, try it.

---

### Post by linux_tech on 2008-12-07
Try changing resolution using xrandr.   xrandr is a command that will change screen size

from- man xrandr
xrandr [-help]  [-display display] [-o orientation] [-q] [-v] [-s size]

ie
xrandr --output LVDS --mode 1024x768
```
xrandr -s 1024x768 
``` or whatever resolution

---

### Post by mahesan on 2009-11-01
I do have the same problem.

I was happy when I read "Ubuntu 9.10 is out!"
But when I tried on my PC, I realises that "Ubuntu is really OUT!"
I did a clean installation (madly believing that everything would be all right), but only to find out that
My Monitor "ViewSonic E55" is not detected, but set the resolution to 800x600.

[Mouse Button clicking on some applications (e.g. Compiz manager)  makes the window shift left/right without letting me do the selection.

My Graphics card is Intel 845GM
I believe it is correctly detected and is well handled by "xserver-xorg-video-intel"

Do I have to go back to Ubuntu-9.04?
My dear friends, kindly let me know what I am missing....
Thanks a lot

Ubuntu-Blacky
02 November 2009

---

### Post by mahesan on 2009-11-01
/***
 xrandr [-help] [-display display] [-o orientation] [-q] [-v] [-s size]
ie
xrandr --output LVDS --mode 1024x768
***/

This does not work for me.. it says 
"Size 1024x768 not found in available modes"
:(
-Ubuntu Blacky
02 November 2009

---

### Post by Nasraf on 2010-01-15
I got the same problem.
I'm running Ubuntu 9.10 32 bit on my new ASRock ION 330 HT [http://www.asrock.com/Nettop/overview.asp?Model=ION%20330HT]("http://www.asrock.com/Nettop/overview.asp?Model=ION%20330HT") that is connected with my 42" plasma tv from Pioneer PDP-427XA [http://www.pioneer.eu/eur/products/archive/PDP-427XA/index.html](http://www.pioneer.eu/eur/products/archive/PDP-427XA/index.html)
The resolution is set to 1920x1080 by default. And that makes the desktop too big for my tv with  approximately 1 cm at the top, bottom and each side of the visible screen. Im mainly using my ASRock as mediacenter through XBMC in which I fond a very practical zoom function   SYSTEM > SETTINGS > APPEARANCE and changing the ZOOM option to -4 . That reveals the whole "desktop" in XBMC.
Now I wonder is there a way to zoom out from the desktop in Ubuntu 9.10, so that the menu bar at the top and the bottom bar is visible, without changing the resolution?

My Pioneer is supposed to handle 1080p, maby thats the problem...

---

### Post by xXxTHADDEUSxXx on 2010-02-28
i'm having this problem too with my sony 40in lcd. i have found that in the display preferences its saying my monitor is a 72in sony...(i wish)...and when i type the xrandr command it says my screen is 1600mm x 900mm...which im guessing is what a 72in would be.

has anyone else checked their screen size to see what it says and if its right? how do u fix this?

by the way, ive never even touched a linux system until i loaded ubuntu 9.10 on my new computer i built yesterday so sorry if i sound like an idiot.

---

