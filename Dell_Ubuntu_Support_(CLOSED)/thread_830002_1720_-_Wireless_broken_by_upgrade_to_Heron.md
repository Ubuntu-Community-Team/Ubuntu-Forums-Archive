---
title: "1720 - Wireless broken by upgrade to Heron"
date: 2008-06-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vuroth on 2008-06-15
Been running ubuntu for a while, but I finally got around to getting the latest upgrade (8.04?)  Suddenly, my wireless is not working.

Before (GG?), I would have to manually select my network, then open a terminal and sudo dhclient eth1 every time I booted up (maybe this is not standard and I just didn't know better).  Now, manually selecting my wireless does not work, even though the settings are all still there.

For wireless, I seem to have the Broadcom 43 drivers, but ubuntu tells me that I need the firmware, which of course, I can't download.

(Thank goodness I'm dual booting, I guess.)

Was there some kind of an issue associated with the Heron release that I missed?  Or is this problem unique to me?

V

---

### Post by cacycleworks on 2008-06-15
Unfortunately, you're not alone; the upgrade was misery for me and broke wired networking. I ended up performing a fresh install of 8.04, which went amazingly well. Check my posts for more info about my story. :-) 

I've found if you have a separate partition for /home and leave it untouched, you can perform a fresh install and transition to new version quickly. The only tweaks normally made are to get the packages reinstalled as you need them.

Best,
Chris

---

### Post by vuroth on 2008-06-22
Found my answer by following this procedure:  [http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

---

