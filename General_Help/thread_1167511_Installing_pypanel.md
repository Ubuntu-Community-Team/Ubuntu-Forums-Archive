---
title: "Installing pypanel"
date: 2009-05-22
forum: General Help
---

### Post by AllRadioisDead on 2009-05-22
Hi, I downloaded crunchbang linux 9.04.01 and I found that our friend pypanel has been removed from the 9.04 repos. As tragic as this sounds, I was horrified. I tried finding the intrepid deb on the web, and the install button is greyed out with no error. I also tried building from source, and it won't install because it complains that it doesn't have GCC even though I have all the dependencies installed. Help is appreciated as always.

---

### Post by Locutus_of_Borg on 2009-05-23
what is the exact error message?

---

### Post by AllRadioisDead on 2009-05-23
> **Locutus_of_Borg said:**
> what is the exact error message?
In the message, I mentioned that there was no error message given when I tried to run the deb.
The exact GCC error was: 
"command '*gcc*' failed with exit status 1"

---

### Post by Locutus_of_Borg on 2009-05-23
what are you doing to build it?

should be 
```

sudo python setup.py
```
while in the PyPanel directory

---

### Post by AllRadioisDead on 2009-05-23
> **Locutus_of_Borg said:**
> what are you doing to build it?

should be 
```

sudo python setup.py
```while in the PyPanel directory
That's exactly what I do.

---

### Post by Locutus_of_Borg on 2009-05-23
and you have kernel headers and build_essential installed?

---

### Post by AllRadioisDead on 2009-05-23
> **Locutus_of_Borg said:**
> and you have kernel headers and build_essential installed?
Yes I do.

---

### Post by AllRadioisDead on 2009-05-23
Bump :)

---

### Post by AllRadioisDead on 2009-05-23
I found the solution. The package "xlibs-dev" was needed, but was no longer available in the jaunty repos. I found it in the hardy repos and it installed just fine.

---

