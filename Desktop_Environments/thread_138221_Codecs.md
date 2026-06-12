---
title: "Codecs"
date: 2006-03-01
forum: Desktop Environments
---

### Post by Luis De Freitas on 2006-03-01
Damn I hate to ask about it but i couln't find no answer for this...

The mplayer throw me a massega everytime i try to open a internet vidio, and if i try to install it says something like this:

Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

Please help.

---

### Post by Perfect Storm on 2006-03-01
```
sudo gedit /etc/apt/sources.list
```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```
sudo apt-get update
sudo apt-get install w32codecs
```

If it's DVD you want to play then also
```
sudo apt-get install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3
```

You might enable universe and multiverse before the commands works.

---

### Post by Luis De Freitas on 2006-03-01
The same problem...

I did step by step and I still have the error message???????

Thanks

---

### Post by Perfect Storm on 2006-03-01
Are you on an i386 x86 system or another like the 64bit system?

---

### Post by Luis De Freitas on 2006-03-01
Well am not too sure about it :-#  

I've got Dell
Centrino 2.0
DVD-RW
1Gb Mem
80 Gb HD

---

### Post by Luis De Freitas on 2006-03-01
Actually if a try to watch a vidio on my Hd i can see it, I only have the problem with internet...

Thanks

---

### Post by Luis De Freitas on 2006-03-01
please help

---

### Post by jerinjoy on 2006-03-05
> 
add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```
sudo apt-get update
sudo apt-get install w32codecs
```

If it's DVD you want to play then also
```
sudo apt-get install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3
```

You might enable universe and multiverse before the commands works.

I have the same problem. I added the links to my sources file, ran update and get w32codecs, it says:
jerinjoy@jj-ubuntu-sys:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

jerinjoy@jj-ubuntu-sys:~$ sudo apt-get install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3
Reading package lists... Done
Building dependency tree... Done
libdvdnav4 is already the newest version.
E: Couldn't find package libdvdplay0


I've been trying to install the codecs and get the dvd player to run for sometime now.

---

### Post by Perfect Storm on 2006-03-05
Try with another mirror check here: [http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

I've checked my sourcelist, and it the works perfect. Make sure you have uncomment them all.

My sourcelist:
(only works for breezy i386)

> deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

## Backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

## Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## PLF testing package
deb [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free

## BMP Plus
deb [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx/) breezy/


---

### Post by jerinjoy on 2006-03-05
thanx for your help. i got it working using the synaptic package installer.

for everyone else, the quick fix is:

System ->Administration -> Synaptic Package Manager
In the Synaptic window:
Settings -> Repositories (then under settings leave 'Show Disabled Software Sources'
In the Repositories window, make sure you check 'Ubuntu 5.10 (Binary) Community Maintained. You can check out the other repositories available and then check them too if you like. Click OK, the packages available from Universe will be shown.
You can now use search to install any package you like. I installed libdvdcss which allows you to play DVD's. Also Install the ogle, ogle-gui players to play your DVD's.
You can use the search option for any other package also.

Side Note: I guess the reason these repositories are not enabled by default is that the software available can be used for copyright infringement. 
Read:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

