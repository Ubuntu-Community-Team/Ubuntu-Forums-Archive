---
title: "Multiple Sound Cards"
date: 2005-12-26
forum: General Help
---

### Post by toran on 2005-12-26
Hey guys, I just recently got an external soundcard for my laptop.

I plugged it in, and then checked /proc/asound/cards. Both my internal/integrated card and external (newly purchased) card are listed, like so:

```
0 [I82801CAICH3   ]: ICH - Intel 82801CA-ICH3
                     Intel 82801CA-ICH3 with AD1881A at 0x1c00, irq 11
1 [PSC805         ]: USB-Audio - Philips PSC805
                     Philips Electronics Philips PSC805 at usb-0000:00:1d.1-1, full speed
```

How can I set my new card to the default card? My computer is not using the new card, sound continues to play out of the old card.

Thanks!

---

### Post by 23meg on 2005-12-26
Is it selectable in System / Preferences / Sound?

---

### Post by loboc on 2007-11-05
Use asoundconf like in this post

[http://ubuntuforums.org/showthread.php?t=322383&highlight=psc805](http://ubuntuforums.org/showthread.php?t=322383&highlight=psc805)

to set it as the default alsa card then select alsa as your sound provider in 
 
System /Preferences/Sound

There are other threads with info on the card like this one

[http://ubuntuforums.org/showthread.php?t=458482&highlight=psc805](http://ubuntuforums.org/showthread.php?t=458482&highlight=psc805)

and this one

[http://ubuntuforums.org/showthread.php?t=274405&highlight=psc805](http://ubuntuforums.org/showthread.php?t=274405&highlight=psc805)

I am trying to figure out the best way to get the card to function any other tips would be appreciated

---

