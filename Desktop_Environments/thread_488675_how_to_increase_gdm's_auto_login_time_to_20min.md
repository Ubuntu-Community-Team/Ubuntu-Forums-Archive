---
title: "how to increase gdm's auto login time to 20min?"
date: 2007-06-30
forum: Desktop Environments
---

### Post by ashwin_cse on 2007-06-30
Hi,

I want to increase the delay before auto-login starts to more than 20 minutes. That is if the pc is not used for more than 20 minutes then it should login to a account (in this case a non-privileged account). But option found in System->Administration->Login Window allows for only a maximus of 100seconds nearly 1.6 minute, which to me is a very low value. How do i change this value to as said 20 minute.

with regards,
ashwin

---

### Post by lha on 2007-07-01
Hi,

The delay (and many other gdm settings) are located in /etc/X11/gdm/gdm.conf. The relevant lines are
```
# Timed login, useful for kiosks.  Log in a certain user after a certain amount
# of time.
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30
```
Since gdm.conf may be overwritten by updates, modifications should be made to /etc/X11/gdm/gdm.conf-custom.

---

