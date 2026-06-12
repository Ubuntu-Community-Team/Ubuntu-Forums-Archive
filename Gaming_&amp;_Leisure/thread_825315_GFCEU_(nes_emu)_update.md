---
title: "GFCEU (nes emu) update"
date: 2008-06-10
forum: Gaming &amp; Leisure
---

### Post by punkrockguy318 on 2008-06-10
Hello all!  It's been quite a while since I have really done anything really related to coding or programing or the OSS world.  However, last weekend I was bed ridden for a couple days due to kidney stones so I really could do much except for lie around and uh... oh.... code.

As of the last gfceu release (about a year or so ago?), fceu development had pretty much come to a halt and there was little work I could do to improve the GUI without digging into the fceu code.  And let me tell you, the FCEU code isn't the cleanest in the world (nor is any emulator for that matter).

However, fceu development has been picking up pace lately.  Many developers have been putting hard work into fceu to improve it and stabilize it.  While most of the developers work on the win32 port, two other devs and I have been working on getting the SDL port ready for release.

The lastest unreleased fceu (codenamed fceux) breaks compatibility with the old fceu, making gfceu 0.6.0 incompatible with fceux.  However, I worked on the gfceu codebase quite a bit and its now ready for release whenever fceux puts out a release.

FCEU is by far the best emulator option for Ubuntu, and I just wanted to let everyone know that it is alive and well.  If you would like to contribute, all the code (fceux and gfceux) is in the fceultra sourceforge subversion server.

```
  svn co https://fceultra.svn.sourceforge.net/svnroot/fceultra fceultra
```

I'm planning on making some serious improvements to (g)fceux in the future.  I'd like to see an actual GUI for fceu, rather than just the launcher that gfceu currently is. 

One major complaint I have received from numerous gfceu users is regarding the configuration system.  Yes, I'm aware it's a PITA.  No, there's nothing that can be done with the stable fceu.  However, with the latest code in subversion it should be much easier to write a GUI to configure gamepads

Just wanted to let the Ubuntu community know that everyone's favorite NES emulator is only going to get better, and if anyone is willing to help out just drop me a PM.

Keep on rockin in the free (as in beer and in speech) world :guitar:

---

