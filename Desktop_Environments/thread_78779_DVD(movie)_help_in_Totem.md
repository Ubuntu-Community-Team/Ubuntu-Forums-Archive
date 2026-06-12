---
title: "DVD(movie) help in Totem"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Rahu on 2005-10-18
I just decided to switch to Ubuntu today. I was using debian 3.1 before for a server I abandoned and decided to switch this box over to my media-jigger for movies and music and such.

My problem is that when I choose the "Play Disc" option in totem I get the error "There were no decoders found to handle the stream. You may need to install the corresponding plugins." Just wondering where I might find these plugins that I need.

Thanks to any help.

---

### Post by aysiu on 2005-10-18
Would one of those plugins be libdvdcss2? If so, you may need to go [here](ftp://ftp.nerim.net/debian-marillat/pool/main/libd/libdvdcss/) to download the .deb to your desktop. Then you can ```
cd Desktop
sudo apt-get install libdvdcss2_1.2.9-0.0_i386.deb
```

---

### Post by Rahu on 2005-10-19
```
jeff@ubuntu:~/Desktop$ dir
libdvdcss2_1.2.9-0.0_i386.deb  stuff.tar.gz.tar.gz.tar.gz
jeff@ubuntu:~/Desktop$ sudo apt-get install libdvdcss2_1.2.9-0.0_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libdvdcss2_1.2.9-0.0_i386.deb

```
Any help?


ps, dont mind the stuff triple tarball. Google wouldn't let me put a binary executable on gmail, so i just had to hide it under a few layers ;)

---

### Post by manicka on 2005-10-19
libdvdcss2 can be downloaded here and installed with dpkg 

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb)

to install

sudo dpkg -i libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb

---

### Post by nico1278 on 2005-10-19
should be :

sudo dpkg -i  libdvdcss2_1.2.9-0.0_i386.deb

---

### Post by Rahu on 2005-10-19
I still get the same error.

Seems that DVDs work in VLC... kinda. It plays the intro and display the menu, but when i click play(on the dvd menu) it just stops playing :/

---

