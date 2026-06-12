---
title: "webcam software"
date: 2005-07-10
forum: Desktop Environments
---

### Post by dc2447 on 2005-07-10
Hi, can anyone recommend sofware to use with my Quick can pro webcam?  I am specifically looking for something that will grab pictures and make them available on a webpage.

My can is detected fine:

> davidcam@vader:~/.tvtime$ lsusb | grep Pro
Bus 001 Device 002: ID 046d:d001 Logitech, Inc. QuickCam Pro


Thanks

---

### Post by emmet on 2005-07-10
There are a number of possible solutions....

Palantir:
[http://www.fastpath.it/products/palantir/](http://www.fastpath.it/products/palantir/)

Camsource:
[http://camsource.sourceforge.net/](http://camsource.sourceforge.net/) 

These are just two examples. For home security, you could use ZoneMinder:

Zoneminder:
[ http://www.zoneminder.com/]( http://www.zoneminder.com/)  

or Motion:
[ http://www.lavrsen.dk/sources/webcam/motion_guide.htm]( http://www.lavrsen.dk/sources/webcam/motion_guide.htm) 

I hope this is useful information.

Cheers

Emmet

---

### Post by dc2447 on 2005-07-10
Thanks for the reply, I think I may be missing step in getting my cam working, using camorama  I get the following output <see attatched grab> and webcam (part of xawtv) failes to grab images.

[http://fu-1.net/~davidcam/images/snapshot2.png](http://fu-1.net/~davidcam/images/snapshot2.png)

[http://fu-1.net/~davidcam/images/webcam.jpeg](http://fu-1.net/~davidcam/images/webcam.jpeg)

Any ideas how to debug this?

---

### Post by emmet on 2005-07-11
I have a quick 'google' and there are reports that your cam has some problems with some packages and not others.

Have you tried the cam with Gnomemeeting?

I saw this:

[http://ubuntuforums.org/archive/index.php/t-3853.html](http://ubuntuforums.org/archive/index.php/t-3853.html) 

But if you use gnomemeeting, you might have to be aware of this:

[http://www.ubuntuforums.org/showthread.php?t=24827](http://www.ubuntuforums.org/showthread.php?t=24827) 

Cheers

Emmet

---

### Post by dc2447 on 2005-07-11
Hi - thanks for the post.

I now realise that my webcam isn't supported natively in the Ubuntu patched kernel and I'll need to compile in additional modules to get the quickcam pro to work :(

---

### Post by [NiCoS] on 2005-11-19
Hello,

I have the same webcam and is interesting in which module you have to compile so that the webcam works !

Up to today, I thought it was not supported at all...

Nicolas

---

### Post by mrashley on 2006-03-21
I also have a 

046d:d001 Logitech, Inc. QuickCam Pro

and I'd love it someone else has gotten their to work, if they could say how! :)

Thanks

---

### Post by [NiCoS] on 2006-03-26
[QUOTE=mrashley]I also have a 

046d:d001 Logitech, Inc. QuickCam Pro

and I'd love it someone else has gotten their to work, if they could say how! :)

Thanks[/QUOTE]

According to the search I made, it uses the nw802 module which is no longer maintained :(

[http://nw802.sourceforge.net/](http://nw802.sourceforge.net/)

So I gave up so far...

---

