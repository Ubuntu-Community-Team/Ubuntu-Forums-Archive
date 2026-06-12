---
title: "please dont make me have to give up"
date: 2007-01-08
forum: Gaming &amp; Leisure
---

### Post by jinxy1919 on 2007-01-08
I really love linux and all but i cant figure out how to get the newsest ati drivers and stuff going so i get really low frames on all my games and i cant fix this so if someone would be kind enough and i set up remote desktop connection could you get my ati drivers and stuff going for me if not im gonna have to give up on linux cause i cant do it so someone please do this for me please?:-|

---

### Post by rocknrolf77 on 2007-01-08
Have you looked here?  

[http://www.albertomilone.com/driver.html](http://www.albertomilone.com/driver.html)

---

### Post by dorcssa on 2007-01-08
It's really simple. You didn't tell which version of ubuntu you are using. Here is for dapper: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
and for edgy:[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by jinxy1919 on 2007-01-08
6.06 desktop all i know so what i do what all i need whats xorg need that? Just someone tell me what all i need links and how this is killen me i wont everything worken i love linux :( ive tryed that dapper one before i couldnt get have the **** to work the commcands and stuff well i cant get the new ones installed the 8.29

---

### Post by dorcssa on 2007-01-08
I don't really understand what you're trying to say, but what is wrong with the driver is the official dapper repos? Have you checked the links?

---

### Post by ardvark71 on 2007-01-08
Hi...

What is your ati video card exactly?

Best Regards...

---

### Post by jinxy1919 on 2007-01-08
I have an x850 pro pci express x 16 and i dont know how to get drivers going correctly and i dont know what the best drivers are i tryed the dapper guide and like the commands you put in like half them dont work i dunno what to do or how to explain someone help me please and also when i boot up and login i get a message home/.dirmc file is being ignored or something like that whats that mean and how you fix it?Also what is all the files i need to install to do the guide to setup drivers and were i get them?

---

### Post by jinxy1919 on 2007-01-08
jinxy@jinxy:~$ sudo aptitude install  xorg-driver-fglrx
E: Malformed line 40 in source list /etc/apt/sources.list (dist)
E: Malformed line 40 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
jinxy@jinxy:~$


so?

---

### Post by ardvark71 on 2007-01-08
> **jinxy1919 said:**
> I have an x850 pro pci express x 16 and i dont know how to get drivers going correctly and i dont know what the best drivers are i tryed the dapper guide and like the commands you put in like half them dont work i dunno what to do or how to explain someone help me please and also when i boot up and login i get a message home/.dirmc file is being ignored or something like that whats that mean and how you fix it?Also what is all the files i need to install to do the guide to setup drivers and were i get them?

Ok. I don't know anything about the home/.dirmc file issue but perhaps the fglrx driver will help your situation. Go to the following link and follow the instructions for your version of Ubuntu:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Read carefully!

Best Regards...

---

### Post by ardvark71 on 2007-01-08
> **jinxy1919 said:**
> jinxy@jinxy:~$ sudo aptitude install  xorg-driver-fglrx
E: Malformed line 40 in source list /etc/apt/sources.list (dist)
E: Malformed line 40 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
jinxy@jinxy:~$


so?

Type:

sudo gedit /etc/apt/sources.list

What does line 40 say?

Best Regards...

---

### Post by jinxy1919 on 2007-01-08
E: Malformed line 40 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
 get that everytime i try to run the install im going to just fresh install ubuntu then do this stuff if that dont work i dunno.

---

### Post by ardvark71 on 2007-01-08
> **jinxy1919 said:**
> E: Malformed line 40 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
 get that everytime i try to run the install im going to just fresh install ubuntu then do this stuff if that dont work i dunno.

What does line 40 say?

---

### Post by dorcssa on 2007-01-08
It would be easier, if you would post your sources.list here. Copy to the terminal : cat /etc/apt/sources.list, and post the result here please. Don't have to reinstall you're whole system coz of one bad line. ;)

---

### Post by jinxy1919 on 2007-01-08
sudo apt-get install module-assistant build-essential $ sudo apt-get install module-assistant build-essential
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package module-assistant



bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper  xo@xo-desktop:~$ bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
bash: ati-driver-installer-8.29.6.run: No such file or directory


got the first when installed tryen to install the 8.29 this is happening when i get this far what i do?

---

### Post by handy on 2007-01-09
Please don't ***make*** me have to give up? 

Is this all of a sudden **MY** responsibility? :KS

---

### Post by Sammi on 2007-01-09
jinxy1919 you really need to do one of those commands in a terminal, that dorcssa and ardvark71 asked you to do, and then post the output here.

If you don't then it is impossible for us to find out what your problem is and help you solve it for you.

We don't want you to give up. Please cooperate or we won't even have the chance to help you.

---

### Post by fx57 on 2007-01-09
> **ardvark71 said:**
> Ok. I don't know anything about the home/.dirmc file issue but perhaps the fglrx driver will help your situation. Go to the following link and follow the instructions for your version of Ubuntu:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Read carefully!

Best Regards...

ohh really.
[www.unreadedpost.com](www.unreadedpost.com)(I dont know)

---

### Post by jinxy1919 on 2007-01-09
xo@xo-desktop:~$ cat /etc/apt/sources.list

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ erse multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
xo@xo-desktop:~$

---

### Post by Ferrat on 2007-01-09
> **jinxy1919 said:**
> sudo apt-get install module-assistant build-essential $ sudo apt-get install module-assistant build-essential
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package module-assistant



bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper  xo@xo-desktop:~$ bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
bash: ati-driver-installer-8.29.6.run: No such file or directory


got the first when installed tryen to install the 8.29 this is happening when i get this far what i do?

Open Synaptic and activate Multivers and Univers respos if you haven't then try again

---

### Post by jinxy1919 on 2007-01-09
Um were at do you enable that in synamptic packacke manager

---

### Post by dorcssa on 2007-01-09
Open a terminal, and type sudo gedit /etc/apt/sources.list, and replace it with this (this way you enable the universe and multiverse repo):

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ erse multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by jinxy1919 on 2007-01-09
xo@xo-desktop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release [23.3kB]
Get:6 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release [4886B]
Get:7 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages [1889B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources [975kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [45.3kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [6017B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages [13.0kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
99% [Waiting for headers]
seems to be sticken on 99% [Waiting for headers]

---

### Post by ardvark71 on 2007-01-09
> **fx57 said:**
> ohh really.
[www.unreadedpost.com](www.unreadedpost.com)(I dont know)

Yes, really! I don't claim to know everything. And how exactly does a link to another forum site, about half of which I can't read, help us? Can you provide us a specific thread??? :rolleyes:

---

### Post by jinxy1919 on 2007-01-09
xo@xo-desktop:~$ sudo apt-get update
Err [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release.gpg
  Could not resolve 'mirror3.ubuntulinux.nl'
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Ign [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas/freenx Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Err [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas/freenx Packages
  Could not resolve 'mirror3.ubuntulinux.nl'
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Fetched 6B in 1s (5B/s)
Failed to fetch [http://mirror3.ubuntulinux.nl/dists/dapper-seveas/Release.gpg](http://mirror3.ubuntulinux.nl/dists/dapper-seveas/Release.gpg)  Could not resolve 'mirror3.ubuntulinux.nl'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release)  Unable to find expected entry  univ/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://mirror3.ubuntulinux.nl/dists/dapper-seveas/freenx/binary-i386/Packages.gz](http://mirror3.ubuntulinux.nl/dists/dapper-seveas/freenx/binary-i386/Packages.gz)  Could not resolve 'mirror3.ubuntulinux.nl'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
xo@xo-desktop:~$ sudo apt-get install module-assistant build-essential
Reading package lists... Done
Building dependency tree... Done
module-assistant is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xo@xo-desktop:~$ sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
dh-make is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
linux-headers-2.6.15-27-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xo@xo-desktop:~$ bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
bash: ati-driver-installer-8.29.6.run: No such file or directory
xo@xo-desktop:~$

Ok now everything works up untill   bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper when i run that it says no such file or directory and i downloaded it to my desktop cab someone help?

---

### Post by hikaricore on 2007-01-09
Hmm.... the ~ means you're in your "home" directory.

You need to:

```
cd Desktop
```

then you should be able to run:

```

chmod +x ati-driver-installer-8.29.6.run
./ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
```

The chmod is just incase the file is not marked as executeable on your system.
That's as far as I can help ya.  I've been able to stay safely away from ati drivers installs in my life.  :)   Good luck.

***** On a completely unrelated but interesting note, this was my 666th post on the Ubuntu forums.  =D *****

---

