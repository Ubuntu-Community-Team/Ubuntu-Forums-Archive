---
title: "Inspiron 6400 - Ubuntu not starting anymore after change in graphical settings"
date: 2008-09-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vitt1984 on 2008-09-27
Hi everybody,

some days ago i had some problems with Firefox being too slow with Ubuntu 7.10 Gutsy. After unsuccessfully trying to change some settings in Firefox itself, i found a website which claimed that a possible reason for my problem could have been the settings with my graphical card.

So i went and followed the instructions (i can't unfortunately find the website anymore :( ) to reinstall my graphic card and guess what, now Ubuntu doesn't want to start anymore :)

All i get is the "Starting up..." words, then it looks like the screen is attempting to change to another resolution, then everything stops, and i'm left with a black screen. I also tried typing Username and Password as i would do normally, just to check if maybe the Login was there, just not shown, but to no avail.

I think what i need is something to switch the graphical settings back to Default - but it looks like Ubuntu is supposed to this by itself. On these forums i also the advice to use "sudo dpkg-configure xserver-xorg" - so i tried but it cannot autodetect my card and i tried with "ati" and "vesa" drivers - same results as before.

So here i am begging for help on my knees :) My Dell is an Inspiron 6400, my graphic card ATI Mobility Radeon X1400 and i am (was :) ) using Ubuntu 7.10 Gutsy Gibbon.

The biggest problem is of course not being able to start up, but if somebody can come up with a good tutorial to configure my card - that would be great as well.

Any help is appreciated :)

---

### Post by vitt1984 on 2008-10-05
Just a bump - i'm not sure if it's allowed. Maybe i shuold just post in another section.

---

### Post by H4ck3rz on 2008-10-16
set ur resolution as it asks then turn off ur computer & restart it should then reconfig its self to default stat then download envyNG-core & envyNG-gtk & istall the drivers that way it might help im not sure but worth a try

---

### Post by natehall on 2008-10-17
Since a new version of Ubuntu is coming out in a few days I'd suggest using a live cd to boot up with, save any data that you'd like, then do a fresh Install with the latest version.

---

### Post by vitt1984 on 2008-10-31
> **natehall said:**
> Since a new version of Ubuntu is coming out in a few days I'd suggest using a live cd to boot up with, save any data that you'd like, then do a fresh Install with the latest version.

Thanks to both, i think i'll go with the reinstall...

---

