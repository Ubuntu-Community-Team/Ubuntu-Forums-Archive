---
title: "Printer configuration: what is supposed to be installed?"
date: 2006-02-07
forum: Desktop Environments
---

### Post by marknewlyn on 2006-02-07
Hi

Firstly, I messed it up and don't ask why, I removed all printer gui related packages from my machines. No printing icon on the system->administration menu. 

Now I want it back :???: I tried installing gnome-cups but this doesn't help me because I want to set up a jetdirect printer and there is no cups server so I just get an error message and it closes.

What packages should I have installed to be able to use printing? Just a pointer to what default packages are installed would help too! I couldn't find a list easily and searching the forums for printing reveals only I was dumb enough to remove them all!

Any advice would be greatly appreciated.

Mark

---

### Post by kaamos on 2006-02-07
You could try
```
sudo apt-get install ubuntu-desktop
```
and install all that it wants to install, or just check what packages with "cups" would get installed.

---

### Post by marknewlyn on 2006-02-07
[QUOTE=kaamos]You could try
```
sudo apt-get install ubuntu-desktop
```
and install all that it wants to install, or just check what packages with "cups" would get installed.[/QUOTE]

Much obliged and it seems to have fixed everything.

Thanks!

---

