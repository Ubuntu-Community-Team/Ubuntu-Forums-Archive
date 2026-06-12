---
title: "kubuntu splash screen annoys me"
date: 2007-05-03
forum: Desktop Environments
---

### Post by daziplqa on 2007-05-03
Hi all,
I have installed kde desktop and find it not appropriate, so i removed it but its splash screen still exists.

I tried this post [http://ubuntuforums.org/showthread.php?t=416887](http://ubuntuforums.org/showthread.php?t=416887) but noway.

I just want to replace the starting splash screen of kubuntu with the one of ubuntu, given that i have removed kubuntu from my pc and the display manager i uses already gdm not kdm and when i told the terminal :

```
sudo update-alternatives --config usplash-artwork.so
```

he said :
```
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.

```

---

### Post by daziplqa on 2007-05-03
up up

---

### Post by k7k0 on 2007-05-03
Try [this]("http://ubuntuforums.org/showpost.php?p=2565139&postcount=2")
And maybe you should add:
```
sudo update-initramfs -u
```

---

### Post by Aetherius on 2007-05-04
The quickest *surefire* way i found to get rid of it is to totally uninstall usplash (sudo apt-get --purge remove) and any other related packages usplash-artwork* or ubuntu-usplash* etc

then reinstall usplash

;)

---

