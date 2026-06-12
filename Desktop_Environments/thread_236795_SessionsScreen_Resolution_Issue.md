---
title: "Sessions/Screen Resolution Issue"
date: 2006-08-15
forum: Desktop Environments
---

### Post by astromac on 2006-08-15
I came in this morning to find my ubuntu desktop locked up hard so I powered down and restarted.  It seemed to restart in some "safe mode" or something because it came up in a 1024x768 resolution on my 20" monitor.  I went to preferences->screen resolution and tried to change it but 1024x768 or less were the only options.  I tried logging out, cold restarting, changing sessions, etc. to no avail.  I looked at /etc/X11/xorg.conf and it looks okay with all resolutions from 1600x1200 and less.

How do I get out of this "safe mode"?  It's very annoying.

Thanks for your help.

---

### Post by orb9220 on 2006-08-15
Back up your xorg.conf file then run in term

sudo dpkg-reconfigure xserver-xorg

---

### Post by astromac on 2006-08-15
You rock.  Thanks!

---

### Post by orb9220 on 2006-08-15
Don't thank me Learned it here in the forums. Thank them thier the greatest!

---

