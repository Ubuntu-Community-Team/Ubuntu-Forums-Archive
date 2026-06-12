---
title: "Need help to get lirc working"
date: 2009-04-03
forum: General Help
---

### Post by teropita on 2009-04-03
I have been trying to get lirc working for some time now.

I have been following the guide here 
[http://xbmc.org/forum/showthread.php?t=40290]("http://xbmc.org/forum/showthread.php?t=40290")

as I have an Imon VRF with IR reciever.

I get stuck because there is an issue with DKMS

after the command

sudo dpkg-reconfigure lirc-modules-source

I get

Error!  Build of lirc_imon.ko failed for: 2.6.27-11-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.3/build/ for more information.
Installing initial module

Error! Could not locate lirc_atiusb.ko for module lirc in the DKMS tree.
You must run a dkms build for kernel 2.6.27-11-generic (i686) first.
Done.

All that there is in the log is:

DKMS make.log for lirc-0.8.3 for kernel 2.6.27-11-generic (i686)
Sat Apr  4 16:20:00 NZDT 2009
/var/lib/dkms/lirc/0.8.3/build

if I run the command lircd -v

I get lircd 0.8.5-CVS

can anyone help me to progress this?

---

