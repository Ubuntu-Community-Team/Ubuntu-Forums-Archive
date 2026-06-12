---
title: "[SOLVED] plplot errors in compiling gdl"
date: 2008-10-30
forum: Education &amp; Science
---

### Post by dphus on 2008-10-30
I'm having a lot of issues trying to get GDL to compile on my machine.  I've seen a couple of other posts with people with different issues, and have followed the suggestions that they got from others, which as you can imagine came to no avail. 

so...
when i type in 
./configure
make

i get ...

make  all-recursive
make[1]: Entering directory `/home/manic/etc/dl/gdl-0.9rc1'
Making all in src
make[2]: Entering directory `/home/manic/etc/dl/gdl-0.9rc1/src'
Making all in antlr
make[3]: Entering directory `/home/manic/etc/dl/gdl-0.9rc1/src/antlr'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/manic/etc/dl/gdl-0.9rc1/src/antlr'
make[3]: Entering directory `/home/manic/etc/dl/gdl-0.9rc1/src'
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/magick -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf -I/usr/include/hdf5 -I/usr/include/python2.5     -g -O2 -MT gdl-plot3d_nr.o -MD -MP -MF .deps/gdl-plot3d_nr.Tpo -c -o gdl-plot3d_nr.o `test -f 'plot3d_nr.cpp' || echo './'`plot3d_nr.cpp
/usr/include/plplot/plplotP.h: In function ‘void lib::plgrid3(PLFLT)’:
/usr/include/plplot/plplotP.h:406: error: too many arguments to function ‘void pldtik(PLFLT, PLFLT, PLFLT*, PLINT*)’
plot3d_nr.cpp:223: error: at this point in file
plot3d_nr.cpp: In function ‘void lib::plnxtvhi(PLINT*, PLINT*, PLFLT*, PLINT, PLINT)’:
plot3d_nr.cpp:344: warning: deprecated conversion from string constant to ‘char*’
plot3d_nr.cpp:384: warning: deprecated conversion from string constant to ‘char*’
plot3d_nr.cpp: In function ‘void lib::plnxtvlo(PLINT*, PLINT*, PLFLT*, PLINT, PLINT)’:
plot3d_nr.cpp:633: warning: deprecated conversion from string constant to ‘char*’
plot3d_nr.cpp:675: warning: deprecated conversion from string constant to ‘char*’
plot3d_nr.cpp: In function ‘void lib::savehipoint(PLINT, PLINT)’:
plot3d_nr.cpp:877: warning: deprecated conversion from string constant to ‘char*’
plot3d_nr.cpp: In function ‘void lib::savelopoint(PLINT, PLINT)’:
plot3d_nr.cpp:897: warning: deprecated conversion from string constant to ‘char*’
plot3d_nr.cpp: In function ‘void lib::c_plot3dcl_nr(PLFLT*, PLFLT*, PLFLT**, PLINT, PLINT, PLINT, PLFLT*, PLINT, PLINT, PLINT, PLINT*, PLINT*)’:
plot3d_nr.cpp:1115: warning: deprecated conversion from string constant to ‘char*’
plot3d_nr.cpp:1120: warning: deprecated conversion from string constant to ‘char*’
plot3d_nr.cpp:1125: warning: deprecated conversion from string constant to ‘char*’
plot3d_nr.cpp:1155: warning: deprecated conversion from string constant to ‘char*’
plot3d_nr.cpp:1183: warning: deprecated conversion from string constant to ‘char*’
make[3]: *** [gdl-plot3d_nr.o] Error 1
make[3]: Leaving directory `/home/manic/etc/dl/gdl-0.9rc1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/manic/etc/dl/gdl-0.9rc1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/manic/etc/dl/gdl-0.9rc1'
make: *** [all] Error 2

I really have no idea what to do from here.  if anyone has any suggestions about next steps, i'm all ears

thanks!

---

### Post by normandin on 2008-10-31
do you need a custom build or just to get it installed?  gdl-0.9rc1 is available in intrepid's universe repos under 'gnudatalanguage', and gdl-0.9pre6 is available for hardy.

---

### Post by dphus on 2008-11-01
thanks normandin!

I would love to have a simple install and not compile my own version.  i can't seem to find gdl-0.9pre6 when i do a search in symantic ( i'm still on hardy), and "apt-get install gdl-0.9pre6" gives the "....couldn't find package..." message.  

I have my universe repository checked.  is there a different, perhaps 3rd party repository that i need to have enabled?  am i searching for the right thing?

Thanks for the help.

Here's the list of all the repositories that i have enabled in case there's something really simple that i'm missing.  

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy mai
n restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hardy universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main
manic@valdarius:~$

---

### Post by normandin on 2008-11-01
hi dphus,

sorry, the wording of my original post was misleading.  the gdl *package* is called 'gnudatalanguage' in both hardy and intrepid.  the *version* will be 0.9rc1 in intrepid and 0.9pre6 in hardy.  it looks like you've got the universe repos in your sources.lst, so
```
sudo aptitude install gnudatalanguage
```
should grab you gdl-0.9pre6.

---

### Post by dphus on 2008-11-01
Yup that did it.

thanks a million!  i don't know what i couldn't find that particular package.  

that just made my life a whole lot easier
Joe

---

### Post by darmok47 on 2009-04-21
hi, i have a problem with gdl. after installation with
apt-get install gnudatalanguage

i go in gdl and try to draw something, than the program reply something like

plstream error and exit

i also installed the latest version with plplot and the result is that the program says

device xwin is not available


i followed this guide that is for gdl 0.9pre4

[http://waterseven.universebox.com/?p=3](http://waterseven.universebox.com/?p=3)

but still dont work!

---

