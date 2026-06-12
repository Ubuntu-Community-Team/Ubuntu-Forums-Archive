---
title: "Problem installing Wine"
date: 2005-12-08
forum: General Help
---

### Post by Ferrat on 2005-12-08
Well trying to install wine to be able to play some games and use some apps, however I get an error saying that my compiler can't create exec files? 

Im pretty new to Linux, used linux a couple of years ago but turned to Windows and got to confy.

The output is somewhat in Swedish, for this Im sry but you get the idea, have translated some that I think could be important.

```
holo@Holokauston:~$ sudo apt-get --build source wine
L&#228;ser paketlistor... F&#228;rdig
Bygger beroendetr&#228;d... F&#228;rdig
Beh&#246;ver h&#228;mta 13,1MB k&#228;llkodsarkiv.
L&#228;s:1 http://wine.sourceforge.net source/ wine 0.9.2-winehq-1 (dsc) [1125B]
L&#228;s:2 http://wine.sourceforge.net source/ wine 0.9.2-winehq-1 (tar) [13,1MB]
L&#228;s:3 http://wine.sourceforge.net source/ wine 0.9.2-winehq-1 (diff) [46,0kB]
H&#228;mtade 13,1MB p&#229; 1m1s (214kB/s)
dpkg-source: extracting wine in wine-0.9.2-winehq
dpkg-source: unpacking wine_0.9.2-winehq.orig.tar.gz
dpkg-source: applying ./wine_0.9.2-winehq-1.diff.gz
dpkg-buildpackage: source package is wine
dpkg-buildpackage: source version is 0.9.2-winehq-1
dpkg-buildpackage: source changed by Scott Ritchie <scott@open-vote.org>
dpkg-buildpackage: host architecture amd64
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/holo/wine-0.9.2-winehq'
make[1]: *** No rules for creating target "distclean".  Stopp.
make[1]: Leaving directory `/home/holo/wine-0.9.2-winehq'
make: [clean] Error 2 (ignored)
#-/usr/bin/make -C documentation clean
dh_clean
 debian/rules build
dh_testdir
# Add here commands to configure the package.
CFLAGS="-Wall -g -O2" ./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for x86_64-linux-gnu-gcc... gcc -m32
[COLOR="Red"]checking for C compiler default output file name... configure: error: C compiler cannot create executables[/COLOR]
See `config.log' for more details.
make: *** [config.status] Error 77
Buildcommand "cd wine-0.9.2-winehq && dpkg-buildpackage -b -uc" failed.
E: Childprocess failed

```

Anyone got any ideas?

EDIT: 
Should probably say that Im using the 64bit version if you didn't see that :P

---

### Post by 23meg on 2005-12-08
You don't absolutely have to compile Wine from scratch. Did you try installing it from the repositories? If you don't prefer that, do a forum search to find info on installing the latest Wine from CVS.

---

### Post by Bachstelze on 2005-12-08
I agree, there's no need to reompile wine from source, the Ubuntu packages works fine, unlike some others (VLC anyone ?)

---

### Post by Ferrat on 2005-12-08
Added the repositories and according to Synaptic it couldn't find a install for wine there but a file that pointed to it and something about out of date >_<

---

### Post by Bachstelze on 2005-12-08
Certainly your sources.list is wrong. Here is a good one : 

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```

---

### Post by Ferrat on 2005-12-08
Just before I do this ^^ 

I understand right when I think it doesn't matter that I run the 64bit version?:roll:

---

### Post by Bachstelze on 2005-12-08
No it doesn't...

---

### Post by Ferrat on 2005-12-08
Hmm ok got this responce to that when I opened Synaptic

```

W: Couldn't get status on sourcecodepaketlist http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 File or Folder doesn't exist)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status p&#229; k&#228;llkodspaketlistan http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)

```

The first line I Translated from Swedish rest is the same just in swedish.

---

### Post by Ferrat on 2005-12-08
NVM forgot to update the system ^^

Works now but still don't get to DL wine even after adding the
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

>/

---

### Post by Bachstelze on 2005-12-08
what do you get when trying to run

```
sudo apt-get install wine
```

---

### Post by Ferrat on 2005-12-08
```

holo@Holokauston:~$ sudo apt-get install wine
L&#228;ser paketlistor... F&#228;rdig (DONE)
Bygger beroendetr&#228;d... F&#228;rdig (DONE)
Packet wine is not avalible, but another packet refers to it.
This usally means that the packet is missing, has "gone old" or just is availble from other sources.
E: Packet wine has no installationscandidate

```

Thats the same responce as before :(

---

### Post by YokoZar on 2005-12-08
[QUOTE=Ferrat]Just before I do this ^^ 

I understand right when I think it doesn't matter that I run the 64bit version?:roll:[/QUOTE]
No, it matters completely.  The reason you're getting the error you are is because there is no 64 bit Wine package.  This is because Wine does not build in 64 bit mode yet.  You *have* to install Wine in a 32 bit chroot environment.

---

### Post by Ferrat on 2005-12-08
Hmm ok, hecked Winehq and there it said that it worked on 64bit but not how so figured it wouldn't matter.. 

Read about chroot before anyone have a nice guide or can sceetch down some notes to follow? :)

---

### Post by Ferrat on 2005-12-09
*bump*

---

