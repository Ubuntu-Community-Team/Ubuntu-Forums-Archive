---
title: "out of luck?"
date: 2005-09-09
forum: Desktop Environments
---

### Post by war-totem on 2005-09-09
```
The following packages have unmet dependencies:
  fluxbox: Depends: menu (>= 2.1.19) but it is not going to be installed
           Depends: libxinerama1 but it is not installable
E: Broken packages
``` 

is what i get when trying to apt-get fluxbox, and i get this when trying to install the .deb package:

```
root@ubuntu:~/debs # dpkg -i fluxbox_0.9.13-1_i386.deb
Selecting previously deselected package fluxbox.
(Reading database ... 62683 files and directories currently installed.)
Unpacking fluxbox (from fluxbox_0.9.13-1_i386.deb) ...
dpkg: dependency problems prevent configuration of fluxbox:
 fluxbox depends on menu (>= 2.1.19); however:
  Package menu is not installed.
 fluxbox depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-13ubuntu2.
 fluxbox depends on libfontconfig1 (>= 2.3.0); however:
  Version of libfontconfig1 on system is 2.2.2-2ubuntu3.
dpkg: error processing fluxbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fluxbox
```

---

### Post by DJ_Max on 2005-09-09
Post your /etc/apt/sources.list file

---

### Post by war-totem on 2005-09-09
```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
```

---

### Post by mlomker on 2005-09-09
> **war-totem]
 fluxbox depends on libc6 (>= 2.3.2.ds1-21) said:**
> 

Hmm.  You might want to check what repositories you have in /etc/apt/sources.list.

---

### Post by DJ_Max on 2005-09-09
That error usually happens when you've used unofficial packages and/or repositories.

See what does
```
sudo apt-get -f install
```

---

### Post by mlomker on 2005-09-09
Are you still running Warty?  I'd assume not since you are posting in Hoary app support.  Change those references to Hoary...

---

### Post by war-totem on 2005-09-09
i tried that earlier and all it did was remove the partially installed fluxbox.

this is a small sympton of a larger problem to do with dependencies.  i cant get many stables of any linux box through apt-get such as xmms-mpe mplayer vlc and so on.

any hints?

---

### Post by DJ_Max on 2005-09-09
[QUOTE=mlomker]Are you still running Warty?  I'd assume not since you are posting in Hoary app support.  Change those references to Hoary...[/QUOTE]
 Hrmm, why didn't I catch that??

What version are you using?

---

### Post by angkor on 2005-09-09
Why are there both Hoary and Warty repos in your sources.list?

---

### Post by DJ_Max on 2005-09-09
[QUOTE=angkor]Why are there both Hoary and Warty repos in your sources.list?[/QUOTE]
 Yep, that'll also cause your errors.

---

### Post by war-totem on 2005-09-09
all right you caught me, im a ubuntu noob.

how do i find out what im running, warty or hoary?

---

### Post by angkor on 2005-09-09
First BACK UP your important stuff, who knows your system is fscked beyond repair after that I'd try changing every "Warty" into "Hoary" in your sources.list and then:

sudo apt-get update

sudo apt-get dist-upgrade

---

### Post by angkor on 2005-09-09
[QUOTE=war-totem]all right you caught me, im a ubuntu noob.

how do i find out what im running, warty or hoary?[/QUOTE]

You installed Warty...then partially upgraded to Hoary...which isn't a very good idea. 

Since I don't know anything about downgrading from Hoary to Warty I'd suggest upgrading fully to Hoary by method I mentioned above. _Don't_ forget to back up your important stuff though...;)

---

### Post by war-totem on 2005-09-09
im apt-get dist-upgrade now.  i know enough about linux to wait until im stable before adding anything important to a new install.  i changed everything from hoary to warthog in my sources.list.

this is all very strange

---

### Post by angkor on 2005-09-09
Did you change everything to Warty? I did say change everything to Hoary...

That means you're changing back to the older version.

It's not really strange. Warty 4.10 is a different release from Hoary 5.04. Hoary is the latest stable version.

You should not mix repositories from both releases in your sources.list cause you'll end up with dependency trouble. Just keep everything pointed towards the Hoary repos or the Warty repos. Just don't mix em.

---

### Post by Juan4Ever on 2005-09-10
> **war-totem]```
The following packages have unmet dependencies:
  fluxbox: Depends: menu (>= 2.1.19) but it is not going to be installed
           Depends: libxinerama1 but it is not installable
E: Broken packages
``` 

is what i get when trying to apt-get fluxbox, and i get this when trying to install the .deb package:

```
root@ubuntu:~/debs # dpkg -i fluxbox_0.9.13-1_i386.deb
Selecting previously deselected package fluxbox.
(Reading database ... 62683 files and directories currently installed.)
Unpacking fluxbox (from fluxbox_0.9.13-1_i386.deb) ...
dpkg: dependency problems prevent configuration of fluxbox:
 fluxbox depends on menu (>= 2.1.19) said:**
> 
 im getting this error message after installing anything (with apt-get or with Synaptic)

[QUOTE]dpkg: error al procesar gpc (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 gpc
E: Sub-process /usr/bin/dpkg returned an error code (1)

sorry, im a linux noob trying to get a full linux system... working...

---

### Post by mlomker on 2005-09-11
[QUOTE=Juan4Ever]sorry, im a linux noob trying to get a full linux system... working...[/QUOTE]

No habla Espanol.   ;-) 

If you can translate that into English then more people would respond.

---

