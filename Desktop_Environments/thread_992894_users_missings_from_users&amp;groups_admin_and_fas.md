---
title: "users missings from users&amp;groups admin and fast-user-switch-applet"
date: 2008-11-25
forum: Desktop Environments
---

### Post by damiannz on 2008-11-25
hey,

i'm dualbooting Intrepid with OSX on a MacBook 2,1. it's great. well done everyone involved. 

now, in order to avoid permissions issues accessing my HFS+ partition under Ubuntu, i've changed my uid from 1000 to 501 (to match OSX). this works great for HFS+ access, but now my username no longer appears on the Users and Groups admin panel unless i turn on the show-all option in gconf-editor.

i also added another user, changed its uid from 1001 to 502 (again to match OSX), but this new user doesn't appear on the fast-user-switch-applet menu.

is there a fix for either of these problems? my hunch is that all uid's below 1000 are being ignored by both applets. if i'm correct, is there any way to change this settings?

thanks for any assistance,
d

---

