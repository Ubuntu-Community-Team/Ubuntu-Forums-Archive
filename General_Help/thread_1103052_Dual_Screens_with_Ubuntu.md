---
title: "Dual Screens with Ubuntu"
date: 2009-03-22
forum: General Help
---

### Post by sa125 on 2009-03-22
Until today I had a single philips 19" screen and everything was dandy. I added an identical screen this morning, and the resolution shot down to 1024x768 on both. I previously had it at 1280x1024, but now this option is no longer there when I try to configure both screens. One is identified as **Philips 19"** while the other (same) is **unknown**. How can I fix this? Is there a way to add a resolution to the selection dialog in resolution settings?

thanks!

---

### Post by men28 on 2009-03-22
What a video card do you have? ATI or nVidia?

---

### Post by alfplayer on 2009-03-22
Maybe you can set new modes for your new monitor with the command xrandr.

---

### Post by sa125 on 2009-03-23
> **men28 said:**
> What a video card do you have? ATI or nVidia?

running lspci in shell gives out this:
```

$ lspci
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:02.1 Display Controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
```

Also, how do I add a graphic resolution choice with xrandr?

thanks

---

### Post by sa125 on 2009-03-23
> **sa125 said:**
> running lspci in shell gives out this:
```

$ lspci
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:02.1 Display Controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
```

Also, how do I add a graphic resolution choice with xrandr?

thanks

OK, I added a new resolution with xrandr, and one of the screens accepts it and displays fine. I tried picking the same resolution for the other screen (which is identical to the first), but got an error saying "Your settings cannot be applied because the  virtual resolution is not big enough to contain your screens" - what's going on?

---

### Post by men28 on 2009-03-24
It looks like very simple controller integrated to motherboard.
This is not nVidia nor ATI.
I am not sure this controller can support two displays simultaneously.

---

### Post by alfplayer on 2009-03-24
I had a similar problem: I couldn't get the maximal resolution in my second monitor.
I found out that the resolution specified in the Virtual line (width and height) in /etc/X11/xorg.conf did not add up to the resolution that I was trying to set: the height was ok but the width was not enough (I think it was 2048 and I set it to 1024+1280=2304).
Finally I changed my second monitor's resolution to the maximum value.
This is how I solved it.

---

