---
title: "Help on Installation Company of Heroes"
date: 2010-08-19
forum: Gaming &amp; Leisure
---

### Post by jarbiscuit on 2010-08-19
Hi All,

I'm totally new to the Ubuntu. it has been 3 months and i'm loving it!! Just that i've been trying to get my favorite game; Company of heroes into my machine but was failed.

my system: Ubuntu 10.04 running on Acer aspire 4710g, ati radeon hd2300. 

i installed wine 1.3 already. Installed the game. try to run it but getting this error, "failed to find supported hardware rendering device. Ensure your system meets the minimum requirements. verify that DirectX is properly installed n have latest drivers bla bla bla.." 

I read that i need to patch wine. but i dont know how.
I also need to patch the game, also failed to do so with error, "patching system detects that critical game files have been modified. Files are either missing, moved.. bla bla bla..". Any idea on this?

Can somebody show me step-by-step on how to install this game? Really appreciate the help~

---

### Post by ronnielsen1 on 2010-08-19
Do you have a Company of Heroes version #?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4506](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4506)

---

### Post by jarbiscuit on 2010-08-19
Version 1.0 i believe. Still not doing any changes to it.

---

### Post by J.K.Makowka on 2010-08-19
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18109](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18109)

try winetricks, make sure you have a good GPU driver installed, check if 3D acceleration is enabled in winecfg.

The original COH works pretty well with wine AFAIK.

---

