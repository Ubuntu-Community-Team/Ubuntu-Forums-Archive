---
title: "[SOLVED] Help please: Removing the new ATI driver (downgrade)"
date: 2007-11-03
forum: Desktop Environments
---

### Post by simoncullen on 2007-11-03
Edit: problem solved.  I needed to run the uninstall script in cd /usr/share/ati



Ubuntu gurus,


I couldn't resist trying the new ATI driver any longer. I now thoroughly regret installing it.  The driver was slow, video play back was choppy, firefox nearly unusabe. I've tried to uninstall it and go back to the previous driver in the repos, but with no luck.  I am on 7.04 Feisty with an ATI Mobility 1700. 

I've uninstalled all of the packages the ATI installer created, removed the restricted drivers (sudo apt-get remove linux-restricted-modules-$(uname -r)) and reinstalled the xorg driver (sudo apt-get install xorg-driver-fglrx) and reinstalled the restricted drivers.

Now when GDM loads, at the log in screen I am presented with a garbled display (predominantly horizontal/diagonal lines).  No matter how I try I can't get it back to the old set up.

Any help will be appreciated.  I've read through the forums extensively and haven't found any useful advice on this topic.  I guess others will be looking for help too.

Cheers,

Simon

---

### Post by zxscooby on 2007-12-26
where do you get the old drivers?

---

### Post by simoncullen on 2007-12-26
> **zxscooby said:**
> where do you get the old drivers?

The driver is still in the repos, I think. Try rolling back to the previous linux-restricted-modules

---

### Post by cdinz on 2007-12-26
can any one say which media player works excellent in ubunt other than vlc and movie player:guitar:

---

