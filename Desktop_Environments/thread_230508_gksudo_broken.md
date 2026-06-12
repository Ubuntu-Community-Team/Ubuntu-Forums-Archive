---
title: "gksudo broken"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Nikusan on 2006-08-06
Hi all,
I just downloaded quite a large number of updates and there is a bunch of breakages.

sudo works fine but gksudo claims I've typed the wrong password.
The icons in my menus are gone.
My workspace switcher disappeared.
Every time I boot I have to re-enter my dns server, ubuntu forgets it.
I can't hold backspace to delete a row of text, I have to tap it for each character.
Many, many other things.

What the hell just happened?

EDIT: I just found out that ekiga is broken also. This is the error:

"Gconf key error

Ekiga got an invalid value for the GConf key "/apps/ekiga/general/gconf_test_age"."

---

### Post by Skia_42 on 2006-08-06
What repositories did you download from?

---

### Post by Nikusan on 2006-08-06
> **Skia_42 said:**
> What repositories did you download from?

dapper, dapper-updates, dapper-security, dapper-backports, PLF, Cipherfunk
and the XGL repos below

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

---

