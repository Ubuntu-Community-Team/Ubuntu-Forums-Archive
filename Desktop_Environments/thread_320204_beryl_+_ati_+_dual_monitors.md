---
title: "beryl + ati + dual monitors"
date: 2006-12-16
forum: Desktop Environments
---

### Post by overdose on 2006-12-16
Hello all, just a quick question involving the installation of Beryl on ubuntu 6.10:  I am using an ATI 9800 pro with dual monitors.  I followed the walkthrough found here [http://all.ofthe.info/node/23]("http://all.ofthe.info/node/23") but after starting beryl-manager I receive the following error: 

[COLOR="DarkOrange"]overdose@elhefe:~$ beryl-manager 
overdose@elhefe:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
compiz.real: GLX_SGIX_fbconfig is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0[/COLOR]

Has anybody come across this before?  And if so, what is the solution?  

Thanks in advance!

---

### Post by scottDkoDer on 2006-12-29
Using proprietary or open source? Try lowering your resolution settings in xorg.conf.

---

