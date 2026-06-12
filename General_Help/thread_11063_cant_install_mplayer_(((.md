---
title: "cant install mplayer :((("
date: 2005-01-13
forum: General Help
---

### Post by T31 on 2005-01-13
ive been looking for but i cant make this works!
after sudo apt-get install mplayer-386 this is what i got
___________________________________________________________________________________
sudo apt-get install mplayer-386
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libarts (>= 4:2.2.2-1) but it is not installable or
                        libarts-alsa (>= 4:2.2.2-1) but it is not installable
               Depends: libdvdread2 but it is not installable
               Depends: libvorbis0 (>= 1.0rc3-1) but it is not installable
E: Broken packages
____________________________________________________________________________________

ive been trying with synoptic as well but with the same results and i cant find a repository with this dependences :P please heeeeeeelp!!!

thanks in advance

Viva Ubuntu!!!!!

---

### Post by madzzoni on 2005-01-13
Do you make any changes to your /etc/apt/source.list before install  ???
You can get mplayer if you add extra repositories?
See ubuntuguide: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

for help on this.
 8-)

---

### Post by T31 on 2005-01-13
i did! even the script from the how to section and doesnt work yet  ](*,)

---

### Post by Perfect Storm on 2005-01-13
Are you sure you did it right while adding to the script? Try again, you could have missing something ;)

Or you could compile Mplayer, there's a nice guide here: [http://www.ubuntuforums.org/showthread.php?t=9850](http://www.ubuntuforums.org/showthread.php?t=9850)

---

