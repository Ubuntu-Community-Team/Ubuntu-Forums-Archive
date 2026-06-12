---
title: "Problem with disappearing gnome Applications Menu"
date: 2006-03-28
forum: Desktop Environments
---

### Post by thaMANSTA on 2006-03-28
Having a problem with my Applications Menu:  When I click on it, the menu blinks on for like a tenth of a second, then disappears.  Technically, it's not disappearing, it's actually turning into an "empty" menu, which is like 4px x 4 px.    If I click on the menu again, if comes up again for like a tenth of a second, and is again emptied, leaving the little square empty menu.

The last thing I changed before I restarted was doing this downgrade, to fix a problem I was having with the runaway gam_server problem:
[http://astokes.org/?q=node/62](http://astokes.org/?q=node/62)

BTW, only the Applications menu is affected, the Places and System menu are working fine.  Also, I created a new test user, and the test user has the same menu glitch, so it is not something in my home directory.

Thanks,
-thaMANSTA

---

### Post by peacerist on 2006-06-14
Hi,

I have the same problem. Problem occured when I have restarted my machine after 34 days uptime. In this time span my computer went through many package updates. I dont know which one caused that. I recently changed my nvidia driver which I have downloaded from the nvidia website. 

Any one got a solution?

---

### Post by peacerist on 2006-06-17
Simple solution:
sudo apt-get install menu
update-menus

see [http://www.ubuntuforums.org/showthread.php?t=94353&page=4](http://www.ubuntuforums.org/showthread.php?t=94353&page=4)

and

[http://bugzilla.ubuntu.com/show_bug.cgi?id=20216](http://bugzilla.ubuntu.com/show_bug.cgi?id=20216)

---

