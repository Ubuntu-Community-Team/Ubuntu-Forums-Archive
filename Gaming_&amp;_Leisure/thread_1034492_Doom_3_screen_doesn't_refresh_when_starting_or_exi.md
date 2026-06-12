---
title: "Doom 3: screen doesn't refresh when starting or exiting"
date: 2009-01-08
forum: Gaming &amp; Leisure
---

### Post by x1a4 on 2009-01-08
Hi,
I dusted off my old games and installed some but have a problem with Doom 3.  When I start it, and again when I quit, the screen doesn't refresh.  It's black.  I have to switch to another display than back again.  

I'm using an MSI video card with a nVidia GeForce 5200 GPU with restricted drivers from the Hardy repos.  

Any ideas?

Thank you.

---

### Post by Dark Aspect on 2009-01-10
> **x1a4 said:**
> Hi,
I dusted off my old games and installed some but have a problem with Doom 3.  When I start it, and again when I quit, the screen doesn't refresh.  It's black.  I have to switch to another display than back again.  

I'm using an MSI video card with a nVidia GeForce 5200 GPU with restricted drivers from the Hardy repos.  

Any ideas?

Thank you.

Are you running compiz? What is your refresh rate in Ubuntu?

---

### Post by x1a4 on 2009-01-11
I'm running an Xfce session without a desktop and Openbox instead of xfwm4.  I tend to have xcompmgr running but I told the Doom 3 start-up script to kill it; or sometimes I do it myself.  Default refresh rate is 72Hz.

---

### Post by Dark Aspect on 2009-01-11
> **x1a4 said:**
> I'm running an Xfce session without a desktop and Openbox instead of xfwm4.  I tend to have xcompmgr running but I told the Doom 3 start-up script to kill it; or sometimes I do it myself.  Default refresh rate is 72Hz.

Could you try setting the refresh rate to 60Hz instead of 72Hz?

---

### Post by x1a4 on 2010-08-12
Changing Doom resolution to the same as system resolution solved it.

---

