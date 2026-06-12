---
title: "unwanted logout after period of inactivity"
date: 2007-01-18
forum: Desktop Environments
---

### Post by mvaniersel on 2007-01-18
Recently, whenever I get back to my system after a period of inactivity (say, an hour), it turns out I was logged out from my current session and I'm back at the login screen. All my open programs are gone and any unsaved documents are lost.

I've looked in Preferences->Sessions and Preferences->Power Management, but there seems to be no setting that controls this behaviour. I have the screensaver set to kick in after 10 minutes (and confirmed that it does), and set it to put the display on sleep after 40 minutes.

How can I stop this very annoying behaviour?

This is on Ubuntu Edgy Eft.

---

### Post by jd65pl on 2007-01-18
Do you have a graphical screen saver in use? If so just select blank screen. I had the same problem and this solved it. You could also check /var/logs to see if there are any messages around your fault time.

---

### Post by mvaniersel on 2007-01-18
That's right, disabling the screensaver altogether seems to solve the problem. So in fact the screensaver crashed the system and caused a reset of X.

Could this be a gfx driver issue? This is with the ATI driver, on a radeon X600 PCIE. Which driver / card do you have gd65pl?

---

### Post by jd65pl on 2007-01-18
I have onboard graphics with no hardware rendering. I don't think its specific to a graphics card.

---

