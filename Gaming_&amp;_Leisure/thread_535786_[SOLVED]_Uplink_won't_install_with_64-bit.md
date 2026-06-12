---
title: "[SOLVED] Uplink won't install with 64-bit"
date: 2007-08-26
forum: Gaming &amp; Leisure
---

### Post by noerrorsfound on 2007-08-26
> 
Verifying archive integrity... All good.
Uncompressing Uplink complete 1.54DOWNLOAD............................................................................................
/home/nicholas/.setup1635: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I have libgtk-1.2 installed, but it's the 64-bit version. I don't know how to install the 32-bit version.

---

### Post by Cappy on 2007-08-27
Install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

and then
```

sudo getlibs -32 libgtk-1.2.so.0 libgmodule-1.2.so.0

```
You may need to repeat if more libraries are missing.

Here are some libraries I found Darwinia (made by the same game maker) needed, which may or may not be needed by Uplink:
```

sudo apt-get install ia32-libs ia32-libs-sdl libc6-i386 lib32gcc1

```

I always found Uplink quite boring since there isn't much thinking involved so I would recommend hackthissite.org. Then again, I don't like MMORPGs at ALL so take my recommendation with a grain of salt.

---

### Post by noerrorsfound on 2007-08-27
Thanks! That worked, and I guess I already had all the other needed libraries because I didn't need to do that last step.

---

### Post by J-raff on 2007-11-04
To Cappy,
Thanks for this. It worked great!:)

---

### Post by blastradius on 2008-03-17
This is what I get when I try to ./uplink on Gutsy 64:

/usr/X11R6/lib/libXmu.so.6 /usr/X11R6/lib/libXi.so.6 ./libfreopen-override.so.0.0.0
ERROR: ld.so: object '/usr/X11R6/lib/libXmu.so.6' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/X11R6/lib/libXi.so.6' from LD_PRELOAD cannot be preloaded: ignored.
./uplink.bin: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Any help would be appreciated.

---

### Post by Cappy on 2008-03-17
run getlibs ( [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) ) on uplink.bin (wherever your performed ./uplink probably)
```
getlibs uplink.bin
```

or use
```
getlibs -l libstdc++-libc6.2-2.so.3
```
just for that one package.

---

### Post by blastradius on 2008-03-18
Hi

Thanks for your reply, still got probs' though.  This is how it went:-

eric@blastradius:~$ cd uplink/uplink
eric@blastradius:~/uplink/uplink$ getlibs uplink.bin
libstdc++-libc6.2-2.so.3: libstdc++2.10-glibc2.2
The following i386 packages will be installed:
libstdc++2.10-glibc2.2
Continue [Y/n]? y
W: Unable to locate package libstdc++2.10-glibc2.2
E: No packages found
libstdc++2.10-glibc2.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
eric@blastradius:~/uplink/uplink$ getlibs -l libstdc++-libc6.2-2.so.3
libstdc++-libc6.2-2.so.3: libstdc++2.10-glibc2.2
The following i386 packages will be installed:
libstdc++2.10-glibc2.2
Continue [Y/n]? y
W: Unable to locate package libstdc++2.10-glibc2.2
E: No packages found
libstdc++2.10-glibc2.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

I've got (as far as I know all the repos' installed.)  In fact here it is:-

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/robster/ubuntu](http://ppa.launchpad.net/robster/ubuntu) gutsy universe
#AUTOMATIX REPOS START

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main
deb [http://repository.akirad.net](http://repository.akirad.net) akirad-gutsy main
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

Thanks again for your help!

---

### Post by Cappy on 2008-03-18
That library doesn't seem exist for 64-bit and thus it can't find the information for it on your system. *scribbles down notes on this in his etch-a-scetch*

Use
```
getlibs -w http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
```
instead =)

---

### Post by blastradius on 2008-03-22
libs now installed but on trying to run uplink it goes to the black screen and then restarts X so I have to login again!  How can I change the options without having to be in-game? maybe if I just mess with display settings I'll get it right.

I used to have the game running fine on 32bit,  I'm starting to think this 64bit distro is more trouble than it's worth, is it possible to go back to 32bit without a complete re-install?

---

### Post by Cebonet on 2008-06-18
I get this, and my repositories are enabled and updated:

libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
Downloading ...
Installing libraries ...

---

### Post by Cappy on 2008-06-18
What's the missing library?
Which version of Ubuntu are you running?

If you're running Hardy enable the Universe repositories and use
```
sudo getlibs -p libglib1.2ldbl
```

If you are running Gutsy enable the Universe repositories and use
```
sudo getlibs -p libglib1.2
```

---

### Post by faldore on 2011-01-18
> **Cappy said:**
> What's the missing library?
Which version of Ubuntu are you running?

If you're running Hardy enable the Universe repositories and use
```
sudo getlibs -p libglib1.2ldbl
```

If you are running Gutsy enable the Universe repositories and use
```
sudo getlibs -p libglib1.2
```

I am using 10.10 Maverick, and I get this error message:


$ sudo getlibs -p libglib1.2
The following i386 packages will be installed: libglib1.2
Continue [Y/n]? Y
E: No packages found
libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install


I tried this:
$ sudo getlibs -p libglib1.2ldbl
The following i386 packages will be installed: libglib1.2ldbl
Continue [Y/n]? Y
E: No packages found
libglib1.2ldbl was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install


Anyone seen this?

---

### Post by Perfect Storm on 2011-01-18
Necromancing. Thread closed.

---