### Post by punkrockguy318 on 2008-06-17
If you want to stay updated on GFCEU check it out on the website: [http://dietschnitzel.com/gfceu/](http://dietschnitzel.com/gfceu/)

---

### Post by tukuyomi on 2008-06-17
Thank you for this GTK port of this wonderful NES emulator, one more to join others, especially Snes9X-GTK for the SNES ([http://snes9x.com/phpbb2/viewtopic.php?t=3703](http://snes9x.com/phpbb2/viewtopic.php?t=3703)) --my favorite.
Furthermore, you can follow this topic if you want to stay tuned about fceu development (mainly related to re-recording): [http://tasvideos.org/forum/viewtopic.php?t=1020](http://tasvideos.org/forum/viewtopic.php?t=1020)
Congratulations and Thanks again ;)

---

### Post by cor2y on 2008-06-19
I have been looking for a plain nes emulator for linux for a while.
How complete is it?
Unfortunately couldn't get this to compile on Gutsy even with scons and libsdl-dev installed.
```
SPRINTF -DOPENGL -O3 -g -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -DLSB_FIRST -D_DEBUG -I/usr/include/SDL src/input/zapper.cpp
src/input/zapper.cpp: In function 'void LogZapper(int, MovieRecord*)':
src/input/zapper.cpp:148: error: 'data' was not declared in this scope
src/input/zapper.cpp:148: warning: unused variable 'ptr'
scons: *** [src/input/zapper.o] Error 1
scons: building terminated because of errors.
```

---

### Post by punkrockguy318 on 2008-06-19
It's complete, it's been around and used for a very long time.

The zapper.cpp just just a new update in subversion so you might want to try svn up and recompiling; but regardless i'm not sure if it will compile on gutsy, what version of gcc do you have?

---

### Post by cor2y on 2008-06-20
gcc 4.2.3 and scons is 0.97.0d20071203.r2509.

---

### Post by punkrockguy318 on 2008-07-01
> **cor2y said:**
> gcc 4.2.3 and scons is 0.97.0d20071203.r2509.

run an ```
svn up
``` in the fceu directory to update the files.  It should compile with those verisons in the latest subversion.

---

### Post by punkrockguy318 on 2008-07-02
I've compiled a 64 bit version of fceux and bundled the latest gfceu with it.

I'd encourange anyone who wants to see fceux improve to test this on your Ubuntu machines and report your bugs to me so they can get fixed before release.

Known Issues:
Netplay is broken.
Some people are reporting sound issues.  Please report any issues you may have with sound so I can do my best to fix them.

Check out [http://dietschnitzel.com/gfceu/](http://dietschnitzel.com/gfceu/)  for the latest *nix svn builds.

---

### Post by Cygoku on 2008-07-23
Wouldn't a 32 bit package be more widely used?

Cygoku

---

### Post by GSZX1337 on 2008-07-23
> **Cygoku said:**
> Wouldn't a 32 bit package be more widely used?

Cygoku

Shh, he'll stop making .debs I can use. :P

---

### Post by punkrockguy318 on 2008-07-23
> **Cygoku said:**
> Wouldn't a 32 bit package be more widely used?

Cygoku

Yes, but I don't have access to a 32bit linux machine.  It's best to just compile it from subversion, because features are always being added.

For instance a lua engine was just added over the past few days.  We're still working on the UI for the sdl port however

---

### Post by punkrockguy318 on 2008-08-03
FceuX 2.0.0 was just released and sports a whole set of new features.  GfceuX 2.0.0 was also released alongside it, and you can grab them both from the source tarbel.  Check it out on the [website]("http://fceux.com")

---

### Post by daring derelict on 2008-09-02
> **punkrockguy318 said:**
> It's complete, it's been around and used for a very long time.

The zapper.cpp just just a new update in subversion so you might want to try svn up and recompiling; but regardless i'm not sure if it will compile on gutsy, what version of gcc do you have?

The legacy fce ultra installs and works great using synaptic, but the fceux does not have a .deb file.  I tried to follow the minimalist instructions for compiling and installng, but it doesn't execute properly. terminal emulator gives the following output:

~$ gfceux
Traceback (most recent call last):
  File "/usr/local/bin/gfceux", line 605, in <module>
    app = GfceuApp()
  File "/usr/local/bin/gfceux", line 213, in __init__
    self.fceux_binary = self.find_fceu()
  File "/usr/local/bin/gfceux", line 258, in find_fceu
    gfceu_error('Could not find the fceux binary.\n\
NameError: global name 'gfceu_error' is not defined
~$

any sugestions?

---

### Post by punkrockguy318 on 2008-09-03
> **daring derelict said:**
> The legacy fce ultra installs and works great using synaptic, but the fceux does not have a .deb file.  I tried to follow the minimalist instructions for compiling and installng, but it doesn't execute properly. terminal emulator gives the following output:

~$ gfceux
Traceback (most recent call last):
  File "/usr/local/bin/gfceux", line 605, in <module>
    app = GfceuApp()
  File "/usr/local/bin/gfceux", line 213, in __init__
    self.fceux_binary = self.find_fceu()
  File "/usr/local/bin/gfceux", line 258, in find_fceu
    gfceu_error('Could not find the fceux binary.\n\
NameError: global name 'gfceu_error' is not defined
~$

any sugestions?

The newest gfceux is distributed with the newest fceux (2.0.2).  Grab the latest fceux source code which will include the latest gfceux (2.0.2).  2.0.2 fixes that bug you are experiencing

---

### Post by daring derelict on 2008-09-13
The main FCEUX site apears to be down, however, I downloaded the tarball from [SourceForge]("http://fceultra.svn.sourceforge.net/viewvc/fceultra/") on 13 Sep 08 and compiled. here are all the command outputs:

```
$ sudo python setup.py install --prefix=/usr/local
running install
running build
running build_scripts
creating build
creating build/scripts-2.5
copying and adjusting gfceu -> build/scripts-2.5
changing mode of build/scripts-2.5/gfceu from 644 to 755
running install_scripts
copying build/scripts-2.5/gfceu -> /usr/local/bin
changing mode of /usr/local/bin/gfceu to 755
running install_data
creating /usr/local/share/gfceu
copying gfceu.glade -> /usr/local/share/gfceu/
copying gfceu_big.png -> /usr/local/share/gfceu/
copying gfceu.png -> /usr/local/share/gfceu/
copying gfceu.png -> /usr/local/share/pixmaps/
copying gfceu.1 -> /usr/local/share/man/man1/
copying gfceu.desktop -> /usr/local/share/applications/
running install_egg_info
Writing /usr/local/lib/python2.5/site-packages/gfceu-0.6.1.egg-info

$ gfceux
Traceback (most recent call last):
  File "/usr/local/bin/gfceux", line 605, in <module>
    app = GfceuApp()
  File "/usr/local/bin/gfceux", line 213, in __init__
    self.fceux_binary = self.find_fceu()
  File "/usr/local/bin/gfceux", line 258, in find_fceu
    gfceu_error('Could not find the fceux binary.\n\
NameError: global name 'gfceu_error' is not defined
$ 
```

---

### Post by punkrockguy318 on 2008-09-14
oops, I just fixed your problem in gfceux version 896.  But that error message only occurs when you don't have fceux installed.  Download fceux from the website and isntall that before you install gfceux

---

### Post by daring derelict on 2008-09-14
> **punkrockguy318 said:**
> oops, I just fixed your problem in gfceux version 896. But that error message only occurs when you don't have fceux installed. Download fceux from the website and isntall that before you install gfceux

apparently my problem is with SCons.  in the fceu install file, it says to :

To compile and install FCE Ultra, follow these steps:
  1.  Ensure that SCons, SDL, and liblua5.1 are installed on your system.
  2.  If you are running linux, ensure zenity is installed on your system.
  3.  Run "scons" to build fceux.
  4.  To install on Linux/BSD run "scons install" as root.

I am definately new at all of this, but I pick up fast.  everytime i run scons i get:
```
$ scons
The program 'scons' is currently not installed.  You can install it by typing:
sudo apt-get install scons
bash: scons: command not found
$ sudo apt-get install scons
Reading package lists... Done
Building dependency tree       
Reading state information... Done
scons is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ scons
The program 'scons' is currently not installed.  You can install it by typing:
sudo apt-get install scons
bash: scons: command not found
$
```

so apparently I need to reinstall scons; or figure out how to use it.

---

### Post by punkrockguy318 on 2008-09-14
> **daring derelict said:**
> apparently my problem is with SCons.  in the fceu install file, it says to :

To compile and install FCE Ultra, follow these steps:
  1.  Ensure that SCons, SDL, and liblua5.1 are installed on your system.
  2.  If you are running linux, ensure zenity is installed on your system.
  3.  Run "scons" to build fceux.
  4.  To install on Linux/BSD run "scons install" as root.

I am definately new at all of this, but I pick up fast.  everytime i run scons i get:
```
$ scons
The program 'scons' is currently not installed.  You can install it by typing:
sudo apt-get install scons
bash: scons: command not found
$ sudo apt-get install scons
Reading package lists... Done
Building dependency tree       
Reading state information... Done
scons is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ scons
The program 'scons' is currently not installed.  You can install it by typing:
sudo apt-get install scons
bash: scons: command not found
$
```

so apparently I need to reinstall scons; or figure out how to use it.


try 

apt-get remove scons

apt-get install scons

and make sure you're using the latest versino of the repos

---

### Post by daring derelict on 2008-09-15
thank you, that fixed the issue with scons, but I can't seem to install some of the other items related to the compiler which are required to install fceux.  
I am apparently missing some of the repositories needed for the dependencies for Gpp and lib.SDL

in response to your earlier post: you were right, fceux was not installed, just the front end. oops ;p

---

### Post by punkrockguy318 on 2008-09-15
> **daring derelict said:**
> thank you, that fixed the issue with scons, but I can't seem to install some of the other items related to the compiler which are required to install fceux.  
I am apparently missing some of the repositories needed for the dependencies for Gpp and lib.SDL

in response to your earlier post: you were right, fceux was not installed, just the front end. oops ;p

This should install all the dependencies required for fceux

```
sudo apt-get install build-essential scons libsdl1.2-dev liblua5.1-dev libz-dev zenity
```

I'm in front of a windows machine right now so I'm not sure if all of those package names are exact but I'll check it out when I get to my laptop

Hope that solves your issue

---

### Post by daring derelict on 2008-09-15
> **punkrockguy318 said:**
> This should install all the dependencies required for fceux

```
sudo apt-get install build-essential scons libsdl1.2-dev liblua5.1-dev libz-dev zenity
```I'm in front of a windows machine right now so I'm not sure if all of those package names are exact but I'll check it out when I get to my laptop

Hope that solves your issue

I must be missing software sources, or I'm just totally missing something.  this is what I got:

```
$ sudo apt-get install build-essential scons libsdl1.2-dev liblua5.1-dev libz-dev zenity

[sudo] password for [me]: *********

Reading package lists... Done
Building dependency tree       
Reading state information... Done
scons is already the newest version.
Note, selecting liblua5.1-0-dev instead of liblua5.1-dev
Note, selecting zlib1g-dev instead of libz-dev
zenity is already the newest version.

[COLOR=Blue]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.[/COLOR]
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
  liblua5.1-0-dev: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: libreadline5-dev but it is not going to be installed
  libsdl1.2-dev: Depends: libglu1-xorg-dev but it is not going to be installed or
                          libglu-dev
  zlib1g-dev: Depends: zlib1g (= 1:1.2.3.3.dfsg-7ubuntu1) but 1:1.2.3.3.dfsg-12 is to be installed
              Depends: libc6-dev but it is not going to be installed or
                       libc-dev
E: Broken packages
$ 
```I highlighted part of it in blue, it gives something beneath it that may help you.

good luck:-s:confused:

---

### Post by punkrockguy318 on 2008-09-16
daring do you have the universe repositories enabled?

---

### Post by daring derelict on 2008-09-19
> **punkrockguy318 said:**
> daring do you have the universe repositories enabled?

I have all repositories in the "Ubuntu Software" tab of the "Software Sources" enabled
so, I'm pretty sure that it is.

---

### Post by punkrockguy318 on 2008-09-19
> **daring derelict said:**
> I have all repositories in the "Ubuntu Software" tab of the "Software Sources" enabled
so, I'm pretty sure that it is.

What version of Ubuntu are you running?  It looks like you can't install build-essential which is a pretty common package.  There's something fscked up with your Ubunut install but i'm not sure what it is

---

### Post by daring derelict on 2008-09-19
> **punkrockguy318 said:**
> What version of Ubuntu are you running?  It looks like you can't install build-essential which is a pretty common package.  There's something fscked up with your Ubunut install but i'm not sure what it is

8.04 hardy heron

---

### Post by punkrockguy318 on 2008-09-19
> **daring derelict said:**
> 8.04 hardy heron

I'm really not sure of a solution to that issue.  it seems to be an Ubuntu issue, can anyone shed any light on not being able to install build-essential?

---

### Post by daring derelict on 2008-09-19
> **punkrockguy318 said:**
> I'm really not sure of a solution to that issue.  it seems to be an Ubuntu issue, can anyone shed any light on not being able to install build-essential?
I installed the packages using Smart Package Manager 0.52 and it fixed the problem.  I apparently had some pieces installed already and they were not of the version compatible with the ones needed for FCEUX.  but all is well, it now opens and I am getting ready to enjoy my first game on it. thank you so much for your help.

:KS:KS:guitar::):)

PS:  the correct syntax for SCons that worked for me was: sudo scons install
just using "sudo scons" returned the same error as before when it said scons was not installed

---

### Post by dfreer on 2008-09-19
> **daring derelict said:**
> I have all repositories in the "Ubuntu Software" tab of the "Software Sources" enabled
so, I'm pretty sure that it is.

I'd recommend posting the contents of your /etc/apt/sources.list file.

Your problem of not being able to install build-essential is likely due to either having extra repositories enabled that have newer versions of some software, causing dependency issues, or not having the main repositories enabled.

---

### Post by daring derelict on 2008-09-19
> **dfreer said:**
> I'd recommend posting the contents of your /etc/apt/sources.list file.

Your problem of not being able to install build-essential is likely due to either having extra repositories enabled that have newer versions of some software, causing dependency issues, or not having the main repositories enabled.


here it is:
```

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy restricted main
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy restricted multiverse universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-updates restricted main
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-updates restricted multiverse universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy universe
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy multiverse
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-backports restricted universe multiverse main
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-backports restricted universe multiverse main

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-security restricted main
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-security restricted multiverse universe main #Added by software-properties
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-security universe
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-security multiverse
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-proposed restricted multiverse universe main
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-proposed restricted multiverse universe main #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted multiverse universe
deb http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
deb-src http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
deb http://ppa.launchpad.net/synce/ubuntu hardy main
deb-src http://ppa.launchpad.net/synce/ubuntu hardy main

```

---

### Post by daring derelict on 2008-09-19
by the way, what exactly is the main folder for fceux... you know the one that I'm supposed to place the disksys and gg.rom files in

~~ never mind, I answered my own question ~./fceux

---

### Post by dfreer on 2008-09-27
```

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy restricted main
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy restricted multiverse universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-updates restricted main
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-updates restricted multiverse universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy universe
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy multiverse
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[B][i]deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-backports restricted universe multiverse main
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-backports restricted universe multiverse main[/i][/B]

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

[B]deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-security restricted main
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-security restricted multiverse universe main #Added by software-properties
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-security universe
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-security multiverse
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-proposed restricted multiverse universe main
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ hardy-proposed restricted multiverse universe main #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted multiverse universe
deb http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
deb-src http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
deb http://ppa.launchpad.net/synce/ubuntu hardy main
deb-src http://ppa.launchpad.net/synce/ubuntu hardy main[/B]

```

All the ones in **bold** are not official repositories. If you are having package conflicts, start by disabling those repositories and then updating apt-get.

The two in ***bold-italics*** are the backports repositories. They are there for installing newer versions of packages than the ones released in hardy, like let's say wine 1.0 instead of wine 0.98, that aren't security/bug related. If you still have problems, it wouldn't hurt to try disabling those repositories as well.

Getting rid of the CD repository is also recommended unless you need it/use it for some reason. In short, I'd just have the following (feel free to change to the mirror of your choice):
```
deb http://archive.ubuntu.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main universe multiverse restricted

deb http://archive.ubuntu.com/ubuntu/ hardy-updates main universe multiverse restricted
deb http://security.ubuntu.com/ubuntu/ hardy-security main universe multiverse restricted
```

---

### Post by daring derelict on 2008-09-29
the unofficial repos are either for opensync/synce(pocket pc software) or are the mirrors that were automatically generated from the software sources menu(download from: [other]...[_S_elect best server])

but thank you, I did disable a number of the unnessisary reopos.

---

### Post by dfreer on 2008-09-29
> **daring derelict said:**
> the unofficial repos are either for opensync/synce(pocket pc software) or are the mirrors that were automatically generated from the software sources menu(download from: [other]...[_S_elect best server])

but thank you, I did disable a number of the unnessisary reopos.

You can always reenable them later when you need to update that software. As for build-essential, were you able to get past the dependency issues once you cleaned out your repository list and updated apt-get?

---

### Post by daring derelict on 2008-10-10
> **dfreer said:**
> You can always reenable them later when you need to update that software. As for build-essential, were you able to get past the dependency issues once you cleaned out your repository list and updated apt-get?

Yes, I was able to fix the dependency issues using "Smart Package Manager"

---

### Post by guyster on 2008-10-24
Hi all, I'm happy to anounce that I got fceux 2.0.2 and the included gfceu installed successfully.  I just have a general question for anyone who doesn't mind answering.  What have you found to be optimal settings for the sample rate and buffer size parameters under sound in gfceu?  I have a core2 duo processor with 2 gb of RAM, running Ubuntu Intrepid with latest updates and pulseaudio.  If anyone has any input, it would be greatly appreciated.

Thanks,


Guy

---

### Post by punkrockguy318 on 2008-10-25
> **guyster said:**
> Hi all, I'm happy to anounce that I got fceux 2.0.2 and the included gfceu installed successfully.  I just have a general question for anyone who doesn't mind answering.  What have you found to be optimal settings for the sample rate and buffer size parameters under sound in gfceu?  I have a core2 duo processor with 2 gb of RAM, running Ubuntu Intrepid with latest updates and pulseaudio.  If anyone has any input, it would be greatly appreciated.

Thanks,


Guy

The SDL sound is sort of sketchy.  First off, I find using the libsdl1.2debian-pulseaudio sound driver for SDL works better than whatever Ubuntu installs by default.

I use 11000 sample size and a 48ms buffer size and it plays pretty cleanly.  Give those settings a try and see how that works out for you

---

