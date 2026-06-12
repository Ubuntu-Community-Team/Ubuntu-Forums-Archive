---
title: "trying to install cinnamon into 13.04 32bit"
date: 2013-06-18
forum: Desktop Environments
---

### Post by Kevin h II on 2013-06-18
Hi im new so dont be to harsh mates

but i have had ubuntu since feb 17 and i love coming here as i gain knowledge yet i have this problem i love testing out the enviroments yet this happens when i try to install cinnamon nemo 

Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Fetched 520 kB in 3min 9s (2,744 B/s)
W: GPG error: [https://download.01.org](https://download.01.org) Ubuntu Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8D8847D52F4AAA66
W: GPG error: [https://download.01.org](https://download.01.org) Ubuntu Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8D8847D52F4AAA66
W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/raring/main/source/Sources](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/raring/main/source/Sources)  404  Not Found




and on top of that my network is monitored and the word games radio etc are blocked from access

so if many of you could help much ablodged and im not afraid to use terminal i just hate how slow ubuntu software center is

thank you and please reply thanks mates for reading. kevin

---

### Post by hamishmb on 2013-06-18
Okay, please post the output of "lsb_release -a" from the terminal, without the quotes.
Also, please post the full output of the command you're running.

Thanks

---

### Post by cincinnatus13 on 2013-06-18
[http://www.ubuntugeek.com/how-to-install-cinnamon-1-8-on-ubuntu-13-04.html](http://www.ubuntugeek.com/how-to-install-cinnamon-1-8-on-ubuntu-13-04.html)

Easier and gets you 1.8.

---

### Post by Kevin h II on 2013-06-18
kah@99kahartman:~$ sudo apt-get install cinnamon nemo
[sudo] password for kah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 cinnamon : Depends: libgjs0-libmozjs185-1.0
            Recommends: cinnamon-screensaver but it is not going to be installed
            Recommends: gir1.2-gjsdbus-1.0 but it is not installable
E: Unable to correct problems, you have held broken packages.
kah@99kahartman:~$ 

thats all mate sorry

---

### Post by Kevin h II on 2013-06-18
ey mate i am using that to get cinnamon. those are the instructions im going off of. good try though

---

### Post by SuperFreak on 2013-06-18
> **cincinnatus13 said:**
> [http://www.ubuntugeek.com/how-to-install-cinnamon-1-8-on-ubuntu-13-04.html](http://www.ubuntugeek.com/how-to-install-cinnamon-1-8-on-ubuntu-13-04.html)

Easier and gets you 1.8.

+1

---

### Post by cincinnatus13 on 2013-06-18
Hmm, didn't know you were going for it.

I recommend a sudo apt-get -f install to try and meet the dependencies but holding broken packages is something I'm not altogether very familiar with.
Worth a shot though. That and sudo apt-get autoremove

---

