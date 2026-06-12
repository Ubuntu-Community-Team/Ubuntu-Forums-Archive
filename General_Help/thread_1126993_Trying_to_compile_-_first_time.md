---
title: "Trying to compile - first time"
date: 2009-04-16
forum: General Help
---

### Post by Maheriano on 2009-04-16
There's a car PC media application I'm trying to install on my desktop before porting it into the car completely. I got the xxx.tar.gz file from Sourceforge and extracted it successfully. Here are the instructions for compiling it that I'm trying to follow:
> Install libnghost

nghost sf.net project page

    * Grab the latest libnghost-x.x.x.tar.gz off of nghost sourceforge.net download page.
    * Extract the tar ball somewhere.
    * cd path/to/libnghost-x.x.x
    * ./configure
    * install any dependencies nghost complains about
    * once you successfully configure with all the dependencies and options you want, type make
    * make install (as root) 

Install nghost

    * get the nghost source tar ball off of sf.net
    * extract
    * ./configure
    * make
    * make install (as root) 

So I download, cd and then try to configure. It gets to a certain point and gives an error:
```
...
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for xmlpp... configure: error: Package requirements (libxml++-2.6) were not met:

No package 'libxml++-2.6' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables xmlpp_CFLAGS
and xmlpp_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
So I try to install the missing package like the instructions state:
```
deemar@Chugger:~/Desktop/libnghost-2.0.2$ sudo apt-get install libxml++-2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxml++-2.6
deemar@Chugger:~/Desktop/libnghost-2.0.2$ 

```

What do I do now? There's a .deb package for 32 bit but I'm running 64 and don't feel like hacking the package just for this. I'd rather compile this one.

---

### Post by pytheas22 on 2009-04-16
Try installing the package named libxml++2.6-2.  If that doesn't work, there's one called libxml++2.6c2a that might (not sure what the difference between the two is; the first may simply be a meta package for the second).  I'm using Intrepid 64-bit, and these packages are in the default repositories.

A useful trick for situations like this is to open a terminal, type *apt-get install* + the first few letters of the piece of software you're looking for, then press tab twice and it will give you a list of packages beginning with those letters.

---

### Post by mc4man on 2009-04-16
You should use synaptic to find your deps, and not be so verbose. (or you may find nothing.

In this case just search libxml and then look for appropriate package(s) (if -devs are also available they should be installed  (screen

So in this case install libxml++2.6-dev (will also install libxml++2.6.2 if not already. Most -devs depend on a similarly named lib

If in the course of configuring or building an error points to l<whatever>, turn that l into lib

If not already installed go (for basic build tools. libs
```
sudo apt-get install build-essential
```

---

### Post by Maheriano on 2009-04-16
Got it, thanks. Now it's saying the same thing for x11 but I can't find any x11 packages in Add/Remove Programs.

---

### Post by pytheas22 on 2009-04-16
X11 is what draws the graphics on your screen, and is definitely already installed if you're using normal Ubuntu.  Maybe it needs x11-dev instead, or maybe the configure script is confused about the location of the x11 libraries.  What is the exact error message?

---

### Post by Maheriano on 2009-04-16
> ...
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for xmlpp... yes
checking for x11... configure: error: Package requirements (x11) were not met:

No package 'x11' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables x11_CFLAGS
and x11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

deemar@Chugger:~/Desktop/libnghost-2.0.2$ 


Is this good or bad? I'm running a fully up to date AMD64 8.1 desktop version. I could try it on 9.04 on my laptop if I have to but I'd rather not.

---

### Post by mc4man on 2009-04-16
One more time - use synaptic package manager, not add-remove (System -> admin..-> Synaptic package manager

(use the 'search' button, not the 'quick search' box

---

### Post by pytheas22 on 2009-04-16
There's a package called libx11-6 which may be what it's looking for.  If not, experiment with the other X11-related packages.  If they still fail, let us know; maybe you need to use the PKG_CONFIG_PATH variable to tell it where the files are located (although on a popular distribution like Ubuntu, this should rarely be necessary).

---

### Post by Maheriano on 2009-04-16
> **pytheas22 said:**
> There's a package called libx11-6 which may be what it's looking for.  If not, experiment with the other X11-related packages.  If they still fail, let us know; maybe you need to use the PKG_CONFIG_PATH variable to tell it where the files are located (although on a popular distribution like Ubuntu, this should rarely be necessary).
Will do, I'll post back tonight, thanks.

> **mc4man said:**
> One more time - use synaptic package manager, not add-remove (System -> admin..-> Synaptic package manager

(use the 'search' button, not the 'quick search' box
Syn-ap-tic? WTF? Why are there 2 ways of downloading things to my machine? I'll look at this thing later anyway, thanks.

---

