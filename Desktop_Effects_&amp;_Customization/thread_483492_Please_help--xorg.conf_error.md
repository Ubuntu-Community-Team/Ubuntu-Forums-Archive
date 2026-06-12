---
title: "Please help--xorg.conf error"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by bazooze28 on 2007-06-24
hey i installed compiz fusion and it was working except sometimes the window borders would dissapear.  someone here suggested that i change the color depth to 16 in xorg.conf.  so i did that and i restarted the computer.  and now its totally messed up. there are no borders, i cant start compiz anymore, and it crashes frequently.  is there a way i can restore my old xorg.conf so that everything will work again.

thanks in advance and i apologize if this is in the wrong forum

---

### Post by Sarisar on 2007-06-25
The number of times I've killed my XORG.CONF file...

Always keep a backup before you do anything.  Now quite a few things do keep backups so go to the /etc/X11 directory and see if there is a nice backup from about the right time.  If that doesn't work you might want to run ENVY to get the correct drivers and overwrite the xorg.conf and restart from there.

There might be an easier way but not sure.  This way should work.

---

