---
title: "Aptitude will not get compizconfig-settings-manager"
date: 2007-08-01
forum: Desktop Effects &amp; Customization
---

### Post by dexwiz on 2007-08-01
I followed the guide for installing Compiz Fusion to a T, but when I run the line 

```
sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes
```

It returns:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

```

Is the server down or something?

---

### Post by dexwiz on 2007-08-01
Any help?

---

### Post by psyopper on 2007-08-01
What repository are you using for Compiz? Also, did you remember to 
```
 sudo aptitude update
``` before trying to get it?

One more thing, I might suggest using aptitude rather than apt-get, it handles dependencies a lot better and is generally more feature rich.

---