### Post by T31 on 2005-01-13
artificial int, thats exactly the script i did and for sure is right couse i just copied and pasted whole text :(

---

### Post by wallijonn on 2005-01-13
> 
sudo apt-get install mplayer-386
Password:

Huh? DId you start a Root Terminal or a User Terminal?

After starting SPM ([COLOR=Blue]Computer -> System Configuration -> Synaptic Package Management[/COLOR]), Hit the [COLOR=Red]Reload Button[/COLOR]. 

-> "[COLOR=Blue]Custom Filters[/COLOR]" up/down arrows -> Select "[COLOR=Blue]Broken[/COLOR]".

What is listed? 

What Repositories are listed in your [COLOR=Blue]Settings -> Repositories[/COLOR]?

---

### Post by NewbieNik on 2005-01-14
Don't shout too loud if you've done this, but I pulled it from this really good and easy to follow thread:-

[http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94)

But try this

 $ sudo apt-get install manpages-dev
$ sudo apt-get install autoconf
$ sudo apt-get install automake
$ sudo apt-get install libtool
$ sudo apt-get install flex
$ sudo apt-get install bison
$ sudo apt-get install gcc-doc
$ sudo apt-get install g++
$ sudo apt-get install x-window-system-dev
$ sudo apt-get install libgtk1.2-dev
$ sudo apt-get install libpng-dev

Hope it helps!!!

---

### Post by T31 on 2005-01-14
# dont worry i dont like to shout but im starting to feel like to scream  :cry:
# everything fine 'till this point 
____________________________________________________________________________
$ sudo apt-get install g++
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  g++: Depends: g++-3.3 (>= 1:3.3.4-1) but it is not going to be installed
E: Broken packages
__________________________________________________________________________

# And doesnt let me install  the g++-3.3 as well with this saying i dont have gcc-3.3 and no matter if i do sudo blabla gcc-3.3 and the worst thing is that i have them installed already  :confused:

---

### Post by wallijonn on 2005-01-14
T31,

please post your sources.list.

Also, are you on Warty or Hoary?

---

### Post by T31 on 2005-01-15
im on Warty Warthog and this is my sources.list


_____________________________________________________________________________________


deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# ubuntu guide+ 1
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
# ubuntu guide+l 1

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

# ubuntu guide+ 2

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
# ubuntu guide+l 2
__________________________________________________________________________


Thx in advance

---

### Post by Perfect Storm on 2005-01-15
A silly question from me: Did you reload your rep. after adding the diffrent sources to the list?

---

### Post by T31 on 2005-01-15
lol :) yes i did, im newbie but no so much   8-[

---

### Post by zenrox on 2005-01-15
i have also tried to install mplayer useing that same install method but same dep errors come up and the files it wants ant on any of the repo.'s
it want libarts 2.2.2 but the repos has 3.2.2
its like that with all of them maby it needs to be forsed to use thoes as deps
or maby it only works with hoary(witch i had it worken on)  :confused:

---

### Post by Perfect Storm on 2005-01-15
Hmmm....Try open 'Synaptic Package Management' (Computer tab ---> System Conf.) and press the search button, write g++ does anything show up like 'g++' and 'g++-3.3'?

---

### Post by T31 on 2005-01-15
# with synaptic i located g++ 3.4 and no problem to install it, but a new problem trying # to install x-window-system-dev:(

 sudo apt-get install x-window-system-dev
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  x-window-system-dev: Depends: libdps-dev but it is not going to be installed
                       Depends: libdps1-dbg but it is not going to be installed
                       Depends: libice-dev but it is not going to be installed
                       Depends: libice6-dbg but it is not going to be installed
                       Depends: libsm-dev but it is not going to be installed
                       Depends: libsm6-dbg but it is not going to be installed
                       Depends: libx11-6-dbg but it is not going to be installed
                       Depends: libx11-dev but it is not going to be installed
                       Depends: libxaw7-dbg but it is not going to be installed
                       Depends: libxaw7-dev but it is not going to be installed
                       Depends: libxext-dev but it is not going to be installed
                       Depends: libxext6-dbg but it is not going to be installed
                       Depends: libxi-dev but it is not going to be installed
                       Depends: libxi6-dbg but it is not going to be installed
                       Depends: libxmu-dev but it is not going to be installed
                       Depends: libxmu6-dbg but it is not going to be installed
                       Depends: libxmuu-dev but it is not going to be installed
                       Depends: libxmuu1-dbg but it is not going to be installed
                       Depends: libxp-dev but it is not going to be installed
                       Depends: libxp6-dbg but it is not going to be installed
                       Depends: libxpm-dev but it is not going to be installed
                       Depends: libxpm4-dbg but it is not going to be installed
                       Depends: libxrandr-dev but it is not going to be installe d
                       Depends: libxrandr2-dbg but it is not going to be install ed
                       Depends: libxt-dev but it is not going to be installed
                       Depends: libxt6-dbg but it is not going to be installed
                       Depends: libxtrap-dev but it is not going to be installed
                       Depends: libxtrap6-dbg but it is not going to be installe d
                       Depends: libxtst-dev but it is not going to be installed
                       Depends: libxtst6-dbg but it is not going to be installed
                       Depends: libxv-dev but it is not going to be installed
                       Depends: libxv1-dbg but it is not going to be installed
                       Depends: xlibmesa-gl-dev but it is not going to be instal led
                       Depends: xlibmesa-glu-dev but it is not going to be insta lled
                       Depends: xlibmesa-gl-dbg but it is not going to be instal led
                       Depends: xlibmesa-glu-dbg but it is not going to be insta lled
                       Depends: xlibosmesa-dev
                       Depends: xlibs-static-dev but it is not going to be insta lled
                       Depends: xlibs-static-pic but it is not going to be insta lled
E: Broken packages

 :cry:

---

### Post by Sensebend on 2005-01-15
marillat's repository is out of sync with warty and has been for some time in regards to the mplayer package. I recommend following the instructions to compile mplayer or  doing this. [http://www.ubuntulinux.org/wiki/InstallingMplayerFromHoaryInWarty](http://www.ubuntulinux.org/wiki/InstallingMplayerFromHoaryInWarty)

---

### Post by T31 on 2005-01-16
Hey Thx a loooooooooooooooot Sensebend!!!!!!!!!!!!!

at last i could install it!!!!!!!!!!!!!!!!!!! :)

---

### Post by T31 on 2005-01-16
just one more question, maybe out of place but just in case someone knows how to enable this:

CPU: Advanced Micro Devices Athlon 4 /Athlon MP/XP Palomino 1461 MHz (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX


just in case  :mrgreen:

---

