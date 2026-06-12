---
title: "OpenGL (Google Earth) in Gutsy with ATI"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by Martin_sensei on 2007-10-23
Hello all,

I have seen a few very similar posts but I am not sure if the answers relate to the current Gutsy release and current restricted ATI drivers so I thought it can't hurt to try for some help...

I have recently installed (from fresh) Gutsy and have managed to get compiz desktop effects working with ease.  However Google Earth refuses to start, it just hangs.  I believe this is something to do with running the ATI card in a XGL environment.

Is there a way to have desktop effects AND run openGL apps like Google Earth with an ATI card?

I am using an ATI X1900XT by the way.

Regards
Martin

---

### Post by KevL on 2007-10-23
I spent a few hours working on this yesterday. Nothing I tried would get Google Earth working. I need Google earth much more than desktop effects so currently I have compiz uninstalled. I would be interested if somebody has got it to work .

Kev

---

### Post by Martin_sensei on 2007-10-23
Do you know if simply turning off all effects via the theme manager would be enough to start using google earth?  Or do you have to disable XGL somehow? :confused:

Cheers

Martin

---

### Post by Martin_sensei on 2007-10-23
Apparently:

"To disable Xgl autostart for this user, create a file named ~/.config/xserver-xgl/disable"

I am not sure exactly how to do this as I am quite new to Linux.  Do I type something like: ```
touch /.config/xserver-xgl/disable
``` from the home directory for that user?

Cheers
Martin

---

### Post by JBAlaska on 2007-10-23
To run Google earth in a limited way under xgl, open a terminal and run "DISPLAY=:0 googleearth " on my system this allows GE to run albeit without window borders since I use emerald.

---

### Post by asiersar on 2007-10-23
The solution provided by Kilz in this thread worked in my case:

[http://ubuntuforums.org/showthread.php?t=520952#8](http://ubuntuforums.org/showthread.php?t=520952#8)

I have an ATI 200m in a Compaq Presario.

---

### Post by Martin_sensei on 2007-10-24
> **JBAlaska said:**
> To run Google earth in a limited way under xgl, open a terminal and run "DISPLAY=:0 googleearth " on my system this allows GE to run albeit without window borders since I use emerald.


Thanks for your help!  This does work in a fashion.  I can launch Google Earth this was, then maximise using F11.  However once I exit google earth my keyboard seems to stop responding, so I am forced to log out and log back in again.  Have you experienced any similar problems?

Cheers

Martin

---

### Post by Martin_sensei on 2007-10-24
> **asiersar said:**
> The solution provided by Kilz in this thread worked in my case:

[http://ubuntuforums.org/showthread.php?t=520952#8](http://ubuntuforums.org/showthread.php?t=520952#8)

I have an ATI 200m in a Compaq Presario.

Works fine! Cheers for that one!  Now I can see google earth in wobbly windows with an ATI card! :KS

---

### Post by fizz on 2007-10-24
updating to the latest aigxl supported ati driver worked for me.. although a lot of artifacting..

---

### Post by carloslosgrande on 2007-10-26
[FONT="Comic Sans MS"]I've got Compiz running perfectly on an ATI X600 card and now thanks to Kilz I've also got GoogleEarth. Those 2 files did the trick. I just copied them straight into the GoogleEarth folder in my home dir. [/FONT]:guitar:

Oops, spoke too soon. Seems to have some other glitch and keeps shutting my system down. Hasn't happened while I'm watching yet so I don't know what is actually happening.

---

### Post by at78rpm on 2008-04-18
Well, that works a little, but GE is still slow as death.

---

### Post by ColJep on 2008-05-19
I have just got Google Earth working on my readom 5600 card by setting desktop effects to none via System>Preferences>Appearance>Visual Effects.

Previously it would start but flicker all over the place.

---

