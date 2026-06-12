---
title: "Compiz Updates?"
date: 2008-03-28
forum: Desktop Effects &amp; Customization
---

### Post by Het Irv on 2008-03-28
Okay, so I think I have missed a memo somewhere.  When I am online I am seeing new Compiz Plugins being used, but I don't have them.  So I went online to download them, and I can find where to get them from.  I have CCSM 0.5.2, and that is the only thing I have installed relating to Compiz.

I really just want to see if I can crash my Laptop with the newer plugins.

---

### Post by luisromangz on 2008-03-28
Try using this repo:

deb [http://kwatrow.nl/repo](http://kwatrow.nl/repo) Gutsy compiz-fusion-git

It allows me to use a pretty recent Compiz Fusion version in my laptop.

---

### Post by Het Irv on 2008-03-28
That works great, now I have to get the plug-ins.

I am having trouble getting the Plug-in's
If I type ```
git://git.opencompositing.org/fusion/plugins/atlantis
```
I get a "file not found error"

---

### Post by luisromangz on 2008-03-29
The atlantis plugin is in the packages in the repository I pointed you before...

---

### Post by Smatt454 on 2008-03-29
while updating compiz with that repo i got 

> Reading package lists... Done
W: GPG error: [http://kwatrow.nl](http://kwatrow.nl) Gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A9D6542CFC16ED1D
W: You may want to run apt-get update to correct these problems


EDIT:
I WAS running apt-get update when i got this error o_O

---

### Post by Smatt454 on 2008-03-30
got it to work, but when i try to run  
compiz --replace
```
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libcrashhandler.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'crashhandler'
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libextrawm.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'extrawm'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libsplash.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'splash'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libbench.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'bench'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libfirepaint.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'firepaint'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libreflex.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'reflex'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libgroup.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'group'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libaddhelper.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'addhelper'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libcubecaps.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'cubecaps'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libcubereflex.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'cubereflex'
smatt454@kubuntu:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

