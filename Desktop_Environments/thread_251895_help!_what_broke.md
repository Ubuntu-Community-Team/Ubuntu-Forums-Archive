---
title: "help! what broke"
date: 2006-09-06
forum: Desktop Environments
---

### Post by terranz on 2006-09-06
I had XGL and compiz installed and working well untill i installed USP - ubuntu system panel (a.k.a. gnome system panel).

I have a radeon card so I followed these instructions

This page to have direct rendering enabled.
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually)

Then this one to install compiz
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

option 2 so I could choose to login with compiz running or not

But I installed usp_0.41-1_all.deb and now when I log in using compiz I have no direct rendering and when i log into vanilla gnome I do have direct rendering.

Help please, I followed the first set of instructions again and it didn't help.
-

---

### Post by dentaku65 on 2006-09-06
mmm, I think really that not depends from usp the causing of the deactivaction of direct rendering... as far as I can tell (second link) is pretty old, in order to start compiz you must replace gconf with csm, gconf configuration is not used anymore for compiz settings

See these two treads:

[http://yep.it/?rudzee](http://yep.it/?rudzee)
and
[http://yep.it/?1nfdj1](http://yep.it/?1nfdj1)

Can be helpful...

---

### Post by terranz on 2006-09-06
Yeah I found that thread now, thanks.

---

