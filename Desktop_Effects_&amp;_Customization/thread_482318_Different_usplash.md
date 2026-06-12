---
title: "Different usplash?"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by UK-Wobbie on 2007-06-23
Hey i installed KDE on my ubuntu! But when i reboot the pc it puts up kubuntu loading screen! I like it to be ubuntu loading screen, Can any one help? :D

Or do any one no of different usplash code?

thanks

---

### Post by Fireblend on 2007-06-23
Just open a terminal, type

```
sudo update-alternatives --config usplash-artwork.so && sudo dpkg-reconfigure linux-image-`uname -r` 
```

and select the usplash you want to use.

---

### Post by UK-Wobbie on 2007-06-23
> **Fireblend said:**
> Just open a terminal, type

```
sudo update-alternatives --config usplash-artwork.so && sudo dpkg-reconfigure linux-image-`uname -r` 
```

and select the usplash you want to use.

Hey thanks mate thats top! I been looking for that code all over the net lmfao :D

---

