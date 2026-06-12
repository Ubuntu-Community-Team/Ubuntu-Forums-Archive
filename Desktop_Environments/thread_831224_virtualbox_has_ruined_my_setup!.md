---
title: "virtualbox has ruined my setup!"
date: 2008-06-16
forum: Desktop Environments
---

### Post by jimmyxx on 2008-06-16
Hi all,
just got a new computer and done a clean install of 8.04 32 bit.

I had a total mare getting the nvidia 9series graphics to work but after a lot of poking it was there. I then went and installed virtual box....

Since then i lost my graphics (back down to safety mode) and I've lost my ALSA support.

I installed virtualbox-ose-modules-generic (as it was complaining saying i needed to install this for it to work).

I've since reinstalled my nvidia driver so i've got my graphics back, still no sound - but now virtualbox is moaning again asking me to reinstall ose-modules....

Does anyone know how to fix this horrible mess? I really want my sound back and it would be good to get virtualbox working - but if its going to be too tricky i just want to reverse what ever its done and ill use vmware!!!


thanks for any help!

---

### Post by Zorael on 2008-06-16
Do you have the modules package installed?
```
$ apt-cache policy linux-ubuntu-modules-`uname -r` linux-generic
```

It *should* say something like the following.
```
$ apt-cache policy linux-ubuntu-modules-`uname -r` linux-generic
linux-ubuntu-modules-2.6.24-19-generic:
  **_Installed: 2.6.24-19.27_**
  Candidate: 2.6.24-19.27
  Version table:
 *** 2.6.24-19.27 0
        500 http://se.archive.ubuntu.com hardy-proposed/main Packages
        100 /var/lib/dpkg/status
linux-generic:
  **_Installed: 2.6.24.19.21_**
  Candidate: 2.6.24.19.21
  Version table:
 *** 2.6.24.19.21 0
        500 http://se.archive.ubuntu.com hardy-proposed/restricted Packages
        100 /var/lib/dpkg/status
     2.6.24.18.20 0
        500 http://se.archive.ubuntu.com hardy-updates/restricted Packages
        500 http://security.ubuntu.com hardy-security/restricted Packages
     2.6.24.16.18 0
        500 http://se.archive.ubuntu.com hardy/restricted Packages
```
Well, the version numbers aren't important, as long as they don't say **(none)**.

To install:
```
$ sudo aptitude install linux-generic
```
The modules package is included in that virtual package, so just grabbing should fix things. IF it's the cause at all.

---

