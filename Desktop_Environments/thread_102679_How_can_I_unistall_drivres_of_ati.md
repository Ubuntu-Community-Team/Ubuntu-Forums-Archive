---
title: "How can I unistall drivres of ati ?????"
date: 2005-12-12
forum: Desktop Environments
---

### Post by clapton on 2005-12-12
I've got the ati-driver-installer-8.19.10-i386 installed and I want to install the new drivers, how I can uninstall this driver?

Thx

---

### Post by Sokraates on 2005-12-12
How did you install the driver in the first place?

Usuallly you should have some .deb-file you installed. The problem is, that you normaly do some tweaking her and there.

If you post us the steps you've taken (or a link to the HOW-TO you've used), it would aid us helping you.

---

### Post by clapton on 2005-12-12
I use this "wiki" formula.

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by Sokraates on 2005-12-13
Take a look [here](http://ubuntuforums.org/showpost.php?p=423584).

As far as I understand, first you should do

```
sudo dpkg-reconfigure xserver-xorg #select the "ati" module
```

then

```
sudo apt-get remove fglrx-kernel-$(uname -r)
```

After that, you will have to install the new driver as described and don't fotget to backup your xorg.conf, just in case.

good luck. ;)

---

### Post by rhys_jones on 2005-12-13
I'm glad someone else is having problems besides me.  My driver was just a generic ATI and didn't give me the higher resolution I wanted.

---

### Post by clapton on 2005-12-13
I've done this things, and dind't work :(

---

### Post by Sokraates on 2005-12-14
Can you specify what exactly doesn't work?

Please post waht you did and any error messages displayed.

---

### Post by clapton on 2005-12-25
```
==================================================
Generating package: Ubuntu/breezy
/tmp/fglrx ~/Desktop/fglrx-install
~/Desktop/fglrx-install
Removing temporary directory: fglrx-install
marco@2l33t4U:~/Desktop$ sudo dpkg -i ./xorg-driver-fglrx_8.20.8-1_i386.deb
dpkg: erro ao processar ./xorg-driver-fglrx_8.20.8-1_i386.deb (--install):
 não pode aceder ao arquivo: Arquivo ou diretório não encontrado
Foram encontrados erros enquanto processava:

```
On english.
There's an error on processing 'cause that can't found file or folder "./xorg-driver-fglrx_8.20.8-1_i386.deb ".

I hope that someone can Answer to me, it's x-mas :P

---

### Post by petri on 2005-12-26
Seems like you have the same problem I did. Take a look at the [howto]("http://ubuntuforums.org/showpost.php?p=423584") again, mlomker has updated it for us newbies.

The update is something like this: 
Quote:
Originally Posted by petri
"For me the DEB files are always created in the current directory, but some people have to change to /tmp to find them." on your

It wasn't you--that was a recent update to the how-to since a number of people were having that problem. I'm not sure why I can't recreate that problem (I have six Ubuntu machines at work and none of them do that).Quote:

You can read it by yourself at [discussion]("http://ubuntuforums.org/showthread.php?t=76116&page=53") to the howto. Works nice for me. At last! :D

---

