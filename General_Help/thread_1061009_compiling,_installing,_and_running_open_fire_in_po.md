---
title: "compiling, installing, and running open fire in powerpc"
date: 2009-02-05
forum: General Help
---

### Post by pesqair on 2009-02-05
Does anyone know how, or if it is possible to compile, install, and run open fire on ubuntu powerpc?

I followed instructions for building the source from the open source website but I cant get openfire started. 

thank you

```
pesqair@ubuntu:~/openfire_src/src$ ls
bin   database  java     plugins    security  test   web
conf  i18n      javadoc  resources  spank     tools
pesqair@ubuntu:~/openfire_src/src$ cd bin
pesqair@ubuntu:~/openfire_src/src/bin$ ls
extra  openfire.bat  openfirectl  openfire-dev.bat  openfire.sh
pesqair@ubuntu:~/openfire_src/src/bin$ ./openfire.sh
ls: cannot access /usr/java/j*: No such file or directory
Unable to access jarfile /home/pesqair/openfire_src/src/lib/startup.jar

```

---

### Post by taurus on 2009-02-05
Does it require you to have java running on your machine first?

```
java -version
```

---

### Post by pesqair on 2009-02-05
yes

```
pesqair@ubuntu:~/openfire_src/build$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Core VM (build 1.6.0_0-b12, interpreted mode)

```

---

### Post by taurus on 2009-02-05
Maybe it wants the Sun's version instead of the OpenJDK!

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by pesqair on 2009-02-05
i think I should add it asks for ```
Unable to access jarfile /home/pesqair/openfire_src/src/lib/startup.jar
```

and

```
pesqair@ubuntu:~/openfire_src/src$ ls
bin   database  java     plugins    security  test   web
conf  i18n      javadoc  resources  spank     tools
pesqair@ubuntu:~/openfire_src/src$ 
```

there is no lib directory

---

### Post by pesqair on 2009-02-05
i'll try that. thanks

---

### Post by pesqair on 2009-02-05
```
pesqair@ubuntu:~/openfire_src/src$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
[sudo] password for pesqair: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sun-java6-jre
E: Package sun-java6-bin has no installation candidate

```

```

pesqair@ubuntu:~/openfire_src/src$ sudo apt-get install sun-java6-jreReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not installable or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not installable
E: Broken packages
pesqair@ubuntu:~/openfire_src/src$ sudo apt-get install sun-java6-jre sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sun-java6-jre
E: Package sun-java6-bin has no installation candidate

```

---

### Post by taurus on 2009-02-05
Post your /etc/apt/sources.list.  Make sure you have all the repos enable in /etc/apt/sources.list.

---

### Post by pesqair on 2009-02-05
```
# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release powerpc+ps3 (20081030)]/ intrepid main restricted

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release powerpc+ps3 (20081030)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu intrepid universe
deb http://ports.ubuntu.com/ubuntu-ports/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ intrepid-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://ports.ubuntu.com/ubuntu-ports/ intrepid-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ intrepid-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ intrepid-security universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ intrepid-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ intrepid-security multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ intrepid-security multiverse

```

---

### Post by pesqair on 2009-02-05
*bump*

---

### Post by pesqair on 2009-02-05
Bump

---

### Post by taurus on 2009-02-05
Open synaptic and at the Search field, type in **sun-java6-bin** and post the screenshot of that window.

---

### Post by pesqair on 2009-02-05
i have no monitor at that computer. i am ssh-ing in from my mac.

---

### Post by taurus on 2009-02-05
Did you install the x86_64 version?

```
uname -m
```

---

