---
title: "Compiz addons, problem finding compiz-bcop"
date: 2007-11-16
forum: Desktop Effects &amp; Customization
---

### Post by thefatmoop on 2007-11-16
I was following this guide 
[http://forum.compiz-fusion.org/showthread.php?t=5303]("http://forum.compiz-fusion.org/showthread.php?t=5303")

I was able to get it working correctly once, but I was having some odd mounting problems with 7.10.I reformatted because of that and I wanted to give Ubuntu more space, but now I cant get add-ons to install to Compiz correctly. 

my problem is that if i follow the 

```
sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev emerald libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool

```

this part isnt working 
```
sudo apt-get install compiz-bcop
```

here is the error I get:

chowda@Operetta:~$ sudo apt-get install compiz-bclop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-bclop
chowda@Operetta:~$

can someone correct me or tell me an alternative method? Thanks!

---

### Post by thefatmoop on 2007-11-16
like is it the server i'm trying to contact that doesnt have it?

---

### Post by totalnub on 2007-11-16
check your spelling man, compiz-bcop is not compiz-bclop

---

