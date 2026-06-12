---
title: "compiz fusion"
date: 2009-05-04
forum: Desktop Environments
---

### Post by sridarshan on 2009-05-04
can anyone tell me the step by step procedure to install compiz fusion

help required for a complete newbie

---

### Post by canadiandude007 on 2009-05-04
Are you using GNOME or KDE as your graphical display?

You need to do something like:
> sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf

Then if you don't get any errors, run:

> compiz --replace

Hope that helps!

---

### Post by sridarshan on 2009-05-04
> **canadiandude007 said:**
> Are you using GNOME or KDE as your graphical display?

You need to do something like:


Then if you don't get any errors, run:



Hope that helps!

i copy pasted the first command you mentioned and i got the error as
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcompizconfig-backend-gconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libcompizconfig-backend-gconf has no installation candidate
""

and btw i'm using gnome ubuntu jaunty jackalope

---

### Post by overdrank on 2009-05-04
Hi and compiz is already install by default, You may want to look a the FAQ's link in my signature :)

---

