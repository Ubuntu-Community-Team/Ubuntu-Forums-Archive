---
title: "[SOLVED] compiz fusion and screensaver problems"
date: 2007-09-06
forum: Desktop Effects &amp; Customization
---

### Post by kubilaycan on 2007-09-06
hi

i have compiz fusion installed and running properly. i have noticed that it seems to override my gnome screensaver settings.before i installed compizfusion, i had disabled all screensavers but set to turn the monitor off after an hour of idle. 

after i installed compiz fusion, the monitor puts on a blank screensaver after 10 minutes, and about 10 minutes later it switches off. i check in the gnome screensaver it still has my old settings.

so i thought compiz fusion might have its own screensaver settings but i fail to find anything like that in compizconfig settings manager..

help! this is annoying, cant watch a proper movie anymore.

---

### Post by kubilaycan on 2007-09-15
solved: 

i read from another thread (i cant find it anymore) that i had to add these to the end of my xorg.conf

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

---

### Post by G-forze on 2007-12-03
Yes, works! Oh how I have been looking for the solution to this problem. My user experience of Ubuntu just rose tenfold. :)

---

### Post by tligman on 2008-01-11
> **kubilaycan said:**
> solved: 

i read from another thread (i cant find it anymore) that i had to add these to the end of my xorg.conf

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

So this sounds like it disables the screensaver altogether, or does it just let you go back to the gnome screensaver settings?  I like having a screensaver, but I prefer it not to interrupt video playback in VLC, and I'm having this same issue.

---

### Post by kubilaycan on 2008-01-11
it disables it completely.. and no matter what u change the gnome settings to from the screensaver options, it wont matter.. 

its not a very satisfying solution, rather a very brutal....

---

### Post by tligman on 2008-01-11
uggh.  thanks for answering, i guess I don't *need* a screen saver...

---

### Post by hetzz on 2008-01-16
My system freeze when i try to configure screensaver with gnome standard application.
I really dont consider deactivating all sorts of screensaver as an alternative. Is there a config for compiz-screensaver?

---

