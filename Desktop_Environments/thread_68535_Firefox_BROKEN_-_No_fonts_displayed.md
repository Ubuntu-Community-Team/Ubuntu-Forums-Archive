---
title: "Firefox BROKEN - No fonts displayed"
date: 2005-09-23
forum: Desktop Environments
---

### Post by iminj on 2005-09-23
When I open mozilla-firefox (1.0.6-0Ubuntu0.2) I see the ubuntu screen graphics (.gif?), but the screen text is either blank or dashes ( - ). The menu is the same, no text .. just a lot of dashes.

I tried uninstall / reinstall - but problem still exists. I picked up ver. 1.0.7 (just out in Universe repo's I think,) but same font problem

I am using all 'hoary' packages with **1 exception.** I use the 'warty' version of pcmcia-cs, and I have this version pinned in synaptic. (*Unfortunately, due to a known bug, the hoary version of pcmcia-cs won't allow my nic to connect to a network.*) 

I notice that when I re-installed mozilla-firefox, synaptic is holding back something called "x-window-system-core". Is this related to the pcmcia-cs pinning, or indicative of _something else_ that might be contributing to the problem?

I also played around with dpkg-reconfigure locales, thinking that I might have a locales issue that borks up the fonts. At the moment, I have 2 locales :

en_US.UTF-8 UTF-8
en_US.IS0-8859-1

I disabled the ISO-8859 locale - and it made no difference re: the font problem - so I re-enabled it.

Anyone have thoughts on a solution ?

Thanks
-iminj

---

### Post by aysiu on 2005-09-23
I would try it with a fresh profile.
In Firefox export your bookmarks to a safe place.
```
cp /home/username/.mozilla /home/username/.mozilla_backup
rm /home/username/.mozilla
``` Then reopen Firefox. Same problem?

---

### Post by iminj on 2005-09-23
Thanks for the reply !

Unfortunately, rm of my profile didn't work.

After removing the profile, and restarting firefox, the profile selection box opened ... with NO VISIBLE FONTS in it.

Is it possible that xorg is broken in some way ?

---

### Post by Velox Letum on 2005-09-24
Do fonts work in Epiphany/Opera etc.?

---

### Post by iminj on 2005-09-24
Velox Letum:

Thanks for the reply !

I never did test any other browser, although that would have been a good idea...

I did a drive format and re-install, and so far, I have no font problems.

-iminj

---

