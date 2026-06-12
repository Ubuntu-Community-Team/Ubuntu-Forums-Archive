---
title: "Help! Dependency HELL with 'build-essential'"
date: 2006-09-14
forum: Desktop Environments
---

### Post by saehn on 2006-09-14
I want to install build-essential to compile some source I've downloaded. I don't have any broken packages showing in Synaptic. My repository list is clean, but I can display it if need be. Here's what's happening, please help!:

shane@shane-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed. The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
shane@shane-desktop:~$ sudo apt-get install libc6-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed. The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.4-1ubuntu9 is to be installed
E: Broken packages

---

### Post by lamego on 2006-09-14
Please cleanup your sources.list to the default ubuntu list you must have included some non Ubuntu repository which is causing that dependency hell, then:
```
sudo apt-get update
```
What source are you trying to compile ?

---

### Post by konst88 on 2006-09-14
use aptitude instead of apt-get, it is resolving dependencies much better.
the commands with it is the same, just replace the word apt-get with aptitude.
good luck!

---

### Post by SendDerek on 2006-10-15
aptitude install gcc worked for me!  Thanks for the tip konst88!

---

### Post by elettronicha on 2006-10-15
> **saehn said:**
> I want to install build-essential to compile some source I've downloaded. I don't have any broken packages showing in Synaptic. My repository list is clean, but I can display it if need be. Here's what's happening, please help!:
Did you enable all the necessary repos?

---

