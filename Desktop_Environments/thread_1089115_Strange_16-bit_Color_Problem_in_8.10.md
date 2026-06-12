---
title: "Strange 16-bit Color Problem in 8.10"
date: 2009-03-06
forum: Desktop Environments
---

### Post by TheOriginalPol on 2009-03-06
I recently upgraded to 8.10 Intrepid on my Compaq F577US laptop, and the upgrade went seamlessly, without any errors (except for my own carelessness, but that's another story.)

However, there is one problem that I didn't notice until now (due to a recent change in desktop wallpapers).  When I login, the color depth of my environment is clearly 16-bit.  I can see the gross little waves on my once nicely gradated wallpaper that indicate the lack of system color choices.  I have checked /etc/X11/xorg.conf again and again, but it definitely is configured for 24-bit.  

The strange part is that the main login screen still displays a gorgeous brown gradient, in 24-bit color and no waves at all.  I was always under the impression that the login screen and then whatever session you log into was the same X session, no?

The other strange part is that if I suspend my computer and then wake it up again, it is back to 24-bit mode.  Even though nothing has changed, I haven't touched a key except to type my password.


Anybody got any ideas?
I'm packing a nvidia GeForce Go 6150 w/ latest accelerated driver.  I used Compiz-Fusion and all that jazz.

Thanks in advance.

---

