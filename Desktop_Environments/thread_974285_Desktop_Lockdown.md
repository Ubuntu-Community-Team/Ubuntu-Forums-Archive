---
title: "Desktop Lockdown"
date: 2008-11-07
forum: Desktop Environments
---

### Post by Fitz_the_gap on 2008-11-07
Hi, I need to prevent users (students) from messing around with the desktop perhaps making it read only. I also need to remove objects from the top panels. Any help is most appreciated. 
cheers 
Fitz

---

### Post by timcredible on 2008-11-07
well, removing objects from the top panel is just right-click on it and 'remove'.  as for making a desktop read only, i guess you could do > chmod 444 .g*after you've got it setup the way you want.
however, if you're in a class environment, you may want to make your life easy and setup the student's computers as xdm clients only (with a pxes cd) and then have them remotely access a single ubuntu server via xdm.  the reason for that is then you only have to maintain/fix/modify 1 machine.  click on the link in my sig for more info on that.

---

### Post by Fitz_the_gap on 2008-11-18
Apologies for a late response. I'll look into it.
Thanks

---

