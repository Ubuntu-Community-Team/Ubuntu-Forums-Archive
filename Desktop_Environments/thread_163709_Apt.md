---
title: "Apt"
date: 2006-04-21
forum: Desktop Environments
---

### Post by catgate on 2006-04-21
Hello,
I am trying to get to grips with Linux. I have been messing with it on and off for a few years. I was "brought up" on DOS and migrated to M$ Windows when it came out and I must say I prefer GUI to command line, and I think this is why I have never been totally happy with making a switch. The Linux commands are so much different to the DOS commands that I find it very arduous to remember them. However I was recently recommended to try Breezy Badger and so here I am. 
I wish to instal a Speedtouch DSL modem and downloaded a "driver" package from Speedtouch's web site. It is a .rpm package but the Badger says it will not play. Can some fount of knowledge please help me? How do I go about getting it on, as they say? (in language that is understandable to a BOF)
Thanks
:confused:

---

### Post by bswilson on 2006-04-21
> It is a .rpm package but the Badger says it will not play.

Let me take a shot.  You may already know, but a *.rpm file is a Redhat Package Manager file, which is a precompiled binary version of a program that will run on a Redhat system (and any other Linux/UNIX system that has right RPM tools installed).

Ubuntu is based on a different Linux distrobution called Debian.  There are multiple packaging systems for binary applications, and the one used on Debian systems are called *.deb files.  The dpkg, apt, and apt-get programs are used to download and install *.deb files. 

I'm telling you this because there is a way to convert *.rpm files to *.deb.  You will need a program called **alien** to convert these files to *.deb format.  Once you've done that, you can install the driver that you've downloaded!

More on the alien program:

[http://www.die.net/doc/linux/man/man1/alien.1.html](http://www.die.net/doc/linux/man/man1/alien.1.html)
[http://www.linuxdocs.org/HOWTOs/RPM-for-Unix-HOWTO-8.html](http://www.linuxdocs.org/HOWTOs/RPM-for-Unix-HOWTO-8.html)
(Get alien) [http://www.kitenet.net/~joey/code/alien.html](http://www.kitenet.net/~joey/code/alien.html) or [http://packages.debian.org/stable/source/alien](http://packages.debian.org/stable/source/alien)

---

### Post by aysiu on 2006-04-21
If the speedtouch .rpm is on your desktop, go to Applications > Accessories > Terminal and type ```
sudo apt-get update
sudo apt-get install alien
cd ~/Desktop
sudo alien -i *.rpm
``` [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by catgate on 2006-04-21
Thank you for that kind sir. I will have a go.

---

