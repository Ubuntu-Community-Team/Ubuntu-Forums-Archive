---
title: "[gnome] uninstalling KDE.."
date: 2008-11-14
forum: Desktop Environments
---

### Post by plasmarox on 2008-11-14
Hi all, i have a couple of Qs about uninstalling the kubuntu-desktop.

i installing the kubuntu-desktop using:
```
sudo apt-get install kubuntu-desktop
```

Which went perfectly (except it doesn't log me in, i have to ctrl-alt-f4, login and exit to login)

Now, that ive tried the KDE and i don't like it. Now i want to get rid of it.

Can i just do ```
sudo apt-get remove kubuntu-desktop
```

will this completely remove?

Also , the boot screen shows kubuntu - will the default ubuntu one be put back? will i still be able to boot and login as i did before?

Im still quite new, so thanks for your time :D

---

### Post by 73ckn797 on 2008-11-14
The remove command will work. Follow this guide for complete removal:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by aged hippy on 2008-11-14
According to this guide here:
[http://ubuntuforums.org/showthread.php?t=205002](http://ubuntuforums.org/showthread.php?t=205002)
> 
 HOWTO: correctly install/remove k/x/ed/ubuntu-desktop packages
This how-to is for correctly installing and/or removing the x/k/ed/ubuntu-desktop meta packages.

NOTE: No matter what distribution you have installed (ubuntu/kubuntu/xubuntu/edubuntu), you can have all four meta packages at the same time, and switch between them all the time.

NOTE: Meta packages are just packages that point to many other packages. So, if you remove the ubuntu-desktop package (with apt-get or synaptic) even though you have ubuntu installed, nothing will happen. All the packages will remain there, just the pointer ubuntu-desktop package will be gone, but essentially nothing will be removed. If installed with aptitude, like this guide, the meta package does get completely removed, along with all the packages it points to.

This is the best way to do it, because it is a lot easier to remove one of the desktop environments later using this method, if you don't want one of them anymore.


.... yes, it will. :D

---

### Post by plasmarox on 2008-11-14
Hi all;

I used ```
 sudo apt-get remove kubuntu-desktop
```

However, the boot loading screen and kubuntu option in the session opetions when i log in :(

I will therefore follow the options in the above posts and report back.

Thanks =D

---

