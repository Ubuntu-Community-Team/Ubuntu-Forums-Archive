---
title: "compiling xmame for hoary on amd64"
date: 2005-09-03
forum: Gaming &amp; Leisure
---

### Post by rah on 2005-09-03
I'm trying to compile xmame 0.99 on a AMD64 running Hoary.  When I do a Make, I get a bunch of warnings and errors, and the last line is:

make: *** [xmame.obj/config.0] Error 1

I don't even know where to begin looking in terms of how to fix this.  A few months ago, I successfully compiled xmame 0.96 on a Pentium 4 running SUSE 9.1.  Can anyone help to point me in the right direction?

Alternatively, is there a repository somewhere where a recent version of xmame built for AMD64 can be downloaded?

---

### Post by rafakl on 2005-09-04
search if its a port in the ubuntu repositories:

sudo apt-get update

sudo apt-cache search xmame

---

### Post by rah on 2005-09-04
Hi again. :) 

The only MAME I can see in the repositories is version 0.86-1.  I'd really like to have something a bit newer.

I searched the backports repositories listed in the unofficial guide, as well as the unofficial AMD64 repositories and the Marillat Debian repositories, by the way.

Thanks for your response though.  I appreciate it.

EDIT:  Okay, I got it to work.  I downloaded a RPM from here:

[http://stentz.freshrpms.net/](http://stentz.freshrpms.net/)

Then I used alien to convert it to a deb package and I used dpkg to install it.  Once it was up and running, I had some trouble getting it to see my gamepad -- I needed to add the line ```
joydevname /dev/input/js0
``` to the xmamerc file -- and I need to do ```
killall esd
``` before running the program if I want to hear any sound, but in short, it's working. :grin:

---

