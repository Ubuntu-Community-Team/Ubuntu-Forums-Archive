---
title: "Unmet Dependencies prevents me from installing anything."
date: 2012-06-25
forum: Desktop Environments
---

### Post by supremekhaoz on 2012-06-25
When I tried installing the package it gave this error

> You might want to run 'apt-get -f install' to correct these: 
The following packages have unmet dependencies: 
lib32gcc1 : Depends: libc6-i386 (>= 2.11) but it is not going to be installed 
lib32stdc++6 : Depends: libc6-i386 (>= 2.4) but it is not going to be installed 
lib32z1 : Depends: libc6-i386 (>= 2.4) but it is not going to be installed 
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I can't install updates either

---

### Post by Peripheral Visionary on 2012-06-25
Whatever you are trying to install needs other software to run properly.   [COLOR=DarkOrange]**Synaptic Package Manager**[/COLOR] does a lot of this dependency-handling stuff automagically (using apt-get). If you use Synaptic to install the software you want, it will detect and include those things as well.  If the needed software is in the [COLOR=DarkOrange]**repositories**[/COLOR] you have in your sources list, it should all go down smoothly. Use synaptic instead of trying to install packages individually.

---

### Post by jmfal on 2012-06-25
Open a terminal and type:

```
 sudo  apt-get -f install   
```

Press enter

enter your password (you won't see it -security reasons) Press enter

If there is an error post it so somebody can help you.

---

