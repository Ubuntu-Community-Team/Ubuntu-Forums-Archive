---
title: "keyboard layout"
date: 2009-05-10
forum: General Help
---

### Post by UltimaWeapon18 on 2009-05-10
hi all this is my first post ib this great forums
i ahve installed ubuntu 9.04 on my ps3 and work great for me but i have done something little stupid i add another layout for keyboard is arabic and i make alt+shift to change between arabic and english
the problem now in the login screen the keyboard writing arabic and my username is in english and it refuse to change to english with alt+shift so what to do???????
plz tell me not format :(

---

### Post by UltimaWeapon18 on 2009-05-10
up

---

### Post by cholericfun on 2009-05-10
try recovery mode...?
i think xfix asks you for keyboard layout

---

### Post by UltimaWeapon18 on 2009-05-10
thax man for help 
but how can i go to recovry mode :(

---

### Post by danwood76 on 2009-05-10
You can change the keyboard layout from the login screen.
Should be in the bottom left hand menu unless they have moved it.

---

### Post by cholericfun on 2009-05-10
reboot and you should have the option of booting normally or recovery mode
if you have various kernels you can boot into various kernels as well
... with their respective recovery modes

if these options dont show up while booting try pressing esc after the bios part went by..

---

### Post by UltimaWeapon18 on 2009-05-10
> **danwood76 said:**
> You can change the keyboard layout from the login screen.
Should be in the bottom left hand menu unless they have moved it.

u can change language but keyboard will still writing in arabic

---

### Post by UltimaWeapon18 on 2009-05-10
> **cholericfun said:**
> reboot and you should have the option of booting normally or recovery mode
if you have various kernels you can boot into various kernels as well
... with their respective recovery modes

if these options dont show up while booting try pressing esc after the bios part went by..

sorry to bother u but this my first time using linux so what u mean by the option to boot normally or recovery mode???? when kboot come?????
and preess esc after bios part????when is that???/ and thanks for help

---

### Post by cholericfun on 2009-05-11
never mind this esc after BIOS thing if you can get to the recovery option after boot.

strange - i thought xfix would ask you for your keyboard

so :

try  this thread

[http://ubuntuforums.org/showthread.php?t=1151141&highlight=keyboard+language](http://ubuntuforums.org/showthread.php?t=1151141&highlight=keyboard+language)

theres some hints as to what has to be changed where
since you'll be unable to type anything i'd say go for the LiveCD and change the settings there manually 
```
gksudo gedit  /etc/X11/xorg.conf
```
switching your keyboard layout to "us" or "en" or whatever else you want...

---

