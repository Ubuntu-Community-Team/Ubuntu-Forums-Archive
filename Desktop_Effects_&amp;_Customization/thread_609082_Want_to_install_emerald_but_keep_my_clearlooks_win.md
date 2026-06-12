---
title: "Want to install emerald but keep my clearlooks window border"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by mmcmonster on 2007-11-10
I installed emerald so that I can create a user account that [looks like Apple OS X]("http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac").  The problem is, on my other account logins, I want to keep my clearlooks window borders (I like how out-of-the-way they appear).

Is there a way to enable the emerald window borders for some user acocunts but not all?

Baring that, is there a clearlooks theme for emerald?

---

### Post by Forlong on 2007-11-10
> **mmcmonster said:**
> Is there a way to enable the emerald window borders for some user acocunts but not all?
Yes: ```
gedit ~/.config/compiz/compiz-manager
```
put this in there
```
USE_EMERALD="no"
```
And save.

Do that in every account where you don't want to use Emerald.

---

### Post by mmcmonster on 2007-11-12
Thanks!  Works fine.

---

### Post by sujoy on 2007-12-23
works great
thanks a lot :)

---

