---
title: "how to get pypanel working"
date: 2006-11-02
forum: Desktop Environments
---

### Post by frente69 on 2006-11-02
Ok, I have tried to install pypanel using 

sudo apt-get install pypanel

apparently the package is broken for edgy.

so then i tried following the instructions in [http://www.ubuntuforums.org/showthread.php?t=280236](http://www.ubuntuforums.org/showthread.php?t=280236)

which takes me though downloading it and installing it manually.

I get:

PyPanel requires the Python X library -
[http://sourceforge.net/projects/python-xlib/](http://sourceforge.net/projects/python-xlib/)

when i try and run sudo python setup.py install

if i try and run sudo apt-get install python-xlib it says i have the latest version.

Any one have any advice?

---

### Post by whac on 2006-11-05
Hi yeah, i have the solution.

Download and install [http://sourceforge.net/projects/python-xlib/]("http://sourceforge.net/projects/python-xlib/") and reinstall pypanel either via apt-get or the link to the alternative way you posted here.

---

### Post by frente69 on 2006-11-05
brilliant. Still wouldn't work from apt-get install pypanel but the other method works now.

Thanks!
Frente

---

### Post by FakeOutdoorsman on 2006-12-31
I was unable to get Pypanel to work on Edgy until I followed dr.zombo's instructions on kmandla's blog:
[Pypanel in Edgy not working]("http://kmandla.wordpress.com/2006/12/11/pypanel-in-edgy-not-working/")

The Edgy/Pypanel bug has been submitted and confirmed: [Bug #67337]("https://launchpad.net/distros/ubuntu/+source/pypanel/+bug/67337")

---

### Post by BLTicklemonster on 2006-12-31
Excellent. You'd think that if you install package-X, then package-X would like, oh, I don't know.. WORK, or something along those lines, right?

Thanks for the info.

---

### Post by K.Mandla on 2007-01-04
That note from dr.zombo is a work in progress, sort of. fuscia and I put together a cheesy howto [here]("http://www.ubuntuforums.org/showthread.php?t=327514"), which probably isn't much better, but gives some more ideas.

---

