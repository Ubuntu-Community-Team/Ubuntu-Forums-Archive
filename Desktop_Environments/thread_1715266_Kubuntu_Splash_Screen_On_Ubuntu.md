---
title: "Kubuntu Splash Screen? On Ubuntu?"
date: 2011-03-26
forum: Desktop Environments
---

### Post by a.kleiner on 2011-03-26
I have Ubuntu 10.10, and I recently installed KDE (package: kubuntu-desktop) from the software center. I was only intending KDE to be an alternative desktop environment for experimentation, and I selected GDM instead of KDM when prompted during package installation. Now, when I boot up or shut down, I'm getting the Kubuntu splash screen. Is there any way to set this back to how it was without getting rid of KDE? Yeah, I'm a little OCD, but it's just weird to see that on Ubuntu.

---

### Post by Krytarik on 2011-03-26
Run those commands and choose the Plymouth boot splash in between, the default is "ubuntu-logo.plymouth":
```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```Greetings.

---

