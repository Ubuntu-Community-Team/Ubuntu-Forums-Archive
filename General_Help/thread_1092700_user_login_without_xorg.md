---
title: "user login without xorg"
date: 2009-03-10
forum: General Help
---

### Post by peedeeramone on 2009-03-10
this is actually a debian machine but i assume it is the same.

i have a debian machine that i am using as a webserver with apache. i have it set to autologin to a specific user after 30 seconds. i want to free a bit of resources since this server will not normally have a monitor connected. how would i disable the x server when this user is logged in?

thanks

---

### Post by fcuk112 on 2009-03-10
to disable xterm you can try sudo sysv-rc-conf and remove X from level 2.

---

### Post by peedeeramone on 2009-03-10
but wouldn't that remove x from all users once logged in?

I will do this if I can't figure out any other way, because if I do login directly from the machine i can start X manually, i just wanted it to be set up so just this specific user wouldn't have x started by default

---

### Post by fcuk112 on 2009-03-10
sorry, i am not running multiple users so can't help you with this.  perhaps someone else can provide the answer here...

---

### Post by peedeeramone on 2009-03-10
thanks anyway. Your solution is my backup plan.

---

### Post by fcuk112 on 2009-03-10
> **fcuk112 said:**
> to disable xterm you can try sudo sysv-rc-conf and remove X from level 2.

correction: that should be remove the X from level 2 for GDM only.

---

