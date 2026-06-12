---
title: "Compiz BROKEN!"
date: 2006-08-26
forum: Desktop Environments
---

### Post by gruffy-06 on 2006-08-26
If you recently updated your Compiz packages (optional), then you may have noticed that the window borders have disappeared, but the effects still work. I wonder when a fix will be available. In the meantime, I had to use metacity.

---

### Post by moini on 2006-08-26
Hi, I've same Problem.

IBM Notebook T43, with Intel 915/910 VGA and Compiz-Vanilla...

Yesterday xserver restartet randomly then I updated today.
After the update compiz does not show window borders. metacity is running ok.

Udated

xserver-xorg-driver-i810_1%3a1.6.5-0ubuntu1_i386.deb
xserver-xorg-air-core_1%3a1.1.1-0ubuntu2_i386.deb
linux-dri-modules-2.6.15-26-686_20060824-0aiglx~compiz1_i386.deb
linux-dri-modules-common_20060824-0aiglx~compiz1_i386.deb

regards

moini

---

### Post by Reb on 2006-08-27
same deal with me...

---

### Post by mcduck on 2006-08-27
If compiz works but window borders are missing you could try to change to some other cgwd theme and restart compiz.

---

### Post by Rasitiln on 2006-08-27
I just upgraded mine and it went just fine. Im using a nvidia 6200 here

---

### Post by moini on 2006-08-27
hi, i was getting nervous...

after all i installed normal compiz (which deinstalled compiz-vanilla) and i am very very happy. after reading, gset-compiz is replaced by another tool gnome-compiz-manager....

what i did:

i added following to my sources list

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

# for the missing gset-compiz
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0
deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0


after that i made
apt-get install cgwd compiz compiz-core compiz-gnome xserver-xorg-air-core gnome-compiz-manager cgwd-themes


and everything looks more fancy


./regards

moini

---

### Post by dentaku65 on 2006-08-27
> **gruffy-06 said:**
> If you recently updated your Compiz packages (optional), then you may have noticed that the window borders have disappeared, but the effects still work. I wonder when a fix will be available. In the meantime, I had to use metacity.

It works perfect here... can you post your start-compiz?

---

### Post by PhrankDaChickenGeek on 2006-08-28
Same prob. Output is

```

** (cgwd:6778): WARNING **: Cannot open pixmap: unshade

** (cgwd:6778): WARNING **: Cannot open pixmap: above

** (cgwd:6778): WARNING **: Cannot open pixmap: unabove

** (cgwd:6778): WARNING **: Cannot open pixmap: sticky

** (cgwd:6778): WARNING **: Cannot open pixmap: unsticky


```

my Plugins are loaded in right order.

---

