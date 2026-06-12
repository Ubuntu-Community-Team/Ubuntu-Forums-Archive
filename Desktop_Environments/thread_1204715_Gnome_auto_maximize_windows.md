---
title: "Gnome auto maximize windows"
date: 2009-07-05
forum: Desktop Environments
---

### Post by sefokuma on 2009-07-05
Hi, i use UNR and i am using standard gnome desktop, when i open a new window or appear new window dialog this auto maximize it. Where can i change this parameter for dont auto maximize?

Thanks guys.

---

### Post by solidus126 on 2009-07-11
Hello!

I was having the same problem as you just now and followed the instructions [ here]("http://ubuntuforums.org/archive/index.php/t-1170468.html"). All I did was issue:

```
sudo apt-get remove maximus
```

And then rebooted (probably can get by with simply logging out and back in).

-solidus126

---

### Post by floatdrop on 2009-12-25
> **solidus126 said:**
> Hello!
```
sudo apt-get remove maximus
```
-solidus126

It is veery brutal method. Besides you lost the hiding function of top part of window (where is the title and close etc buttons) in Ubuntu.

Better go to gconf-editor, find maximus (/app/maximus) and set no_maximize.

---

