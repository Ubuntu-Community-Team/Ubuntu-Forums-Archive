---
title: "OpenOffice Base Wizards Broken"
date: 2006-01-29
forum: Desktop Environments
---

### Post by william_nbg on 2006-01-29
My wife upgraded, (using the Automatix script) her OO to version 2 on a fresh Breezy install. We upgraded to the newest version of Java from sun and now all OO apps including Base are running much faster.

The only problem is none of the wizards in base will work. They either don't work at all, or hang up. I found something about it on the OO forum regarding maybe there are still files left over from 1.5 in the system could be doing this.

We'd appreciate any suggestions, on fixing the problems or how to clean out all files from the older version. 

Thanks.

---

### Post by william_nbg on 2006-01-30
I found another entry on the OO forum who uses Kubuntu and upgraded to openoffice using the Automatix script and has the same problem with the wizards. 

Does anyone know how to completly wipe OO and all files and databases and everything from the system for a fresh OO2 install??

---

### Post by william_nbg on 2006-02-01
OK, I fixed the problem and now our OpenOffice on both computers is working just great - wizards and all.

Something with upgrading from the 1.9 to the 2 from the repos. didn't quite work for us.

I simply uninstalled all OO components from Synaptic, and then reinstalled everything using the .dep's which I downloaded online somewhere (sorry can't find the link right now, if anyone needs it let me know and I'll look againd).

---

### Post by MartinG on 2006-02-01
Tell me, please! I've been watching this thread hoping for an answer.

---

### Post by william_nbg on 2006-02-01
What exactly do you need to know??

Like I said in my last post:

I just opened Synaptic, and uninstalled all openoffice apps and stuff. Then I downloaded the .deb files from here:

[http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/)

extracted them to a temp folder (you'll have a lot of .deb files) so

In terminal: cd to the temp folder and type in:

sudo dpkg -i *.deb

And it should install.

---

### Post by MartinG on 2006-02-01
Thanks, it was just the link I wanted.

---

