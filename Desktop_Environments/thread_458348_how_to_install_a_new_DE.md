---
title: "how to install a new DE"
date: 2007-05-29
forum: Desktop Environments
---

### Post by Mapkoz on 2007-05-29
Hi people....
since I am totally unsatisfied with the italian forum I ask you here....
I am a Kubuntu Feisty user (I am using kubuntu since Dapper and used Ubuntu 5.10 for a while before) 
and I installed th XFCE desktop environment with

```
sudo apt-get install xfce4
```

this installed just the XFCE desktop environment and the file browser Thunar (total 39MB) ...
my question now is...can I do something similar to this for Gnome?
I tried 
```
sudo apt-get install gnome
```
and
```
sudo apt-get install ubuntu-desktop
```

but both of them are like 690 MB....
can you help me?
Thank you a lot...

---

### Post by coffeecat on 2007-05-29
You only need ubuntu-desktop which, I believe, is a meta-package that will pull in everything you need for a complete Ubuntu-configured gnome environment. I'm not sure how different the gnome package in the Ubuntu repos is. I'm posting from Ubuntu Feisty (that's the Gnome version of Ubuntu) at the moment and, according to Synaptic, I don't have the gnome package installed. I guess the gnome package is for vanilla gnome, not the Ubuntu version.

Try just ubuntu-desktop - you should find it's considerably less than 690Mb, but it won't be as little as 39Mb. Don't forget that it will pull in a load of gnome apps too.

Once you've done that, you may find [this link]("http://doc.gwos.org/index.php/Different_usplash") useful. The irritating thing about installing ubuntu-desktop on kubuntu or kubuntu-desktop on Ubuntu is that you get a different usplash which may not be what you want.

By the way, I notice you installed Xfce by installing the Xfce4 package. I guess you would have got the (X)ubuntu styled Xfce desktop by installing xubuntu-desktop instead.

---

### Post by Mapkoz on 2007-05-29
Thanks man, it was exactly what ài was looking for...it's 190 MB though...
anyway...well the xfce4 was EXACTLY what I wanted ;);) I simply got my XFCE environment without any software other than Thunar... pretty cool thing for me.:D

---

