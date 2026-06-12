---
title: "[SOLVED] Need help installing Baghira"
date: 2007-07-24
forum: Desktop Environments
---

### Post by mastercoderx on 2007-07-24
Hi everyone, I posted this in "General Help" before, but I didn't get any replies, so I'm posting it here:


Hi everyone

I'm using Kubuntu 7.04.

I'm trying to install [Baghira]("http://en.wikipedia.org/wiki/Baghira"), using [this guide]("http://baghira.sourceforge.net/OS_Clone-en.php").


I think I did everything right from the beginning to "Compile the sources and install Baghira".

When I get to "Compile the sources and install Baghira", I cd to the baghira directory, and I enter the command ```
make -f Makefile.cvs
``` in the terminal.


However, instead of giving proper output, it gives this output: ```
:~/baghira$ make -f Makefile.cvs
This Makefile is only for the CVS repository
This will be deleted before making the distribution

./admin/cvs.sh: 651: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2

``` 


However, as you can see from the attached screenshot, I have both autoconf and autoconf2.13 installed, and autoconf is version 2.61-3.


Please tell me what I am doing wrong and how I can install Baghira.

I'll be very thankful for any help you can give me.

---

### Post by jcarlock on 2007-07-25
Now I am not a pro, but I would recommend checking that that the shell scripts, makefile scripts aren't referencing a autoconf location for a different distro.  Basically if this were originally a redhat source and you try to compile in (k)ubuntu it may have a direct path to your autoconf which may be different in the original distro the source was written for.

You may also want to try running it as root, or atleast sudo.

JC

---

### Post by mastercoderx on 2007-07-26
Hi jcarlock

Thank you for replying. I'm very thankful for your help.

However, I don't need to compile Baghira anymore, as I've found a package called kwin-baghira in the repositories, and it seems to work alright.

mastercoderx

---

### Post by menacers on 2007-12-07
i was experiencing the same problem. Now my only problem left is that when i try to loa the baghira starter applet, i get an error:

The Baghira Starter applet could not be loaded. Please check your installation.

This is not a very descriptive error!  I'm runninf Kubunto which i jsut downloaded and installed from ubuntu website.

Hope someone has experienced this problem before and can help!

---

