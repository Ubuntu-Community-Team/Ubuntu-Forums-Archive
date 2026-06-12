---
title: "Text in menu disapper in apps after compiz install."
date: 2008-12-25
forum: General Help
---

### Post by jkbpower on 2008-12-25
Hi,
Running Ubuntu 8.10 and it's working great.
After installing Compiz fusion which worked fine all text disappered in apps.
Not in gnome menues just in apps like openoffice,K3b etc.Not all apps.

Anyone know how to fix this.

/Jimmy

---

### Post by ronniet on 2008-12-25
I had the same problem with OOo and Scribus. It seems to be due to the video drivers.

I was using an old GeForce4MX, now using a GeForce9400GT, and the menu items are all fine.

The only quick fix (which I know works for OOo) is to go to System > Appearance, then in the Fonts tab, pick sub-pixel smoothing. That should fix OOo, not sure about the others though...

**Good luck!**

---

### Post by jkbpower on 2008-12-25
Found it and fixed it :-)

The problem was the nvidia driver.
Found this in another thread about almost same problem.
------------------------------------------------------------------------
For me (Geforce4 MX440 card with 96beta driver on Intrepid) I changed my xorg.conf file to

Option "RenderAccel" "False"
or
Option "RenderAccel" "0"

in the Section "Device".
--------------------------------------------------------------------------
This worked for me and I have MX420 card.
/Jimmy

---

