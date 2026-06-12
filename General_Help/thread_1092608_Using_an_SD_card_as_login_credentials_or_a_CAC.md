---
title: "Using an SD card as login credentials or a CAC?"
date: 2009-03-10
forum: General Help
---

### Post by Unikraken on 2009-03-10
I'm not sure if I'm posting this in the right forum, if not I'm sorry.

I can faintly remember once seeing an article about how someone could use an SD memory card like a CAC(common access card) so that they would insert the SD and the computer would log in and when you pulled it out the computer would lock or shut down, not sure about the last part. So the card would basically carry login credentials? Does anyone here know anything about this? Because I think that would be a really nifty hack.

I tried searching the tubes and found nothing so I'm coming to biggest bunch of experts I can find which is here on this forum.

---

### Post by heindsight on 2009-03-12
There are PAM modules you can use to achieve something like this. I haven't tried it out yet, but it looks like libpam_usb which is available in the Universe repository (at least it is in Hardy), provides functionality similar to what you want.

Have a look at:
[http://pamusb.org/](http://pamusb.org/)

---

