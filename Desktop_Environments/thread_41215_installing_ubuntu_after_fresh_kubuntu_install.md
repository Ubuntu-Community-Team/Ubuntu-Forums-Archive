---
title: "installing ubuntu after fresh kubuntu install?"
date: 2005-06-12
forum: Desktop Environments
---

### Post by furtivefelon on 2005-06-12
hi, i had a default install of kubuntu, how do you get ubuntu desktop as well?

---

### Post by az on 2005-06-12
Install the ubuntu-desktop package.

---

### Post by furtivefelon on 2005-06-12
apparently kubuntu can't find it.. the following is the source.list

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary main restricted
 deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted
 deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

and the error i got after typing in sudo apt-get install ubuntu-desktop:
jason@jason:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package ubuntu-desktop

anyone know what's wrong?

---

### Post by improverrr on 2005-06-12
open your /etc/apt/sources file and replace with the following (after the 2nd line)

this will get you everything you ever wanted and then some:


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted  

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe multiverse  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe multiverse  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe multiverse  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe multiverse  

# deb [http://www.mpe.mpg.de/~ach/kubuntu/hoary/](http://www.mpe.mpg.de/~ach/kubuntu/hoary/) ./ 
# deb-src [http://www.mpe.mpg.de/~ach/kubuntu/hoary/](http://www.mpe.mpg.de/~ach/kubuntu/hoary/) ./ 

# deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./ 

# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main  
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main  
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main  

# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-backports main universe restricted  
# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras main universe restricted  

# deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free  
# deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free  

# Java - neustes SDK, JRE von Sun
# deb [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) binary/ 

# MPlayer, w32codecs, libdvdcss2, Transcode, Avidemux
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main  

# Bootspash Quelle
# deb [http://www.bootsplash.de/files/debian/](http://www.bootsplash.de/files/debian/) unstable main  


# unstable stuff

# deb [http://www.lychnis.net/files/debian/](http://www.lychnis.net/files/debian/) unstable/i386/ 
# deb [http://www.lychnis.net/files/debian/](http://www.lychnis.net/files/debian/) unstable/all/ 


# super experimental

# deb [http://kitenet.net/~joey/debian/](http://kitenet.net/~joey/debian/) unstable/ 
# deb [http://kitenet.net/~joey/debian/](http://kitenet.net/~joey/debian/) experimental/ 


# packages for multimedia and more, like mplayer

# deb [http://pessoal.onda.com.br/rjamorim/debian/](http://pessoal.onda.com.br/rjamorim/debian/) ./ 
# deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./ 
# deb [http://debian.xmixahlx.com/packages/unstable/](http://debian.xmixahlx.com/packages/unstable/) ./ 


# more stuff

# deb [http://bulma.net/~daneel/debian/](http://bulma.net/~daneel/debian/) ./ 
# deb [http://smurf.noris.de/code/debian/](http://smurf.noris.de/code/debian/) unstable smurf 
# deb [http://smurf.noris.de/code/debian/](http://smurf.noris.de/code/debian/) experimental smurf 

# deb [http://www.stanchina.net/~flavio/debian/](http://www.stanchina.net/~flavio/debian/) ./

---

