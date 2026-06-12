---
title: "Library libGL.so.1 not found when installing dual head driver on Dell optiplex 755"
date: 2008-02-04
forum: Dell  Ubuntu Support
---

### Post by Ralph Boland on 2008-02-04
I am running Ubuntu 7.10 (dual boot mode) on a DELL optiplex 755 computer.
I am following the instructions on:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

to install the dual head graphics driver for a 256MB ATI Radeon 2400XT, Dual Monitor DVI or VGA (TV-out) full height.

Method 1 didn't work so I I am using method 2
to install the Catalyst 8.1 driver manually.
 When I get to the stage to install .deb packages I run the command:

sudo dpkg -i xorg-driver-fglrx_8.452.1-1*.deb fglrx-kernel-source_8.452.1-1*.deb fglrx-amdcccle_8.452.1-1*.deb

At this point I get the error:

Installing new version of config file /etc/xdg/compiz/compiz-manager ...
 * Starting atieventsd                                                                                                                  /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

                         [fail]

Setting up fglrx-kernel-source (8.452.1-1) ...


The rest of the command seems to run OK.

This sounds like I am missing a standard library but I don't know what one, why it's not installed or how to install it.

Advice on how to fix this problem much appreciated.
I am not quite a beginner but I am no pro so please
keep explanations simple.

Ralph Boland   
~

---

### Post by techtrickster on 2008-04-03
I'm having the same problem, following the same instructions, but with a slightly different card (radeon 3470) I got to the same part of the install and everything is ok but then i get that error.  I went and looked around in /usr/lib /usr/lib32 and /usr/lib64 and manually confirmed that the file was there it was a link but that should be sufficient right?  If I figure out a way through it i will repost here

---

### Post by TheMightyGirth on 2008-04-05
Same problem Here.

I'm wondering if it is a problem with a new version or something.

---

