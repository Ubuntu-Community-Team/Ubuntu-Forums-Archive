---
title: "installing kernel-source."
date: 2005-08-19
forum: Desktop Environments
---

### Post by iDleR on 2005-08-19
Hi! I've just installed on my laptop Hoary 5.04 but I have a problem: I have a DWL-G122 D-Link Usb Wireless Pen so I've tried to install it on my laptop. I've find chipset driver [here](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page) but I need the kernel source. I use kernl 2.6.10-5-386 so I've found, using apt-cache search, kernel-source-2.6.10 so I've installed it. But when I try to compile the chipset driver there is an error because /lib/modules/2.6.10-5-386/build is missing. So how can I install the correct kernel source, pls?

---

### Post by iDleR on 2005-08-19
up

---

### Post by duminas on 2005-08-19
[QUOTE=iDleR]up[/QUOTE]
 Doing this should fix you right up.
```
sudo apt-get install linux-headers-2.6.10-5 linux-headers-2.6.10-5-386 build-essential
```
If linux-kernel-headers isn't installed, you might want to try grabbing that, too.

build-essential is in there just because you generally need it. You can omit it if you wish, but if you get some funky errors during install and you omitted it, grab it and see if that fixes them.

---

### Post by iDleR on 2005-08-19
I've installed linux-headers and build-essential (i forgot to tell) but problem remain, in /lib/modules/2.6.10-5-386/ there ins't build/

this is the error output:
```
 make: *** /lib/modules/2.6.10-5-386/build: No such file or directory. Stop.
rt2750.ko failed to build!
make: *** [module] Error 1
```

---

### Post by duminas on 2005-08-19
[QUOTE=iDleR]I've installed linux-headers and build-essential (i forgot to tell) but problem remain, in /lib/modules/2.6.10-5-386/ there ins't build/

this is the error output:
```
 make: *** /lib/modules/2.6.10-5-386/build: No such file or directory. Stop.
rt2750.ko failed to build!
make: *** [module] Error 1
```[/QUOTE]
 Did you install both of the linux-headers packages I referenced?

---

### Post by Hairy_Palms on 2005-08-19
hi i had the exact same problem a few months, and it would seem to me that the kernel headers are broken or have a bug, the messages i were getting were something like
> the kernel headers located in (cant remeber location) are incomplete or not correct, try installing a kernel source rpm or kernel headers.deb, at the time iw was trying to install the latest nvidia drivers but this problem meant i just gave up and installed the premade package from synaptic

---

### Post by iDleR on 2005-08-20
[QUOTE=duminas]Did you install both of the linux-headers packages I referenced?[/QUOTE]

yep

---

### Post by iDleR on 2005-08-20
[QUOTE=Hairy_Palms]hi i had the exact same problem a few months, and it would seem to me that the kernel headers are broken or have a bug, the messages i were getting were something like
, at the time iw was trying to install the latest nvidia drivers but this problem meant i just gave up and installed the premade package from synaptic[/QUOTE]

from the cd?

---

### Post by iDleR on 2005-08-20
up

---

### Post by iDleR on 2005-08-20
up pls

---

### Post by az on 2005-08-20
/lib/modules/2.6.10-5-386/build
is a symlink that is made when you install linux-headers-2.6.10-5-386.

Are you certain that this package is installed?  Build-essential and linux-headers-2.6.10-5-286 are on your cd, yes.

If you are sure that you installed the correct packages, did you do anything funny that may have erased the symlink?  It links /lib/modules/2.6.10-5-386/build to /usr/src/linux-headers-2.6.10-5-386

Do not just make that symlink without first trying to solve the problem of why it is not there.  It should be there.

---

### Post by iDleR on 2005-08-21
i swear, i've installed build-essential and linux-headers-2.6.10-5-386 (and linux-headers-2.6.10-5) and there is no "build/" symlink in that directory...I didn't modify anything there :(
Now I try to create the symlink...

---

### Post by iDleR on 2005-08-21
ok, I used the symlink, now it works, tnx...

---

