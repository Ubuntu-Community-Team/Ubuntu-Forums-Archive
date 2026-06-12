---
title: "User account restrictions by time and time used"
date: 2006-03-29
forum: Desktop Environments
---

### Post by zoph on 2006-03-29
I'm using Ubuntu 5.10 for my kids computer.  I have a small problem where my teenager is always logged in and the other kids don't get any computer time.  I would like to be able to setup restrictions for the kids users such that they can only login within certain hours on given days.  This can be done using the pam time module, however I would also like to be able to enforce some sort of daily use limits, like maybe 2 hours per day, but preferably configurable for individual users rather than all users.  I can't seem to find anything obvious looking at various Linux forums and googling it.  Does anyone know of a method to setup these types of controls?

Thanks much,

-Z

---

### Post by aysiu on 2006-03-29
Maybe this might help?
[http://linux.com.hk/penguin/man/5/timeouts.html](http://linux.com.hk/penguin/man/5/timeouts.html)

---

### Post by zoph on 2006-03-29
Thank you, this is definitely heading in the right direction, however, my users are logging in via the X-windows front-end and when I do a ps -wuax I don't see them logging into a specific tty.  Do you have any idea how I might connect that in with X?

[QUOTE=aysiu]Maybe this might help?
[http://linux.com.hk/penguin/man/5/timeouts.html](http://linux.com.hk/penguin/man/5/timeouts.html)[/QUOTE]

---

### Post by aysiu on 2006-03-29
[QUOTE=zoph]Do you have any idea how I might connect that in with X?[/QUOTE] No idea. I just found that link through Google...

---

