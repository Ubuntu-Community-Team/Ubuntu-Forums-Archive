---
title: "GDM auto-login after set time does not bring up desktop"
date: 2014-08-31
forum: Desktop Environments
---

### Post by wmdvanzyl on 2014-08-31
Hi All.

I am running Ubuntu server 14.04 LTS and GDM which i installed afterward. I can log in using my created user just fine and i can get to the desktop, but i would like to have one user auto-login if no-one logs in for a given amount of time.

This i tried to achieve by changing /etc/gdm/custom.conf and removing the # from the lines that deal with timed login. After rebooting the server i can see the line (timer) running across the username of the selected user and it seems to log in, but then never brings up the desktop. 

Any suggestions?

---

