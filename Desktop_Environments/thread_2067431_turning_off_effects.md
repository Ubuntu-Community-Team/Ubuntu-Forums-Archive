---
title: "turning off effects?"
date: 2012-10-06
forum: Desktop Environments
---

### Post by greatsirkain on 2012-10-06
Hi my OU course started today (thought it was next month but there you go) and ubuntu locks up all the time (11.10 unity 2D). I noticed it's always xorg and unity 2d panel that are eating up the cpu and mem when it freezes. I tried gnome classic but I couldn't find anything easy and it had performance issues of its own mainly due to ubuntuone.
My computer isn't great to start with; 512 ram (8mb reserved for video buffer) P4, 2.8G. Had a look around the forums but I couldn't find anything specific.

The course is IT and computing so I kind of need a computer that I know my way around and doesn't spazz out all the time, is there anyway I can turn off all the bells and whistles for maximum performance?

---

### Post by Frogs Hair on 2012-10-06
2D is already without bell and whistles that is why it's there. You could check out the LXDE or XFCE _sessions_ which are much lighter than the Lubuntu or Xubuntu desktops. The LXDE session is plain Jane but quick and has low memory requirements.  

12.10 has one unity with or without proprietary drivers.

---

### Post by jerrrys on 2012-10-06
> **greatsirkain said:**
> is there anyway I can turn off all the bells and whistles for maximum performance?

Maybe

Either use the mini.iso or the alternate install cd and do a terminal only install.  Then enter:

sudo apt-get install --no-install-recommends ubuntu-desktop

This will install the necessary packages (red) and leave out the recommended packages (green).  This will turn the 600+MB ubuntu-desktop download into a 160MB download and you still have Unity.

Will it be faster?  Your just going to have to try it to know for sure.

[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)

Edit:  If you can live without Unity, an Xubuntu install would give you better performance.

---

### Post by will1982 on 2012-10-06
Hi,

I heard Unity performance was improved in 12.04, and I noticed a slight speed boost after the upgrade.
If it's possible, I suggest upgrading to 12.04.

Best regards,

Will1982

---

### Post by greatsirkain on 2012-10-07
I had a good look around gnome classic with no effects (think I've got the hang of it) then I got xubuntu and lubuntu so I can have a play around and see what feels best, thanks for the suggestions :)

Edit: LXDE seems to be the fastest apart from lubuntu netbook but that's so ugly it made me want to slap my mother, sooo going to see if I can get everything set up the way I like it, thnx again.

---

