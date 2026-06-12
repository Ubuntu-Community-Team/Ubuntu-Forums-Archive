---
title: "[SOLVED] Installed CF. Cannot remove Beryl Settings Manager"
date: 2007-08-08
forum: Desktop Effects &amp; Customization
---

### Post by Inxsible on 2007-08-08
I installed Compiz Fusion and so I wanted to remove Beryl since everything seems to work in CF.

when I did a ```
sudo aptitude remove beryl beryl-manager
```it did remove those packages, but i still have Applications --> System Tools --> Beryl Settings Manager. when I click on it, it also pulls up the application, which means it is still installed. what is the package name for it?

I tried searching in the Synaptic, but i get quite a few beryl  related packages that are installed..but since CF and Beryl have merged, i am not sure if they are required by CF.

---

### Post by Kingsley on 2007-08-08
You might have beryl-core installed.

---

### Post by esc1 on 2007-08-08
Sytems, Admin, Synaptic.... look for anything with beryl still intsalled.

---

### Post by Inxsible on 2007-08-08
> **Kingsley said:**
> You might have beryl-core installed.yes i do have that installed, but is it not required by Compiz fusion ?

> **esc1 said:**
> Sytems, Admin, Synaptic.... look for anything with beryl still intsalled. in all i have about 10 beryl related packages. 

What i dont know is, are they a required dependency for CF

---

### Post by Bachstelze on 2007-08-08
Moved to Desktop Effects & Customization.

---

### Post by Inxsible on 2007-08-08
These are the beryl related packages that I still have installed
```
beryl-core
beryl-plugins
beryl-plugins-data
beryl-plugins-unsupported
beryl-plugins-unsupported-data
beryl-settings
beryl-settings-bindings
beryl-vidcap
libberyldecoration0
libberylsettings0
``` Are all of these safe to remove. In other words will removing any of these cause any issues with my Compiz Fusion install?

---

