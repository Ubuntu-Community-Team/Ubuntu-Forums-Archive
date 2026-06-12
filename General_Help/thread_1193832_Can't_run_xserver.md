---
title: "Can't run xserver"
date: 2009-06-22
forum: General Help
---

### Post by entropy1 on 2009-06-22
When I login to Ubuntu, instead of getting my desktop, I get the message "There already appears to be an Xserver running on display :n"  [where n=0,1,2,..]

I am then given a choice to try again or to try another display.
Neither one works, and I just come back to the login screen
or to the error message.  Has anyone seen or solved this problem?

---

### Post by T.J. on 2009-06-22
Have you tried restarting the machine?  

Usually when you get that message, X is already running, obviously.  If you know how, you can restart the X server without rebooting, but that may be too complex without knowing your experience.

If that doesn't fix it, you may have a corrupted desktop file, or need to adjust your video driver, but let's not go there if we don't have to.  One thing at a time.

---

### Post by Tews on 2009-06-22
As a ***LAST*** resort, boot into the recovery mode and choose  the last option, fix xserve.  Know that you will have  to re-install any proprietary drivers when you do this ....

---

### Post by entropy1 on 2009-06-22
> **Tews said:**
> As a ***LAST*** resort, boot into the recovery mode and choose  the last option, fix xserve.  Know that you will have  to re-install any proprietary drivers when you do this ....
Tews,

Thank you for the suggestion.  Unfortunately, I've tried it twice and it did not work.

---

