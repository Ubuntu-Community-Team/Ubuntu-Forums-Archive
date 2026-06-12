---
title: "Installing Fonts"
date: 2009-03-21
forum: General Help
---

### Post by Lupy on 2009-03-21
I want to install the fonts I have on my old windows computer onto my linux one, because I liked some of them better than their substitutes. I went and copied the fonts .ttfs and put them on my desktop, but because I am not root, I cannot move them from 
```
/home/owner/Desktop/fonts
``` to 
```
/usr/share/fonts/trueype
```

So far, aside from plain old cut and paste, I have tried this:

```
gksudo gedit /home/owner/Desktop/fonts_to_/usr/share/fonts/truetype
```

Any help is appreciated, thanks ahead of time,

-Lupy

---

### Post by kaibob on 2009-03-21
An easier alternative that you may want to try is to place the new fonts in in the hidden .fonts directory in in your home directory. You'll have to create this folder if it's not present.

```
mkdir -p /home/username/.fonts

cp /home/username/Desktop/fonts/* /home/username/.fonts/
```

The following Ubuntu Wiki provides detailed instructions on the installation of fonts (but I would try the above first):

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

