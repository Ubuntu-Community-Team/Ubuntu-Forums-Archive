---
title: "Gusty on a Dell Dimension 8400"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by Austin17 on 2007-10-23
Hi all, just a quick question. Does anyone out here who has a Dell Dimension 8400 have any problems with Ubuntu 7.10? Thanks.

---

### Post by jpittack on 2007-10-24
If you post some hardware on the dell that you will be using, this would be very helpful, as you would broaden how many people can respond.

---

### Post by Austin17 on 2007-10-24
It's P4 3.2 GHz, 2 GB DDR2 RAM,  GeForce 6800, Sound Blaster Audigy 2. I guess the main thing would be the GeForce 6800, because if there is trouble with Gusty, the video card would be the thing to cause it.

---

### Post by opengovtv on 2007-10-24
i have the same system as yours less the sound card.  no problems loading gutsy on it. no video problems. i would be more worried about your sound card as they always seem to be the most troublesome.

---

### Post by Austin17 on 2007-10-24
> **opengovtv said:**
> i have the same system as yours less the sound card.  no problems loading gutsy on it. no video problems. i would be more worried about your sound card as they always seem to be the most troublesome.

Thanks. :)

---

### Post by tim heeter on 2007-10-24
from what i have read all the audigy families work extremely well in gutsy except for the X-Fi family. Which isn't ubuntu's fault what so ever. :)

---

### Post by Austin17 on 2007-10-24
> **tim heeter said:**
> from what i have read all the audigy families work extremely well in gutsy except for the X-Fi family. Which isn't ubuntu's fault what so ever. :)

Neat, thanks for the info. I will feel more comfortable upgrading to Gusty after this. :)

---

### Post by Austin17 on 2007-10-25
Sorry for the double post, but I upgraded my main computer to gusty this morning. Before doing so I deleted Automatix and disabled my effects. The install asked me if I wanted to replace a configuration file, but thats it. Gusty is running great! Thanks for all the help guys!

---

### Post by mmooney on 2008-03-03
I have a Dimension 8400 with  a P4 3.2, 1G of memory, nVidia graphics card, 160 Gig hard drive. When I try to run from the live cd the computer freezes up. It starts to load but gets to the Ubuntu splash screen and the screen starts drawing  all over the screen then locks up. I've had this on an older computer with no problems. Can anybody help?

---

### Post by mmooney on 2008-03-09
I never could run the live disk at all. It would load and then the screen would start breaking up. If I let it go I could hear Ubuntu start in the background. I tried using a different monitor to see if that was the problem.( I now have an lcd monitor instead of a crt). Same problem, so I knew it was the graphics card. I ended up installing it in text mode but, it still wasn't reading my card correctly. At this point I'm in console mode. You need to reconfigure the xorg.conf file. Do this by typing:
"sudo dpkg-reconfigure xserver-xorg" you will have to answer a lot of questions but it works. I hope this helps you.

---

