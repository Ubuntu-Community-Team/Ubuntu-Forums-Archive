---
title: "Can't get"
date: 2010-03-03
forum: Gaming &amp; Leisure
---

### Post by Slantzalot on 2010-03-03
I used this link to download Nestopia
[http://rbelmont.mameworld.info/?page_id=200 ]("http://rbelmont.mameworld.info/?page_id=200")
but I have no idea how to install it. The Synaptic Package manager doesn't even show it when I try to install it. On that page that I dl'd it from it says I need to overlay a source code over it (or something like that) but I have no idea how to do that. I'm still fairly new to Ubuntu so please forgive my ignorance on this subject. Could someone help me, or provide a link to download it without having to overlay a source thing? 

Thanks!
[]("http://rbelmont.mameworld.info/?page_id=200")

---

### Post by zliefer on 2010-03-03
Grab both:
[http://prdownloads.sourceforge.net/nestopia/Nestopia140src.zip?download](http://prdownloads.sourceforge.net/nestopia/Nestopia140src.zip?download)
[http://rbelmont.mameworld.info/nst140_lnx_release_h.zip](http://rbelmont.mameworld.info/nst140_lnx_release_h.zip)

Save them to a new directory called build_Nestopia; open a Xterminal and type:

cd  build_Nestopia
unzip Ns*
unzip ns*
make
mkdir ~/.nestopia
cp *.xml  nst nstc* ~/.nestopia
cd ~/.nestopia
nst

Its a source build. Hope this helps. You also need some rom images e.g. disksys.rom <- I'll leave that part to you.
:KS

---

### Post by Slantzalot on 2010-03-03
> **zliefer said:**
> Grab both:
[http://prdownloads.sourceforge.net/nestopia/Nestopia140src.zip?download](http://prdownloads.sourceforge.net/nestopia/Nestopia140src.zip?download)
[http://rbelmont.mameworld.info/nst140_lnx_release_h.zip](http://rbelmont.mameworld.info/nst140_lnx_release_h.zip)

Save them to a new directory called build_Nestopia; open a Xterminal and type:

cd  build_Nestopia
unzip Ns*
unzip ns*
make
make install

Its a source build. Hope this helps.
:KS

Thanks for the help. I appreciate it!

---

### Post by Slantzalot on 2010-03-03
I got this message after I put in the "make" command.

Creating output directory objs
Creating output directory objs/core
Creating output directory objs/core/api
Creating output directory objs/core/board
Creating output directory objs/core/input
Creating output directory objs/core/vssystem
Creating output directory objs/linux
Creating output directory objs/linux/7zip
Creating output directory objs/linux/unzip
Creating output directory objs/nes_ntsc
Compiling source/linux/main.cpp...
/bin/sh: sdl-config: not found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make: *** [objs/linux/main.o] Error 1

No idea what it means. Any help?

---

### Post by Perfect Storm on 2010-03-03
When building from source and it complains about missing libraries, you have to look for -dev package of the complained libraries (most of the time);



> /bin/sh: sdl-config: not found
It can't find libsdl, check if libsdl1.2-dev is installed.


> No package 'gtk+-2.0' found
check if libgtk2.0-dev is installed.

> gcc: error trying to exec 'cc1plus': execvp: No such file or directory
When building on ubuntu there's a meta-package called build-essential which give you the standard tools to compile the source.

---

### Post by Slantzalot on 2010-03-04
> **Artificial Intelligence said:**
> When building from source and it complains about missing libraries, you have to look for -dev package of the complained libraries (most of the time);




It can't find libsdl, check if libsdl1.2-dev is installed.



check if libgtk2.0-dev is installed.


When building on ubuntu there's a meta-package called build-essential which give you the standard tools to compile the source.

Still trying to learn Ubuntu, could you please explain how to do that stuff? Sorry...

---

### Post by Perfect Storm on 2010-03-04
How to install them or?

You can search and find them via Synaptic Package Manager.

Or install them through the terminal;
```
sudo apt-get install libsdl1.2-dev libgtk2.0-dev build-essential
```

---

### Post by Slantzalot on 2010-03-04
Thanks! Got it up and running, I appreciate the help.

---

