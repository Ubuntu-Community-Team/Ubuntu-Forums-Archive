---
title: "No Gama Settings for nVida card"
date: 2008-03-16
forum: Desktop Environments
---

### Post by Garmuar on 2008-03-16
I had gama setting for my nvidia card under windows.   I installed the nVidia 3d drivers from Add/remove repository and it works great for 3D games running on Gusty, but every things is so much darker than it was in XP.  I can't find any software Gama settings for my vid card. 

Are there any in Ubuntu??  I checked all the Screen and Graphics settings I could find under Admin and Preferences.

Thanks in advance.

---

### Post by steveneddy on 2008-03-16
In terminal run

```
nvidia-settings


```

---

### Post by kryth on 2008-03-17
Steveneddy, hit the nail head on.

---

### Post by rigol on 2008-03-18
You can also do a simple 

```
$ xgamma -gamma x.x
```

in a terminal, with x.x representing your gamma value.

---

### Post by Garmuar on 2008-03-19
Thank you very much.  I got gamma adjusted.

---

