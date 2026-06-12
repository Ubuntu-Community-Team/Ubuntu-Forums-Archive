---
title: "Bootsplash themes?"
date: 2005-12-24
forum: General Help
---

### Post by CPUFreak91 on 2005-12-24
How can I change the bootsplash themes? I looked for a directory containing bootsplash .cgf files and the ubuntu picture but I can't find it.

---

### Post by rcerreto on 2005-12-24
There's a line within /boot/grub/menu.lst:
**splashimage (hd1,0)/boot/grub/images/ubuntu_dance.xpm.gz**
edit it to point to your new image.

Still I don't know which size it has to be, I can imagine that not everyone will do

---

### Post by oskude on 2005-12-24
[http://ubuntuforums.org/showthread.php?t=89916](http://ubuntuforums.org/showthread.php?t=89916)
and here the first hit by google
[http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)

---

### Post by adie273 on 2005-12-24
If you mean the GRUB splashimage, then oskude has you covered.

If you mean the usplash image, then try...

[https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)

See if it helps you any,

Adie

---

### Post by CPUFreak91 on 2005-12-24
Well now that I think about it, I could use both. But I was originally looking for usplash (sorry)

---

