---
title: "Gparted segmentation error"
date: 2005-07-31
forum: Desktop Environments
---

### Post by cotcot on 2005-07-31
I installed gparted with Synaptic.
Starting gparted does not work. A window comes up but disappears after a couple of seconds.
Starting gparted from terminal (sudo gparted) results in the message "libparted 1.6.20" and then "segmentation fault" and then it stops.
Any ideas ?

---

### Post by JurB on 2005-09-18
I have the same problem

---

### Post by ktogias on 2005-11-30
I had the exactly same error: Segmentation Fault just a few seconds after running sudo gparted

I removed the gparted package with synaptic (one could do it also with sudo apt-get install gparted- ) and downloaded the newest gparted source from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) (the file i downloaded is 'gparted-0.0.9.tar.bz2' )

The configure script stoped at varius unmet dependencies, that I had to fullfill by installing through synaptic the corresponting dev packages for some libraries. I have not recorded exactly the libs I had to install, so I can not recall them now... One missing package that I had to install and configure script failed to catch was 'libparted1.6-dev' .

After satisfying all the dependencies gparted-0.9.9 was compiled with 'make' and installed with 'make install'.

As long as I tested it, gparted-0.9.9 seems to start and function fine on my system.

PS: To compile from source in ubuntu you will need to have installed build-essensial package and maybe some other development libraries and compiler packages. See also [https://wiki.ubuntu.com/InstallingCompilers?highlight=%28compile%29](https://wiki.ubuntu.com/InstallingCompilers?highlight=%28compile%29) .
Finaly to mention that compiling from source is not the recomended ubuntu way... One should Install (and be happy with) only packages from the distribution repositories.

---

