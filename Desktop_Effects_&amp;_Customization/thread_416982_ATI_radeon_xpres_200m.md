---
title: "ATI radeon xpres 200m"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by Give_Peace_A_Chance on 2007-04-21
Well desktop effects is not working, ends up with a white screen if i enable it, i was wondering if anyone would be kind enough to help me with this problem Via aim so or pm?

---

### Post by orange2k on 2007-04-21
Have you installed the drivers for your card?

And what Ubuntu are you using - is it 7.04?

If it`s 7.04 you can just enable the driver by going to system - administration - restricted driver manager...  

At least that`s how I did it

---

### Post by Give_Peace_A_Chance on 2007-04-21
Ok i got the drivers and now when I try to start up the desktop effects it says the composite extension is not available.

---

### Post by jaimz on 2007-04-21
did you install the fglrx drivers from ATI?

---

### Post by Give_Peace_A_Chance on 2007-04-21
I don't know i went to the thing under setting and did that.
Is there something I have to do to get that?

---

### Post by Give_Peace_A_Chance on 2007-04-21
Well i got fglrx installed and desktop effects is still not working

The Composite extension is not available
:confused:

---

### Post by thau on 2007-04-21
You can activate Composite by adding:

Section "Extensions"
        Option          "Composite"     "enable"	
EndSection

to your /etc/X11/xorg.conf

I did it but it still doesnt work though so d I wouldnt bother, when I tried to activate desktop effects after activating the composite extension i got rid of the first message. But when i click th button to activate desktop effects it just says it cant. Anyone knows a workaround for this?

---

### Post by jazzman83 on 2007-04-22
> **thau said:**
> You can activate Composite by adding:

Section "Extensions"
        Option          "Composite"     "enable"	
EndSection

to your /etc/X11/xorg.conf

I did it but it still doesnt work though so d I wouldnt bother, when I tried to activate desktop effects after activating the composite extension i got rid of the first message. But when i click th button to activate desktop effects it just says it cant. Anyone knows a workaround for this?

This is my issue as well.  I have installed the restricted ATI drivers and enabled composite but Desktop Effects just tells me that it won't enable.

---

