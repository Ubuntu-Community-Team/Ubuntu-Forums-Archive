---
title: "build pikdev on Xorg?"
date: 2006-01-03
forum: Desktop Environments
---

### Post by macsimski on 2006-01-03
Hello all,

I still am trying to build pikdev [http://pikdev.free.fr](http://pikdev.free.fr) on my kubuntu breezy ix86 box. 

./configure quits on not finding the X11 headers. it expects to find Xfree86-devel headers, but this machine runs Xorg. Is there a way to use the headers of Xorg?

I think that adding a path to my PATH variable would do the trick, but wich path?

or am I wrong and sould a package be installed? I was unable to locate a Xorg headers package with dselect on my machine

anyone?

---

### Post by lurker on 2006-01-03
I just found this on another thread.  Try the package **x-window-system-dev**
It worked when I compiled xine.

Here's a link to the other thread.
[http://www.ubuntuforums.org/showthread.php?t=78973&highlight=xfree86-devel](http://www.ubuntuforums.org/showthread.php?t=78973&highlight=xfree86-devel)

---

### Post by macsimski on 2006-01-04
That worked for me. hurray! 

Now i will inform the original developer of pikdev what to do to build it on kubuntu 5.10

---

