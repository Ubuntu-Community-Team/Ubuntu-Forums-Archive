---
title: "SLI hard crashes my system"
date: 2006-08-09
forum: Desktop Environments
---

### Post by touser on 2006-08-09
Hello everyone, i am running 6.06 with the latest nvidia drivers available in the repos. Everything is working great under one card, and glxgears gets around 14,000 with 1 7800gtx, but when i add the option to turn sli on into my xorg.conf and restart the X server it completely hard crashes the whole system and the only solution is to reset the computer. If anyone has any idea how to fix this i would greatly appreciate the help!

---

### Post by touser on 2006-08-10
sorry to bump this but i still havent found a solution yet :(

---

### Post by hanover.fiste on 2006-08-11
Are you running a multiprocessor system with an AMD processor and the ubuntu K7 kernel. I have that problem, and one other person has reported it. If you use the 386 kernel, the problem doesn't occur and SLI works fine. Obviously, that's not a long-term solution.

---

### Post by touser on 2006-08-12
Thanks for the reply hanover.fiste. I am running an amd X2 and the k7 kernel, i tried the i686 kernel and it still crashed. I guess we'll just have to wait for a patch?

---

### Post by hanover.fiste on 2006-08-25
I had this, but after upgrading to the 8774 driver, my system seems to be working.

---

