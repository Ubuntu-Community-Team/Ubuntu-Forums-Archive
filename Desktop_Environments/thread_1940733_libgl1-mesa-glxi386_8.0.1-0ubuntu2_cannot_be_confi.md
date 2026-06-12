---
title: "libgl1-mesa-glx:i386 8.0.1-0ubuntu2 cannot be configured because libgl1-mesa-glx:amd6"
date: 2012-03-14
forum: Desktop Environments
---

### Post by DavidSommen on 2012-03-14
Hey guys,

I recently upgraded my main computer to Precise because on my laptop and my (older) pc it worked perfectly, as if it wasn't a beta version.

Everything went ok, but after the most recent upgrade there is a problem with the package libgl1-mesa-glx.

Output from the terminal if I use sudo apt-get -f install:

```
sommen@sommen:~$ sudo apt-get -f install
[sudo] password for sommen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgl1-mesa-glx:i386
The following packages will be upgraded:
  libgl1-mesa-glx:i386
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0 B/137 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libgl1-mesa-glx:i386 (--configure):
 libgl1-mesa-glx:i386 8.0.1-0ubuntu2 cannot be configured because libgl1-mesa-glx:amd64 is in a different version (8.0.1-0ubuntu4)
dpkg: error processing libgl1-mesa-glx (--configure):
 libgl1-mesa-glx:amd64 8.0.1-0ubuntu4 cannot be configured because libgl1-mesa-glx:i386 is in a different version (8.0.1-0ubuntu2)
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of libglu1-mesa:
 libglu1-mesa depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:i386 which provides libgl1 is not configured yet.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
dpkg: error processing libglu1-mesa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglu1-mesa:i386:
 libglu1-mesa:i386 depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:i386 is not configured yet.
  Package libgl1-mesa-glx:i386 which provides libgl1 is not configured yet.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
dpkg: error processing libglu1-mesa:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on libgl1-mesa-glx | libgl1; however:
  PackageNo apport report written because the error message indicates its a followup error from a previous failure.
                                    libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:i386 which provides libgl1 is not configured yet.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgl1-mesa-glx:i386
 libgl1-mesa-glx
 libglu1-mesa
 libglu1-mesa:i386
 unity
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

This means I cannot update my system anymore, because of the dependencies...

Can anyone think of a workaround or fix of this problem? I don't think it's necessarily a universal bug, more a specific problem for my system? Not sure though..

---

### Post by DavidSommen on 2012-03-14
I solved it myself using this method:

```

dpkg --force-depends --purge libgl1-mesa-glx
sudo apt-get -f install

```
at which point only unity was still "broken". I repeated the process, like this:

```

dpkg --force-depends --purge unity
sudo apt-get -f install

```
it reinstalled the unity package and everything is fine again!

---

### Post by nasenmann72 on 2012-03-20
Thanks!

I got nearly the same issue and could resolve it with you solution. Thanks for reporting back!

Der Nasenmann

---

### Post by SelbyRowleyCannon on 2012-08-07
Man, thanks so much for this fix! I would have stayed with a broken system if it wasn't for this! :D

---

