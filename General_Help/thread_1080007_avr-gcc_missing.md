---
title: "avr-gcc missing"
date: 2009-02-24
forum: General Help
---

### Post by samiscooking on 2009-02-24
Hi everybody, I downloaded an IDE to program the arduino microcontroller ([http://www.arduino.cc/](http://www.arduino.cc/)) but it needs the avr-gcc package, I tried to install it via apt-get but this is what i get 
```
Package avr-gcc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package avr-gcc has no installation candidate
``` why? I have the standard /etc/apt/source.list , I tried to find some extra repositories to add but it seems that avr-gcc should be already available with the standard ubuntu repositories...some hint?

---

### Post by geraldm on 2009-02-25
The distribution is separate from gcc.
The package name is avr-libc.
The project:
[http://www.nongnu.org/avr-libc/](http://www.nongnu.org/avr-libc/)

best regards,
Gerald

---

### Post by samiscooking on 2009-03-24
Thanks, solved

---

