---
title: "going from fglrx -&gt; radeon drivers?  composite broken"
date: 2007-02-11
forum: Desktop Environments
---

### Post by shrndegruv on 2007-02-11
Hello

I installed the fglrx driver, but want to migrate back to radeon driver.  Ive got it mostly working, but for some reason composite extension doesnt want to work.   Here's what I can tell you

1.  I am specifying the correct driver in my xorg.conf.
2.  lsmod reveals that the radeon driver is loaded.
3.  the dri, dbe, glx modules are loaded in xorg.conf.
4.  DRI mode is 0666 and extenstions has composite enabled.

glxinfo reveals direct rendering isnt happening.

what gives?

I think when I went to fglrx some underlying lib got overwritten.  Please help me get back to a working radeon...thanx...

---

### Post by shareMenaPeace on 2007-02-11
Maybe recheck these guide, depending on your ubuntu

Dapper guide
[http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html](http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html)

Edgy guide
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

---

### Post by shrndegruv on 2007-02-11
that guide doesnt say anything about migrating drivers....

thanx for playing though. ;)

anyone?

---

### Post by shrndegruv on 2007-02-16
the answer was in the migrating to fglrx guide -- at the bottom it says to completely remove the fglrx drivers, which was the key.  not enough to just to specify the radeon driver in xorg.conf...

---

