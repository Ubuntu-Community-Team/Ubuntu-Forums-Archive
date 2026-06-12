---
title: "checking for KDE... configure: error:"
date: 2006-06-24
forum: Desktop Environments
---

### Post by w1z4rd on 2006-06-24
Im trying to install [kdeextragear]("http://yu.samba.org/kde/snapshots/kdeextragear-addons.tar.bz2")  so I can get skype installed on kopete, and since I cant find it in my packet manager, im downloading it and installing it from source. 

I first got this error when typing ./configure :

```
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log
```

So i went to the packet manager, and installed everything that said qt3 and qt4. However, when I type the ./configure command I now get to a point Im not to sure what to do:

> checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log

---

### Post by raptros-v76 on 2006-06-24
you need to get the libqt4 stuff. search in your package manager for qt4.

---

### Post by w1z4rd on 2006-06-24
[QUOTE=raptros-v76]you need to get the libqt4 stuff. search in your package manager for qt4.[/QUOTE]


nope, installed everything i could to do with qt... not working... :(

---

### Post by claydoh on 2006-06-24
Have you installed the kdelibs4-dev package? that should also install any missing qt *-dev lib packages as well, which *should* get you going

---

### Post by w1z4rd on 2006-06-24
ive tried that a lot, im on the verge of completely removing kubuntu, cause i can get access to half the cool stuff out there :(

This is the error I get:
```
w1z4rd@b0x:~/src/kdeextragear-addons-547270$ sudo apt-get install kdelibs4-dev
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs4-dev: Depends: kdelibs4c2a (= 4:3.5.2-0ubuntu18) but 4:3.5.3-0ubuntu0.1 is to be installed
                Depends: kdelibs-bin (= 4:3.5.2-0ubuntu18) but 4:3.5.3-0ubuntu0.1 is to be installed
                Depends: libarts1-dev (>= 1.5-rc1) but it is not going to be installed
E: Broken packages
w1z4rd@b0x:~/src/kdeextragear-addons-547270$    
```

and if i try install the "missing" dependencies..

```
w1z4rd@b0x:~/src/kdeextragear-addons-547270$ sudo apt-get install kdelibs4c2a
Reading package lists... Done
Building dependency tree... Done
kdelibs4c2a is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
w1z4rd@b0x:~/src/kdeextragear-addons-547270$ sudo apt-get install kdelibs-bin
Reading package lists... Done
Building dependency tree... Done
kdelibs-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by rupy on 2006-06-24
What about re-installing all the "broken" packages? Also try googling 'apt broken packages'
[http://www.google.co.za/search?q=apt+%22Broken+packages](http://www.google.co.za/search?q=apt+%22Broken+packages)

---

### Post by claydoh on 2006-06-24
"did you run apt-get update" and "apt-get upgrade"? It seems you may have added the (non-standard) KDE 3.5.3 repo to your sources.list?

---

