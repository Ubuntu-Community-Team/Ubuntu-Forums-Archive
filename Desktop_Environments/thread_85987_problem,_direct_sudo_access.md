---
title: "problem, direct sudo access"
date: 2005-11-04
forum: Desktop Environments
---

### Post by sebast on 2005-11-04
Hi,

I have a problem burning audio CDs on CD-R with serpentine (but that's not the problem for this thread), so I tried to install k3b and graveman and still had problems. I read someone who made it work by running k3b as root, so I did so.

It didn't correct my burning problem, but it created a new problem, when I restarted my computer and trying to connect I had a message like asking me to check in .xsession-errors, I did so and found out that the .ICEauthority was owned by root and not the user, I changed the owner and I can now connect correctly.

Now, the problem is that every time a try to access a sudo protected thing the password is not required, I just have direct access from my normal user. So, I tought it might not be very secure to work like this.

Can someone help me on this?

---

