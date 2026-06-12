---
title: "Changing splash screen back ti Ubuntu after installing xubuntu-desktop in 13.04"
date: 2013-05-29
forum: Desktop Environments
---

### Post by zemega on 2013-05-29
The other day I installed xubuntu-desktop inside Ubuntu 13.04. Now I'm getting Xubuntu splash screen when booting and during shutdown. How can I change this back to using Ubuntu splash screen?

---

### Post by stinkeye on 2013-05-29
In the terminal run...
```
sudo update-alternatives --config default.plymouth
```
and choose **ubuntu-logo.plymouth**

Then run ...
```
sudo update-initramfs -u
```

**[SIZE=3]or[/SIZE]**

just remove the xubuntu plymouth theme and it will revert back  to the ubuntu plymouth theme.
```
sudo apt-get remove plymouth-theme-xubuntu-logo
```

---

### Post by zemega on 2013-05-29
Thank you. I'll choose to configure the plymouth. I'm not going to remove the xubuntu one, I might want to show it to other people.

---

