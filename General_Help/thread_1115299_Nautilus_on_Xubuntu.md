---
title: "Nautilus on Xubuntu?"
date: 2009-04-03
forum: General Help
---

### Post by chessnerd on 2009-04-03
Hi, I'm new to Linux and I recently installed Xubuntu 8.04 on an old computer. I've used Ubuntu before on a friend's computer (which is why I went with Xubuntu over another Linux version) and I like the Nautilus file manager better than Thunar. I was wondering if there was a way to install Nautilus on Xubuntu without slowing down Xfce?

---

### Post by kanikilu on 2009-04-03
I can't say whether or not it will "slow down" your system, however, I don't believe the file managers are tied the DE, so you should be able to install and use nautilus in XFCE - although I expect that it will bring in some libraries and dependencies with it...in fact you can see exactly what it needs here:

[http://packages.ubuntu.com/intrepid/nautilus](http://packages.ubuntu.com/intrepid/nautilus)

BTW, if you do install it, you'll probably want to run it with the no-desktop option:```
nautilus --no-desktop
```

---

### Post by anjilslaire on 2009-04-03
```

sudo apt-get install nautilus

```

---

### Post by ShaunG on 2009-04-03
Hey chessnerd, 

I started off with an install of Ubuntu 8.04 and after a few months i downloaded the xfce desktop as gnome was starting to annoy me. However I also missed Nautilus greatly, thunar is great but doesn't cut it.

Anyways, do just as kanikilu suggested. 

To run nautilus, type alt+f2 to bring up the run window then type in 

```
nautilus --no-desktop
```

This will open nautilus in your home directory :D

---

### Post by chessnerd on 2009-04-03
Thanks guys, I got Nautilus to work. Also, you're right, it is important to run it with --no-desktop. ;)

---

