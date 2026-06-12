---
title: "Installing Kile : Do I need all 766MB of packages?"
date: 2010-11-27
forum: Education &amp; Science
---

### Post by wniroshan on 2010-11-27
I am trying to install Kile on Ubuntu 10.04 using Synaptic Package manager. When I select Kile it installs 766MB of packages.

Do I need all these packages?

I am planing on using Kile for writing a thesis. Thesis is related to Computer Vision. In this context do I have to install packages like lilypond(which is for typesetting sheet music) too?

Are there any packages that can be removed from installation list?

Thank You.

---

### Post by mikewhatever on 2010-11-27
You can use '--no-install-recommends', as in 

```
sudo apt-get install --no-install-recommends kile
```

That reduces the size of the required packages almost tenfold, but may also remove useful features and functionalities. Look through the recommended packages and selectively install what's needed.

---

### Post by hzambran_cl on 2010-11-28
Just a comment: most of the packages included in the 766MB belongs to 'textlive', the latex engine, and not to Kile.

---

