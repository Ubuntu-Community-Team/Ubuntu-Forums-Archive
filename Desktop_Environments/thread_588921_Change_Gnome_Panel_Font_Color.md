---
title: "Change Gnome Panel Font Color"
date: 2007-10-23
forum: Desktop Environments
---

### Post by Jay_Davis on 2007-10-23
When I use a transparent panel with a dark background the text becomes unreadable because it is also dark. I don't know where the option to change this is located. I would like to make it white; what's the easiest way to do that?

Using 7.10

Thanks,
Jay

---

### Post by WiFi Ed on 2007-10-23
[http://brentroos.com/2006/07/07/change-gnome-panel-text-color/]("http://brentroos.com/2006/07/07/change-gnome-panel-text-color/")

---

### Post by Jay_Davis on 2007-10-23
> **WiFi Ed said:**
> [http://brentroos.com/2006/07/07/change-gnome-panel-text-color/]("http://brentroos.com/2006/07/07/change-gnome-panel-text-color/")

[edit]

Rebooting, again (took 6 minutes, why?) made it work. Strange, I have no idea why it did this.

---

### Post by WiFi Ed on 2007-10-24
Glad it worked, but I don't understand the 6 minute reboot either. The "killall gnome-panel" command works for me, takes less than 1 second. Oh well, all's well that ends well...

---

### Post by Jay_Davis on 2007-10-24
> **WiFi Ed said:**
> Glad it worked, but I don't understand the 6 minute reboot either. The "killall gnome-panel" command works for me, takes less than 1 second. Oh well, all's well that ends well...
Yeah, got the panel thing figured out, but that reboot time means Windows is going to have to go back on there for now. The only other thing I did was install the wireless and the new ATI drivers. It's an aspire 5100 (Xpress 200m graphics) and uses a broadcom card. I know there's been problems with those drivers before. I had performance problems with the new graphics drivers too, 2d wasn't working well as people are saying. Disappointing, but with this hardware it doesn't look like there's anything anyone can do about it.

---

### Post by berlinbullet on 2007-10-24
I ran into the reboot taking awhile too (I am using ATI drivers as well). The fix I found on the forums here was actually to change "splash" to "nosplash" in the menu.lst for grub. This made my boot time go back to the normal under a minute. If you need more help with it, the thread is around here somewhere :guitar:

---

### Post by Jay_Davis on 2007-10-24
Thanks for the suggestion, but I had already disabled it so that couldn't have been the problem. I'm certain it's just buggy drivers and my hardware not being supported. ATI+Broadcom, pretty much the worst laptop you could get if you want linux compatibility.

---

