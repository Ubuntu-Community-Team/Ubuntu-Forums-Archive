---
title: "Funny menu font in OpenOffice"
date: 2006-07-24
forum: Desktop Environments
---

### Post by mjpatey on 2006-07-24
Hi, Group-

I'm not sure if this is because I just recently reconfigured my xorg.conf file, but here's the problem...

The font used in Open Office for menu headings and menu items themselves is displaying really badly on my system.  I honestly don't remember if it looked like this before I reconfigured xorg.conf or not, but during the reconfiguration, I only accepted the defaults, so I don't think that could have affected anything.

Have a look at my screenshot... there's a clear difference between the menu headings in Firefox and in OpenOffice, where they just look uneven.  Some letters are normal, others are almost bold or smeary.

Any idea how to fix this?  The "Fonts" section of System Preferences was where I looked first, but all was well there.

Thanks for any help you may have!

-Mark

---

### Post by mjpatey on 2006-07-24
Got it!

I just realized that I'd set the "Application Font" in System Preferences to "Tahoma", and it seems OOo doen't like Tahoma.  I re-set it to Arial, and OOo looks just fine.

Here's a screenie!  Thanks for reading... I hope this helps somebody!

If you're even newer than I am to this whole Linux thing and were wondering how to even get fonts like Arial and Tahoma, do a search for "msttcorefonts", then search these forums for "Tahoma" (since Tahoma is not included in the msttcorefonts package).  I think it's only OK to use these fonts if you own a legal copy of Windows.

-Mark

---

