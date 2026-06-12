---
title: "theme resets after every reboot"
date: 2012-12-20
forum: Desktop Environments
---

### Post by Askel on 2012-12-20
I have the faience-theme. After it updated the theme gets reset every time I reboot. I have to open MyUnity and change the theme to get it right again. Is there a solution to this.

---

### Post by Frogs Hair on 2012-12-20
Hello Askel

where is the theme installed and what Ubuntu version ?

---

### Post by Askel on 2012-12-20
I installed it using the PPA, and the Ubuntu-version is 12.04

---

### Post by vasa1 on 2012-12-20
> **Frogs Hair said:**
> Hello Askel

**where** is the theme **installed** and what Ubuntu version ?

Meaning did you install the theme in ~/.themes or in /usr/share/themes?

---

### Post by Askel on 2012-12-20
> **vasa1 said:**
> Meaning did you install the theme in ~/.themes or in /usr/share/themes?


It's in /usr/share/themes

---

### Post by Frogs Hair on 2012-12-20
The theme description states it only has support for Gnome 3.6 which is what 12.10 uses. > Description:
Faience is a Work In Progress that include GTK3, GTK2, Metacity and Gnome-Shell themes and an icon theme based on Faenza.

Support Gnome 3.6 only.

---

### Post by Askel on 2012-12-20
> **Frogs Hair said:**
> The theme description states it only has support for Gnome 3.6 which is what 12.10 uses.

Guess that explains it. To bad I updated then.

---

### Post by Askel on 2012-12-20
I have the folders with the old theme. How do I do to replace them in the /usr/share/themes folder?

I've used the mv command but it doesn't work. It says it can't remove the target cause it's a catalog.

---

### Post by Frogs Hair on 2012-12-20
You can replace them , but why does the PPA have themes that are not supported in your version of Ubuntu ? I would consider removing the PPA before manually installing the theme , because if the PPA updates you will have problems with the package system.

This is not a well managed PPA if it is providing incompatible versions of themes. If you are running 12.04 you should be using themes compatible with Gnome 3.4.

To open the file system use ```
gksudo nautilus
```

---

