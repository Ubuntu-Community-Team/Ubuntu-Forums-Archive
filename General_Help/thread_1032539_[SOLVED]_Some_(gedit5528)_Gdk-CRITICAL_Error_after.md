---
title: "[SOLVED] Some (gedit:5528): Gdk-CRITICAL Error after i decide to edit."
date: 2009-01-06
forum: General Help
---

### Post by morbid_bean on 2009-01-06
Anytime I decide to edit a file I will get this weird error:

```
jimbo@monster:~$ sudo gedit /etc/X11/xorg.conf
[sudo] password for jimbo: 

(gedit:5528): Gdk-CRITICAL **: gdk_display_get_default_screen: assertion `GDK_IS_DISPLAY (display)' failed

(gedit:5528): Gdk-CRITICAL **: gdk_screen_get_width: assertion `GDK_IS_SCREEN (screen)' failed

(gedit:5528): Gdk-CRITICAL **: gdk_display_get_default_screen: assertion `GDK_IS_DISPLAY (display)' failed

(gedit:5528): Gdk-CRITICAL **: gdk_screen_get_height: assertion `GDK_IS_SCREEN (screen)' failed

(gedit:5528): Gdk-CRITICAL **: gdk_display_get_default_screen: assertion `GDK_IS_DISPLAY (display)' failed

(gedit:5528): Gdk-CRITICAL **: gdk_screen_get_width: assertion `GDK_IS_SCREEN (screen)' failed

(gedit:5528): Gdk-CRITICAL **: gdk_display_get_default_screen: assertion `GDK_IS_DISPLAY (display)' failed

(gedit:5528): Gdk-CRITICAL **: gdk_screen_get_height: assertion `GDK_IS_SCREEN (screen)' failed
```

Now the thing will still pop up and I can edit with no problem....any idea what this stuff is?

---

### Post by Tim Sharitt on 2009-01-06
I may have something to do with running sudo instead of gksudo. gksudo is the prefered way to run non-cli apps.

---

### Post by morbid_bean on 2009-01-09
> **Tim Sharitt said:**
> I may have something to do with running sudo instead of gksudo. gksudo is the prefered way to run non-cli apps.

Tried using gksudo instead but I get the same thing... :confused:

---

### Post by Tim Sharitt on 2009-01-09
I can't really say what the problem is. I don't get anything like that, though I seems like I may have in gusty, I'm runnig hardy now. It would seem to be a bug in either the gedit code or gdk code. I would guess that some thing changed with gdk assertions, but that they were not properly implemented in gedit. 

If it still runs fine I wouldn't worry about it.

Just out of curiosity, what version of Ubuntu are you running, and do you get the same errors when running gedit from a terminal without root priviledges?

---

### Post by morbid_bean on 2009-01-09
> **Tim Sharitt said:**
> I can't really say what the problem is. I don't get anything like that, though I seems like I may have in gusty, I'm runnig hardy now. It would seem to be a bug in either the gedit code or gdk code. I would guess that some thing changed with gdk assertions, but that they were not properly implemented in gedit. 

If it still runs fine I wouldn't worry about it.

Just out of curiosity, what version of Ubuntu are you running, and do you get the same errors when running gedit from a terminal without root priviledges?

Im using ibex, and how do i open a terminal without root privileges?

---

### Post by Tim Sharitt on 2009-01-09
> **morbid_bean said:**
> Im using ibex, and how do i open a terminal without root privileges?
I meant run gedit from the terminal without using sudo or gksudo.

---

### Post by morbid_bean on 2009-01-09
Hmm weird...same thing...oh well it doesnt really affect anything so its not a big deal:D

---

### Post by Tim Sharitt on 2009-01-09
Must not be a critiacal bug if it hasn't been fixed. Thanks for indulging my curiosity.

---

### Post by morbid_bean on 2009-01-09
I figured it out after doing some research If found out its a bug with my current gdk theme so i switched to a different theme temporarily and it didn't show the odd errors. So that means this thread is officially solved

---

