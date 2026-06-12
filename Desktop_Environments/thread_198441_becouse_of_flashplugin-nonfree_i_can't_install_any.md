---
title: "becouse of flashplugin-nonfree i can't install anything"
date: 2006-06-17
forum: Desktop Environments
---

### Post by mitjab on 2006-06-17
when i want to install any app i get this error

```
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```


and when i try dpkg --configure -a nothing happens

```
sudo dpkg --configure -a 
Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...
```

what i can do that this will start working?

thx

---

### Post by rider343 on 2006-06-17
yes same here:

Instalando flashplugin-nonfree (7.0.63.3ubuntu3) ...
 and nothing happen...

maybe macromedia repo is down?

---

### Post by pete83 on 2006-06-17
Yeah, I had the same thing. To stop and remove the flash plugin, type this at a terminal:

sudo dpkg -P flashplugin-nonfree


If you want the flash plugin, download it from the adobe/macromedia site, and follow their directions int he readme file.

---

### Post by someusernoob on 2006-06-17
Yes, i had it too. Did download the plugin from the Adobe site and that works fine btw.

Really weird that such thing can "crash" your computer (it crashed mine when it kept saying "setting up" for over 15 minutes.)

---

### Post by sirhalos on 2006-06-17
Same problem. If I install Adobes flash from their site than it won't work with auto update correct?

---

