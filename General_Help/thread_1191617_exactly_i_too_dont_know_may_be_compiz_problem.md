---
title: "exactly i too dont know may be compiz problem"
date: 2009-06-19
forum: General Help
---

### Post by icivilion on 2009-06-19
hi... i tried to install compiz on my friends laptop whic is HP 64 BIT AMD ATHLON, I tried installing as per the web guidelines  as per it it said first to remove the compiz-core like so... i did it.... later i came to know it was for older version of ubuntu.... now i am using 9.04... now i want to install compiz on this.... its not possible.... can any one help me... whenever i type sudo apt-get install compiz it gives same error saying E: Package build-essential has no installation candidate
i have pasted the output when i tried to install compiz.... please can any one help me step by step bit clearly.....


praveen@praveen-laptop:~$ sudo apt-get install build-essential gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev python-dev python-pyrex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
praveen@praveen-laptop:~$

---

### Post by pedro_orange on 2009-06-19
```
sudo apt-get update
```

```
sudo apt-get install build-essential
```

---

### Post by icivilion on 2009-06-19
thank you i tried that but it gave this error....


praveen@praveen-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
praveen@praveen-laptop:~$ 

would you tell me next what should i do

---

### Post by 3rdalbum on 2009-06-19
That sounds like an interesting HOWTO: "To install Compiz, first you have to remove Compiz!". Compiz is preinstalled, you just need the "compizconfig-settings-manager" package in order to change the visual effects settings.

Now to your package manager problem.

Run "sudo apt-get update" and see if this fixes your problem. If it doesn't, then try going to System > Administration > Software Sources and disable all the repositories in the "3rd party" tab, and enable all the repositories in the "Ubuntu sources" and "Updates" tab (except for "jaunty-proposed").

Close the program. It will ask if you want to reload the package list. Do it, and then see if you can install the Compiz package again.

---

### Post by pedro_orange on 2009-06-19
```
sudo dpkg --configure -a
```

```
sudo apt-get clean
```

```
sudo apt-get update
```

I agree with the previous poster. compiz is installed by default with Ubuntu. You shouldn't need to remove a whole host of things to get it working. 

You've probably got some dodgy things in your /etc/sources.list - Remove all the rubbish and try clean / update again if the above doesn't work.

---

### Post by icivilion on 2009-06-19
i tried doing it but nothing happend... and one more thing whenever i update my computer it satrts from 12% ..... this is the output ..
praveen@praveen-laptop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Reading package lists... Done
praveen@praveen-laptop:~$ sudo apt-get build-essentials
E: Invalid operation build-essentials
praveen@praveen-laptop:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials
praveen@praveen-laptop:~$ 


i am using amd 64bit laptop and i am running ubuntu 9.04

---

### Post by pedro_orange on 2009-06-19
It's build-essential not build-essentials

Try:

```
apt-cache search build-essential
```

---

### Post by icivilion on 2009-06-19
> **pedro_orange said:**
> ```
sudo dpkg --configure -a
``````
sudo apt-get clean
``````
sudo apt-get update
```I agree with the previous poster. compiz is installed by default with Ubuntu. You shouldn't need to remove a whole host of things to get it working. 

You've probably got some dodgy things in your /etc/sources.list - Remove all the rubbish and try clean / update again if the above doesn't work.

Thank you very much pedro... it worked... thanks a lot.... what does dpkg -- configure -a do... anyway thank you... its workin smooth now....

---

### Post by pedro_orange on 2009-06-19
No problem.

It configures all unpacked packages.

---

