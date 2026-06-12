---
title: "when doing a sudo dkpg-reconfigure xserver-xorg should video memory be defined ?"
date: 2007-08-01
forum: Desktop Environments
---

### Post by kraymore on 2007-08-01
when doing a sudo dkpg-reconfigure xserver-xorg should video memory be defined ?  

thanks

---

### Post by az on 2007-08-01
> **kraymore said:**
> when doing a sudo dkpg-reconfigure xserver-xorg should video memory be defined ?  

thanks

It doesn't need to be.  If you put in a wrong amount (too large) you may end up with a funny looking mouse pointer.

On some recent onboard video cards, that memory amount is dynamic.  So just leave it blank.

---

