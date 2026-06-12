---
title: "lop sided logon page. Really weird."
date: 2009-01-23
forum: General Help
---

### Post by ceaser_salad on 2009-01-23
Hello,

I just installed xubuntu(hardy) on my desktop. I had ubuntu(hardy) on before, but I want to give it away, and thought while wiping all my stuff off it, why not try something different.
Anyway, I've got a nvidia geforce 2..., so while doing the usual envy thing, the resolution dropped to 640x350! I couldn't see the whole of the nvidia settings page, so couldn't change that. After straining my eyes for an hour,I managed to get everything sorted. 
BUT, now I've got this weird log on screen?  

Any advice is appreciated. Thanks.

---

### Post by ceaser_salad on 2009-01-25
bump

---

### Post by JKyleOKC on 2009-01-25
Try going into your xorg.conf file (/etc/X11/xorg.conf) and changing its DefaultDepth value from the current value of 24 or 32 doen to a value of 15 or even 8. This cured a similar problem for me when all else failed.

If you can't get an editor to work properly in the low-resolution screen, go to an alternate terminal via ctrl-alt-2, log in at the command prompt, and use vi (sudo vi /etc/X11/xorg.conf) to make the change, then exit back to your GUI screen via ctrl-alt-7 and hit ctrl-alt-backspace to restart the X server with the new DefaultDepth value.

---

### Post by ceaser_salad on 2009-01-27
I followed those tips, but there wasn't a change. 
I could live with it, but I think it might irk my PC's next owner :-)

---

