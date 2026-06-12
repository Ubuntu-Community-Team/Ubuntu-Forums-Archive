---
title: "Reactive GDM from KDM"
date: 2008-05-05
forum: Desktop Environments
---

### Post by andyrue304 on 2008-05-05
Hello I'd like to reactivate the GDM as default login screen, please see [http://ubuntuforums.org/showthread.php?t=783311]("http://ubuntuforums.org/showthread.php?t=783311") this post for more info.

How would I go about doing this?

I've tried to KDE control Centre to stop KDE loading at start-up but that just gives me no GUI at all and I have to type in sudo GDM...

Cheers

---

### Post by lesergi on 2008-05-05
You cant reactive gdm doing:

```
sudo dpkg-reconfigure gdm
```

And selecting GDM as default.

Bye!

---

### Post by p_quarles on 2008-05-05
In a terminal window, type the following:
```
sudo dpkg-reconfigure gdm
```
A menu will come up asking which login manager you want to use. Choose GDM, and you're set.

---

### Post by lesergi on 2008-05-05
You cant reactive gdm doing:

```
sudo dpkg-reconfigure gdm
```

And selecting GDM as default.

Also, you have to install ubuntu-desktop (for gnome support):

```
sudo apt-get install ubuntu-desktop
```

Bye!

---

### Post by p_quarles on 2008-05-05
In a terminal window, type the following:
```
sudo dpkg-reconfigure gdm
```
A menu will come up asking which login manager you want to use. Choose GDM, and you're set.

---

### Post by andyrue304 on 2008-05-05
> **lesergi said:**
> You cant reactive gdm doing:

```
sudo dpkg-reconfigure gdm
```

And selecting GDM as default.

Bye!

> **p_quarles said:**
> In a terminal window, type the following:
```
sudo dpkg-reconfigure gdm
```
A menu will come up asking which login manager you want to use. Choose GDM, and you're set.

Many thanks.

New it was simple thing!:)

---

