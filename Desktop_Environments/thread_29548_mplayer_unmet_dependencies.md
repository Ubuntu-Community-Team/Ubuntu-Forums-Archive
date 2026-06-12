---
title: "mplayer unmet dependencies"
date: 2005-04-24
forum: Desktop Environments
---

### Post by negatory on 2005-04-24
I'm trying to upgrade mplayer-amd64 but it keeps complaining about unmet dependencies.

```
# apt-get install mplayer
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
  mplayer: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to be installed
           Depends: libbio2jack0 but it is not going to be installed
           Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
           Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
           Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
           Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
           Depends: xmms (>= 1.2.10+cvs20050209) but 1.2.10-2ubuntu1 is to be installed
E: Broken packages
```

here are the contents of my sources.list
```
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://pt.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://pt.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://pt.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://pt.archive.ubuntu.com/ubuntu hoary universe
deb-src http://pt.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

#Ubuntu backports
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

#Marrillat
deb http://cyberspace.ucla.edu/marillat unstable main
```  

I can't install any of those unmet dependencies some saying that they're allready the newest version and others saying that depend on others that say that they're allready the newest version   ](*,) . 
It started when I added the marrilat repository...I think.
Any help on this?
Thanks

Pedro Carrico

---

### Post by Burgundavia on 2005-04-24
I think there is a package collision between the marilliat repo and the hoary repo. 

Corey

---

### Post by NeoChaosX on 2005-04-25
Remove the marillat repos. They cause a lot of headaches for any Ubuntu users trying to install MPlayer.

---

### Post by aiyi on 2005-04-25
But how to install MPlayer via apt-get&#65311;

---

### Post by NeoChaosX on 2005-04-25
There's builds of MPlayer in the offical Hoary repos, so you're really not going to miss the marillat repos all that much.

---

### Post by negatory on 2005-04-25
Yes there's some kind of package collision beetween the two!
Thanks

Pedro Carrico

---

### Post by Vache on 2005-04-26
[QUOTE=negatory]Yes there's some kind of package collision beetween the two!
Thanks

Pedro Carrico[/QUOTE]
 I have removed the repositories in question, and I still get...

[code]
The following packages have unmet dependencies:
  mplayer-386: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but it is not going to be installed
E: Broken packages
[code]

Hmm... *ponders*

---

### Post by Perfect Storm on 2005-04-26
Did you first:

```

sudo apt-get update
sudo apt-get upgrade

```


By the way also try VLC media player which is my opinion is much better than Mplayer (vlc, vlc-plugin-esd, wxvlc, mozilla-plugin-vlc) when it comes to play DVD movies on the PC

---

### Post by fordfan753 on 2005-04-26
[QUOTE=Vache]I have removed the repositories in question, and I still get...

[code]
The following packages have unmet dependencies:
  mplayer-386: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but it is not going to be installed
E: Broken packages
[code]

Hmm... *ponders*[/QUOTE]


Why mplayer-386 ?...Can't you just get standard mplayer? Also, make sure you have the multiverse repositories, these are mentioned in the Hoary guide.

---

### Post by Perfect Storm on 2005-04-26
If I'm not mistaken i586 and i686 depends on i386 (did with I try), but I droped it and compile my own instead.

---

