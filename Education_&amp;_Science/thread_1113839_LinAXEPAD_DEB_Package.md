---
title: "LinAXEPAD DEB Package"
date: 2009-04-02
forum: Education &amp; Science
---

### Post by tdm on 2009-04-02
I have created a DEB package for the LinAXEPAD programming software for programming PICAXE chips via a serial/usb port. :D

[B]It can be downloaded _[[SIZE=4]here[/SIZE]]("http://www.esnips.com/doc/fbc27679-d9ae-4bda-b400-35eb12ff5ba3/LinAXEPAD-0.1.4")_. :KS

[/B]Please note I am new to DEB packages and have only created**_ [one before]("http://ubuntuforums.org/showthread.php?t=730598") _**so there are some issues:

[LIST]
[*]Only tested on Ubuntu 8.10
[*]No menu items (must run "linaxepad")
[*]No dependency checking (see below)
[/LIST]
I have not added dependency to the package checking but here is what is required: :p

[LIST]
[*]x86 distribution
[*]GTK+ 2.8 or higher
[*]CUPS
[*]libstdc++.so.6
[/LIST]
Have fun!
;)

*LinAXEPAD 0.1.4 screenshot attached.*

---

### Post by lolgeek on 2009-06-15
Cool thanks. I was having issues with the one that is downloaded from rev-ed website. This one seems to work a lot better. :) Keep up the great work!

---

### Post by acidblue on 2009-06-21
Too bad this dosn't work on x86_64 bit systems.
It would be nice if developers would make 64 bit versions as well.
It's frustrating to find a good app, like this one, only to discover
there is'nt a 64 bit one.:mad:

---

