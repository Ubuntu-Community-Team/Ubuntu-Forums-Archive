---
title: "Goofy Dell"
date: 2005-10-20
forum: Desktop Environments
---

### Post by Big Red on 2005-10-20
I have an inspiron 5150 laptop with the broadcom wireless card and the xgi volari video card. I have two problems.

The first is that the wireless card doesn't work. I've done some research, and I know that the drivers can be made to work, but I haven't found any good instructions on how to do that (I'm new to Linux). 

The second is that when it boots to linux, the colors are all off. Once in Linux, if I change the resolution, this problem fixes itself, and stays fixed even if I change the resolution. 

Any help with either of these would be greatly appreciated. I'm really excited to start learning Linux, but these have both really limited my use of it thus far.

---

### Post by chanders on 2005-10-22
I am not sure about the colors being off, but to get your wireless card working, you need to install ndiswrapper. This essentally "Wraps" itself around the windows drivers to provide an interface to the card.

A quick search will yield some valuable information in setting it up.... 
It souldnt be too difficult. You can do it, and welcome to Ubuntu! :D

First place to start...
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

---

### Post by Hairy_Palms on 2005-10-22
i have a inspiron 5160, same i think except the gfx card, the wireless works great with ndiswrapper. though it took me a lot of googling to figure out how to use ndiswrapper wish i knew about the guide chanders posted,
try running sudo dpkg-reconfigure xorg-xserver to fix ur gfx,
also if that doesnt work try editting xorg.cong.

---

### Post by chanders on 2005-10-22
Hey, hairy palms, I think you meant xorg.con**f** ;)

---

