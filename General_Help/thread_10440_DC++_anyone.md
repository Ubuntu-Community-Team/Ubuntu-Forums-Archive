---
title: "DC++ anyone?"
date: 2005-01-07
forum: General Help
---

### Post by earobinson on 2005-01-07
anyone know where i can get dc++ that will work with ubuntu?

---

### Post by ow50 on 2005-01-07
```
sudo apt-get install dcgui-qt
``` 
or
```
sudo apt-get install dctc dcgui
``` 

dcgui-qt, also known as valknut, works quite well.

dctc is a text based client and dcgui is a gui for it. dcgui has a horrible user interface and it didn't work for me at all. 

There's a newer version of the valknut dcgui-qt [here](http://dcgui.berlios.de/download.php), if you're into compiling.

Finally there's a [linux dc++](http://linuxdcpp.berlios.de/articles.php?um=index) in the making, but it's not yet ready.

---

### Post by earobinson on 2005-01-07
well u need to have the extra repositories but once i figured that out it worked thanks

---

### Post by fng on 2005-01-07
ditched dcgui, welcome dcgui-qt :)

---

### Post by earobinson on 2005-01-08
me to qt seems to be better

---

### Post by RadixLecti on 2005-02-11
The new valknut seems to have had a major bout with a cosmetic surgeon, it looks good (the 0.3.6 version). It looks nothing like the one that's available in the repository. But when I try to install the tar ball of 0.3.6 manually, it whines about me not having installed libxml2, which I have. 
Darn it all. ;)

---

### Post by ow50 on 2005-02-12
[QUOTE=RadixLecti]The new valknut seems to have had a major bout with a cosmetic surgeon, it looks good (the 0.3.6 version). It looks nothing like the one that's available in the repository. But when I try to install the tar ball of 0.3.6 manually, it whines about me not having installed libxml2, which I have. 
Darn it all. ;)[/QUOTE]

Do you have the dev package  'libxml2-dev'?

I don't care much about the makeover as its still not gtk, but it does seem to fuction better than 0.3.4 version i had previously.

---

### Post by RadixLecti on 2005-02-12
[QUOTE=ow50]Do you have the dev package  'libxml2-dev'?

I don't care much about the makeover as its still not gtk, but it does seem to fuction better than 0.3.4 version i had previously.[/QUOTE]
 No, that one I didn't have installed. I'll have to try it. ;)

---

### Post by Xappe on 2005-02-14
there actually is a dc++ port for linux called linuxdcpp or Wulfor reloaded. It uses gtk+ and it is usable but not fully stable (some bugs with the user list, and it freezes sometimes when handling tabs). 

[http://linuxdcpp.berlios.de/articles.php?um=index](http://linuxdcpp.berlios.de/articles.php?um=index)

---

### Post by piedamaro on 2005-02-14
I always used dcgui, it's the best, but I know what I'm doing...:D
Too bad it's no more developed.

---

### Post by earobinson on 2005-04-01
Anyone got a working DC for Horay?

---

### Post by uggeli on 2005-04-02
[QUOTE=Xappe]there actually is a dc++ port for linux called linuxdcpp or Wulfor reloaded. It uses gtk+ and it is usable but not fully stable (some bugs with the user list, and it freezes sometimes when handling tabs). 

[http://linuxdcpp.berlios.de/articles.php?um=index](http://linuxdcpp.berlios.de/articles.php?um=index)[/QUOTE]

Could anyone told to newbie how to get berlios dc++ linux port installed to ubuntu? Do I have to register to get some files downloaded or what is the idea there?

---

