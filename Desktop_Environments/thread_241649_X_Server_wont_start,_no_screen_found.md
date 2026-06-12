---
title: "X Server wont start, no screen found?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Nickoladze on 2006-08-22
Yesterday i ran sudo apt-get upgrade and it installed some x server programs with no problems, and today when i booted the x server wouldnt start! It said something like "No devices found, no screen present."

would it be something in xorg.conf?
Please help, this is rather urgent

---

### Post by someusernoob on 2006-08-22
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

The new version of xserver-xorg-core might also be allready in your repositories. So try sudo apt-get update > sudo apt-get upgrade > sudo apt-get dist-upgrade, it might solve your problem.

---

### Post by wirah on 2006-08-22
I got the same thing!

Looks like somebody messed up xserver-xorg-core, because I ran a quick

```

apt-get update
apt-get upgrade

```

and a new xserver-xorg-core package was downloaded which fixed it.

This is a disaster however, because a lot of people are going to be stuck in console with no idea what to do. I hope this wont happen again, as it has ruined my view of Ubuntu as a user-friendly distro... sorry :(

---

### Post by Nickoladze on 2006-08-22
oh thank you ill go try it. and i think that is the package i installed last night.

edit: it worked! thanks

---

