---
title: "apt-get update removed my adobe-flashplugin"
date: 2012-05-05
forum: Desktop Environments
---

### Post by ronaldv on 2012-05-05
Ubuntu 11.10:

I run a 'apt-get update' yesterday and this has removed my adobe-flashplugin:

[PHP]
The following packages will be REMOVED
  adobe-flashplugin
The following NEW packages will be installed
  linux-headers-3.0.0-19 linux-headers-3.0.0-19-generic linux-image-3.0.0-19-generic
The following packages will be upgraded:
  apt apt-transport-https apt-utils chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg dpkg dpkg-dev etc.........
[/PHP]

Now I don have flash anymore in my browsers. :-(

What has happened to the flash-plugin? Has ubuntu decied to remove it from the repo's?

BTW: re-install fails: 
[PHP] sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'adobe-flashplugin' has no installation candidate
[/PHP]

All universe/restricted/multiverse repo's are enabled. I 'download from a server in netherlands'.

---

### Post by 3Miro on 2012-05-05
I think the name of the package changed. Check to see if flash is still working, if not, install Synaptic Package Manager and look for flash among all the packages.

---

### Post by oldos2er on 2012-05-05
Yes, I think it's now **flashplugin-installer**.

---

### Post by ubuntu27 on 2012-05-05
Yes, it is flashplugin-installer

```
sudo apt-get install flashplugin-installer
```

EDIT: Wait, there is also **adobe-flashplugin** in the repository. Both installs Flash, what are the differences?

I see that if I mark adobe-flashplugin to be installed, Synaptics ask to remove flashplugin-installer and install adobe-flash-properties-gtk (marked as recommended).

---

### Post by Max Blyss on 2012-05-05
If you're using Firefox, go get Flash-Aid from the Add-Ons and run it.

It will tell you if you're running the wrong one and fix it...  Worked great for me in 11.10, and I'm assuming it will work in 12.04, too.

---

### Post by ronaldv on 2012-05-07
Solved by installing 'flashplugin-installer'. 

Why doesn't Ubuntu warn you somehow for this quite important change???

---

### Post by archolman on 2012-05-08
> **Max Blyss said:**
> If you're using Firefox, go get Flash-Aid from the Add-Ons and run it.

It will tell you if you're running the wrong one and fix it...  Worked great for me in 11.10, and I'm assuming it will work in 12.04, too.

Works for 10.04 as well. Since I found it, I've had no unresolvable Flash glitches...
I'm using the ESR version of Firefox.

---

