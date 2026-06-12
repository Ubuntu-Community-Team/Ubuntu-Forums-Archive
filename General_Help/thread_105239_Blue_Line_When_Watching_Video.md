---
title: "Blue Line When Watching Video"
date: 2005-12-18
forum: General Help
---

### Post by Noah0504 on 2005-12-18
After I install totem-xine and all of the neccesary packages to watch video and DVDs, I see an ugly blue line to the left of the video I'm watching.  Sometimes, the line is always there, even when I'm just listening to a song in Totem.  Other media players such as VLC do the same thing.

Can anyone help me remove this ugly distraction?

---

### Post by 23meg on 2005-12-18
Did you try changing your video driver in your xorg.conf file to "vesa" instead of "trident"? 

(I know you have a trident from your former post but you should post your video hardware details when asking display related questions.)

---

### Post by janga on 2006-08-06
Hi there, this is a bit late for an aswer, but maybe some other people will benefit from my solution searching for trident + blue line..

solution:

in xorg.conf, section device, add:

```
    Option        "XvHsync" "-3"
``` 
depends on how fat the blue line is.
this is only for the "trident" driver.

---

### Post by mojoman on 2006-08-07
> **janga said:**
> Hi there, this is a bit late for an aswer, but maybe some other people will benefit from my solution searching for trident + blue line..

solution:

in xorg.conf, section device, add:

```
    Option        "XvHsync" "-3"
``` 
depends on how fat the blue line is.
this is only for the "trident" driver.

Janga, could I ask if you got the trident driver to work properly? I've had the blue line and will try your fix on that one but I also have problems with the playback being jerky and getting out of synch.

Best regards
/mojoman

---

