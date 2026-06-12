---
title: "Gutsy, fglrx, Dual Head, Compiz, and xserver-xgl"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by ComPro on 2007-11-23
I have a dual monitor setup with the restricted fglrx driver installed. I ran through aticonfig and I have it set up with an extended desktop, not really big desktop, as I like to be able to maximize windows to single monitors, not the whole display.

I'm trying to get Compiz working, so in doing so, I installed xserver-xgl. It enabled me to use Compiz, which looks fantastic, but ended up turning my extended desktop into one giant display, with programs dead center between the two screens and maximizing across both. If I remove xserver-xgl, it works perfectly fine again, but without the Compiz effects.

I cannot upgrade to the ATI proprietary 8.42 driver, as it causes my display to get all multicolored and garbled, and it locks up the machine. I must stay on 8.37. Is there any way to get xserver-xgl working, or some alternative, as to where I can keep my extended desktop mode?

Thanks.

---

### Post by ComPro on 2007-11-24
Nevermind, I figured it out. It turns out I had the solution in front of me the whole time. I just needed to chmod my /usr/bin/startxgl.sh file to be executable - a simple mistake for a Linux newbie.

Hopefully others will be able to learn from my mistake. :)

---

### Post by ComPro on 2007-11-24
OK, Interesting issue...

If I restart my machine or log out and back in, or something along that nature, my dual head setup will be incorrect again. I then have to fall back to a fullscreen terminal, stop gdm, manually run /usr/bin/startxgl.sh, and then restart gdm. That fixes it until the next time X starts.

Any thoughts/ideas?

---

### Post by evilfred on 2007-12-08
Same problem as above. 

I'm running fglrx drivers as Big Desktop (one big screen). I believe you get better 3D acceleration doing it like this or something, and it's much simpler than Dual Head. But would really like to sort out the maximise issue.

I've read elsewhere that you need to make sure that XGL is loading with Xinerama support, but I don't know how to do this.

---

