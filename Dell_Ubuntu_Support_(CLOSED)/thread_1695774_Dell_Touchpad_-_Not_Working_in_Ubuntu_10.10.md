---
title: "Dell Touchpad - Not Working in Ubuntu 10.10"
date: 2011-02-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by A4orce84 on 2011-02-26
Hello Everyone,

I installed Ubuntu 10.10 on my Dell Latitude E6410 laptop, and it seems that my touchpad is not working correctly. 

Has anyone got the scrolling (vertically and horizontally) to work correctly?

Thanks!

--Asif

---

### Post by NikoC on 2011-03-18
Same problem on my dell E6510 with ubuntu 10.10 64-bit and kernel 2.6.35-28-generic.

No luck in finding a workaround so far...

---

### Post by liferules on 2011-03-18
> **A4orce84 said:**
> Hello Everyone,

I installed Ubuntu 10.10 on my Dell Latitude E6410 laptop, and it seems that my touchpad is not working correctly. 

Has anyone got the scrolling (vertically and horizontally) to work correctly? --Asif

Works fine on my Dell Vostro 1700 ...

---

### Post by NikoC on 2011-03-23
You might want to follow up [this]("http://ubuntuforums.org/showthread.php?t=1637372") thread.

---

### Post by ugm6hr on 2011-03-23
Might be worth specifying exactly what the problem is.
Sometimes, the tap-to-click and scrolling can be adjusted, if the problem is related to sensitivity / width of scrolling areas.

---

### Post by NikoC on 2011-03-28
> **ugm6hr said:**
> Might be worth specifying exactly what the problem is.
Sometimes, the tap-to-click and scrolling can be adjusted, if the problem is related to sensitivity / width of scrolling areas.

It's definitely a kernel bug: see post above (link to thread) and a patch has been suggested, but I don' t really  know how to patch a kernel... so I guess I'll wait until a permanent fix is released.

---

### Post by jasonr80 on 2011-04-01
I have the same problem with my E6410 on Ubuntu 10.10 64bit.  The touchpad works, but scrolling feature does not work.  System > Preferences > Mouse does not display a touchpad tab.

I found this blog post that says there is a patch but it brings about other issue with screen brightness.  I'll pass and hope to find a mainstream fix soon.
[http://munjunga.blogspot.com/2011/02/ubuntu-1010-touchpad-scrolling-error-on.html](http://munjunga.blogspot.com/2011/02/ubuntu-1010-touchpad-scrolling-error-on.html)

The other issue I'm having with the e6410 is the issue where it can't resume after being suspended while running on battery power. I read that it might be a problem with the BIOS and that disabling Speed Step will fix the issue.  Sadly it did not fix it for me.

---

### Post by NikoC on 2011-04-01
Same here: I also found the patch, but I'm going to wait until a mainstream fix is released.

I'm not having the suspend/resume problems on a E6510 though.

---

