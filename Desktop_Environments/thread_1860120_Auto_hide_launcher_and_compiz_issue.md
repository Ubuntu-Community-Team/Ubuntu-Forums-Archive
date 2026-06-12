---
title: "Auto hide launcher and compiz issue"
date: 2011-10-14
forum: Desktop Environments
---

### Post by mrbox24 on 2011-10-14
This is my setup, I installed compiz-settings-manager and enabled auto hide launcher and wobbly windows I then installed ubuntu-tweak-0 via ppa:tualatrix/next to enable show windows when i put cursor in bottom right corner.

It worked for awhile then broke as it did in the betas of oneiric. now launcher doesn't show when cursor is put to left of screen and windows are not displayed when cursor is put to bottom right of screen.

How can I fix this? Call me picky but I was spoiled with compiz on Fuduntu and this is how I want my windows displayed and unity launcher to show. What drives me nuts is it will work great for awhile then stop. Please help thanx :)

---

### Post by mrbox24 on 2011-10-14
> **mrbox24 said:**
> This is my setup, I installed compiz-settings-manager and enabled auto hide launcher and wobbly windows I then installed ubuntu-tweak-0 via ppa:tualatrix/next to enable show windows when i put cursor in bottom right corner.

It worked for awhile then broke as it did in the betas of oneiric. now launcher doesn't show when cursor is put to left of screen and windows are not displayed when cursor is put to bottom right of screen.

How can I fix this? Call me picky but I was spoiled with compiz on Fuduntu and this is how I want my windows displayed and unity launcher to show. What drives me nuts is it will work great for awhile then stop. Please help thanx :)

EDIT Resetting auto hide launcher and display windows options fixes it for that session until reboot/logout of course i dont want to reset these each time i boot.....

---

### Post by mrbox24 on 2011-10-14
I fixed it :) discovered that compiz --replace brought my settings back so i put that in a shell script and added it to startup applications.

I suppose i may have been inadvertently switching my window manager from unity to compiz?

is there a place i can put my script to run at startup without using the startup applications?

Amazing how we can answer our own questions sometimes :D

---

