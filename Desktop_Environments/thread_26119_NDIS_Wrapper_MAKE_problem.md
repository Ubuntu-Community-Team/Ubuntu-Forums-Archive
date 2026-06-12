---
title: "NDIS Wrapper MAKE problem"
date: 2005-04-11
forum: Desktop Environments
---

### Post by sparke67 on 2005-04-11
I am newbie and have been plodding along and I am  trying to get wireless working on my laptop I have the driver but I can not do the make and make install commends because I keep getting these error - I am not sure how to link this up to finish the build It must be simple to you guys but help is appreciated  [-o< 


root@shawnlinux:~/ndiswrapper-1.1 # make
make -C driver
make[1]: Entering directory `/home/sparke67/ndiswrapper-1.1/driver'
Can't find kernel sources in /lib/modules/2.6.8.1-3-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/sparke67/ndiswrapper-1.1/driver'
make: *** [all] Error 2
root@shawnlinux:~/ndiswrapper-1.1 #

---

### Post by az on 2005-04-12
Install build-essential and linux-headers

Read this:
[http://ubuntuforums.org/showthread.php?t=26079](http://ubuntuforums.org/showthread.php?t=26079)

---

### Post by sparke67 on 2005-04-12
[QUOTE=azz]Install build-essential and linux-headers

Read this:
[http://ubuntuforums.org/showthread.php?t=26079](http://ubuntuforums.org/showthread.php?t=26079)[/QUOTE]
 Thank you - I am new and I have downloaded them. How do I install ? do I just copy them to the directory ?

/lib/modules/2.6.8.1-5-386/build;

Sorry I fell dumb asking this since the other guy figured it out when you gave him the answer

---

### Post by az on 2005-04-12
cd Desktop (or to wherever you saved the files)
sudo dpkg -i *.deb

---

### Post by sparke67 on 2005-04-12
thank you now I am here and not sure what to do: I had gnomebaker installed and then it got messed up but more to the point - what should I do for ndiswrapper I have this now :

**root@shawnlinux:~ # dpkg -i *.deb**
(Reading database ... 70487 files and directories currently installed.)
Preparing to replace gnomebaker 0.3-3ubuntu1 (using gnomebaker_0.3-3ubuntu1_i386.deb) ...
Unpacking replacement gnomebaker ...
Preparing to replace ndiswrapper-modules-2.6.10-5-386 1.1-1 (using ndiswrapper-modules-2.6.10-5-386_1.1-1_i386.deb) ...
Unpacking replacement ndiswrapper-modules-2.6.10-5-386 ...
Preparing to replace ndiswrapper-utils 1.1-1 (using ndiswrapper-utils_1.1-1_i386.deb) ...
Unpacking replacement ndiswrapper-utils ...
dpkg: dependency problems prevent configuration of gnomebaker:
 gnomebaker depends on libatk1.0-0 (>= 1.9.0); however:
  Version of libatk1.0-0 on system is 1.8.0-1ubuntu2.
 gnomebaker depends on libgconf2-4 (>= 2.9); however:
  Version of libgconf2-4 on system is 2.8.1-0ubuntu1.
 gnomebaker depends on libglade2-0 (>= 1:2.5.1); however:
  Version of libglade2-0 on system is 1:2.4.0-1.
 gnomebaker depends on libglib2.0-0 (>= 2.6.0); however:
  Version of libglib2.0-0 on system is 2.4.7-0ubuntu2.
 gnomebaker depends on libgnomevfs2-0 (>= 2.9.90); however:
  Version of libgnomevfs2-0 on system is 2.8.2-0ubuntu1.
 gnomebaker depends on libgtk2.0-0 (>= 2.6.0); however:
  Version of libgtk2.0-0 on system is 2.4.10-1ubuntu1.1.
 gnomebaker depends on libogg0 (>= 1.1.2); however:
  Version of libogg0 on system is 1.1.0-1.
 gnomebaker depends on libpango1.0-0 (>= 1.8.1); however:
  Version of libpango1.0-0 on system is 1.6.0b-0ubuntu1.
 gnomebaker depends on libxml2 (>= 2.6.17); however:
  Version of libxml2 on system is 2.6.11-3ubuntu1.1.
dpkg: error processing gnomebaker (--install):
 dependency problems - leaving unconfigured
[B]Setting up ndiswrapper-utils (1.1-1) ...
Setting up ndiswrapper-modules-2.6.10-5-386 (1.1-1) ...
[/B]
Errors were encountered while processing:
 gnomebaker
root@shawnlinux

Thank you for your patience and help !!!

---

### Post by az on 2005-04-12
Two options:

sudo apt-get remove gnomebaker

or
sudo apt-get -f install
to try to resolve dependancy trouble.


The sl-modem stuff should work.

---

### Post by sparke67 on 2005-04-12
Thanks but same error - is my problem this ?

root@shawnlinux:~ # ls
53xx wireless Linux.zip
bcmwl5.inf
bcmwl5.sys
Desktop
DSCF0052.JPG
ep3_320.mov
gnomebaker_0.3-3ubuntu1_i386.deb
gnomebaker_0.3-3ubuntu1_i386.deb.1
gnomebaker_0.3-3ubuntu1_i386.deb.2
gnome-clipboard-daemon-1.0.bin.tar.bz2
install_flash_player_7_linux
install_flash_player_7_linux.tar.gz
lnxm310.tar.gz
ndiswrapper-1.1
ndiswrapper-1.1.tar.gz
ndiswrapper-modules-2.6.10-5-386_1.1-1_i386.deb
ndiswrapper-utils_1.1-1_i386.deb
thebling.jpg
ubuntu_mark2.xpm.gz
ubuntu_snow.xpm.gz
Unknown Artist
root@shawnlinux:~ # dpkg -i *.deb

Should I delete or move the gnome stuff here all together ? I am guessing that the ** dpkg -i *.deb** is still grabbing it ???

BTW all of a sudden gnomebaker shows up in the gnome menu  [-o<

---

### Post by az on 2005-04-12
No.  The packages are already installed.  It was my being sloppy to advise you to do *.deb in the fisrt place.  I assumed you had no other debs there.  It should have been ndiswrapper*.deb


Anyway, the ndiswrapper packages are installed, unless you removed them.  But you did not.  (you would have to go into synaptic and remove them, or apt-get remove....)

---

### Post by sparke67 on 2005-04-13
[QUOTE=azz]No.  The packages are already installed.  It was my being sloppy to advise you to do *.deb in the fisrt place.  I assumed you had no other debs there.  It should have been ndiswrapper*.deb


Anyway, the ndiswrapper packages are installed, unless you removed them.  But you did not.  (you would have to go into synaptic and remove them, or apt-get remove....)[/QUOTE]

Ok now I am stuck at the boot screen - I rebooted when I got home to try to do NDISwrapper and my machine will not boot past 

* configuring network interfaces 

oh geez do I have to reinstall - did I mess something up ?

if I leave it alone and unplug the ethernet it will eventually load but I can not get any network connection going  :-?  :-?


**** OOPS ID10T error -- I needed to reset my router at home --- most of the time following AZZZ instructions while at work  :roll: 

No back to trying to get wireless to work  :-#

---

### Post by sparke67 on 2005-04-13
[QUOTE=azz]No.  The packages are already installed.  It was my being sloppy to advise you to do *.deb in the fisrt place.  I assumed you had no other debs there.  It should have been ndiswrapper*.deb


Anyway, the ndiswrapper packages are installed, unless you removed them.  But you did not.  (you would have to go into synaptic and remove them, or apt-get remove....)[/QUOTE]
 **root@shawnlinux:~/ndiswrapper-1.1 # ls**
AUTHORS    debian  INSTALL   ndiswrapper.8     README  version
ChangeLog  driver  Makefile  ndiswrapper.spec  utils
**root@shawnlinux:~/ndiswrapper-1.1 # make distclean**
make -C driver clean
make[1]: Entering directory `/home/sparke67/ndiswrapper-1.1/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o pe_linker.o proc.o wrapper.o divdi3.o usb.o x86_64_stubs.o \
   divdi3.o .*.ko.cmd .*.o.cmd ndiswrapper.mod.[oc] *~ .tmp_versions
make[1]: Leaving directory `/home/sparke67/ndiswrapper-1.1/driver'
make -C utils clean
make[1]: Entering directory `/home/sparke67/ndiswrapper-1.1/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/sparke67/ndiswrapper-1.1/utils'
rm -f *~
rm -fr ndiswrapper-1.1 ndiswrapper-1.1.tar.gz *.deb patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/sparke67/ndiswrapper-1.1/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o pe_linker.o proc.o wrapper.o divdi3.o usb.o x86_64_stubs.o \
   divdi3.o .*.ko.cmd .*.o.cmd ndiswrapper.mod.[oc] *~ .tmp_versions
rm -f *_exports.h .\#* x86_64_stubs.h
make[1]: Leaving directory `/home/sparke67/ndiswrapper-1.1/driver'
make -C utils distclean
make[1]: Entering directory `/home/sparke67/ndiswrapper-1.1/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/sparke67/ndiswrapper-1.1/utils'
rm -f .\#*[B]
root@shawnlinux:~/ndiswrapper-1.1 # make[/B]
make -C driver
make[1]: Entering directory `/home/sparke67/ndiswrapper-1.1/driver'
Can't find kernel sources in /lib/modules/2.6.8.1-5-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/sparke67/ndiswrapper-1.1/driver'
make: *** [all] Error 2
root@shawnlinux:~/ndiswrapper-1.1 #

Man I am losing it !!!!! What am I doing wrong still ?

---

### Post by az on 2005-04-13
Use synaptic to look for ndiswrapper.  If you see that you have the two packages installed, then forget about the source.  Forget about the source anyway, since you already have the deb packages on your harddrive.


Just go on configuring your card.

sudo ndiswrapper -i <driver.inf>
sudo modprobe ndiswapper
ndiswrapper -l

---

### Post by sparke67 on 2005-04-13
[QUOTE=azz]Use synaptic to look for ndiswrapper.  If you see that you have the two packages installed, then forget about the source.  Forget about the source anyway, since you already have the deb packages on your harddrive.


Just go on configuring your card.

sudo ndiswrapper -i <driver.inf>
sudo modprobe ndiswapper
ndiswrapper -l[/QUOTE]
 Man you must never sleep thanks -- this is what I have now ....

root@shawnlinux:~ # sudo ndiswrapper -i bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
root@shawnlinux:~ # sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-5-386/kernel/drivers/ne t/ndiswrapper/ndiswrapper.ko): Invalid module format
root@shawnlinux:~ # ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
root@shawnlinux:~ #

No what ? thanks

rebooting .......

---

### Post by sparke67 on 2005-04-14
Bump AZZZ or someone else please help  ](*,)

---

### Post by Casey on 2005-04-15
Do you have linux-restricted-modules installed for your kernel?  Also did you install all of this via synaptic?  I found that that was easier than the compile-from-source method that I had to use when I previously needed the CVS version of ndiswrapper.

I believe that might be required for ndiswrapper (even though ndiswrapper itself is open).  I can't remember for sure.  I do recall having the exact problem you are having but I cannot recall how I fixed it...

---

### Post by sparke67 on 2005-04-15
[QUOTE=Casey]Do you have linux-restricted-modules installed for your kernel?  Also did you install all of this via synaptic?  I found that that was easier than the compile-from-source method that I had to use when I previously needed the CVS version of ndiswrapper.

I believe that might be required for ndiswrapper (even though ndiswrapper itself is open).  I can't remember for sure.  I do recall having the exact problem you are having but I cannot recall how I fixed it...[/QUOTE]
 I don't think so - I am new but I did alomost everything from the instructions at the ndiswarpper site. I have used the synaptic thing too when I was just experimenting and trying to get DVD playback to work -

Is there a way Ican tell if I am using linux restricted modules ? If there is a way to fix this I need it desperately - thanks everyone

---

### Post by az on 2005-04-15
The packages I made are for Hoary!

Here are some for Warty:
[http://www.vif.com/users/mzajac/ndiswrapper-modules_0.11-2.6.8.1-3-386_i386.deb](http://www.vif.com/users/mzajac/ndiswrapper-modules_0.11-2.6.8.1-3-386_i386.deb)
[http://www.vif.com/users/mzajac/ndiswrapper-utils_0.11_i386.deb](http://www.vif.com/users/mzajac/ndiswrapper-utils_0.11_i386.deb)

---

### Post by az on 2005-04-15
Sorry that I did not notice you were using Warty.  There are too many posts inthe forums for me to really look closesly.  Also, this is the Hoary applications support forum.  Anyway,

dpkg -i *0.11*.deb

should install the two packages, even if the other ones are in the same directory.

The thing is, I do not know why you are trying to compile the thing from source.  ndiswrapper is alreadypackaged for you and you just have to install it.  I was assuming that you needed a more recent versio than the one that is included on the Ubuntu cd....

anyway.

sudo ndiswrapper -l
that will list the drivers you have installed.  Remove them with
sudo ndiswrapper -e <driver>
and start over
sudo ndiswrapper -i <driver.inf>
sudo ndiswrapper -l
sudo modprobe ndiswrapper
Then, configure the interface in the networking gui.


If all works fine, add the word ndiswrapper to /etc/modules so that the modules loads every time you boot.

sudo gedit /etc/modules

---

### Post by sparke67 on 2005-04-15
Ok thanks and I swear when I know what I am doing I will help those coming behind me :::

This is what I have now :

sparke67@shawnlinux:~ $ sudo dpkg -i *0.11*.deb
Selecting previously deselected package ndiswrapper-modules.
(Reading database ... 70487 files and directories currently installed.)
Unpacking ndiswrapper-modules (from ndiswrapper-modules_0.11-2.6.8.1-3-386_i386.deb) ...
dpkg - warning: downgrading ndiswrapper-utils from 1.1-1 to 0.11.
Preparing to replace ndiswrapper-utils 1.1-1 (using ndiswrapper-utils_0.11_i386.deb) ...
Unpacking replacement ndiswrapper-utils ...
Setting up ndiswrapper-utils (0.11) ...
Setting up ndiswrapper-modules (0.11-2.6.8.1-3-386) ...

sparke67@shawnlinux:~ $ sudo ndiswrapper -l
Installed ndis drivers:
**bcmwl5  driver present, hardware present**
sparke67@shawnlinux:~ $ sudo ndiswrapper -e bcmwl5.inf
[B]Driver bcmwl5.inf is not installed. Use -l to list installed drivers
[/B]

??????? ](*,) 

Is it installed or not ????

---

### Post by az on 2005-04-15
[QUOTE=sparke67]Ok thanks and I swear when I know what I am doing I will help those coming behind me :::

This is what I have now :

sparke67@shawnlinux:~ $ sudo dpkg -i *0.11*.deb
Selecting previously deselected package ndiswrapper-modules.
(Reading database ... 70487 files and directories currently installed.)
Unpacking ndiswrapper-modules (from ndiswrapper-modules_0.11-2.6.8.1-3-386_i386.deb) ...
dpkg - warning: downgrading ndiswrapper-utils from 1.1-1 to 0.11.
Preparing to replace ndiswrapper-utils 1.1-1 (using ndiswrapper-utils_0.11_i386.deb) ...
Unpacking replacement ndiswrapper-utils ...
Setting up ndiswrapper-utils (0.11) ...
Setting up ndiswrapper-modules (0.11-2.6.8.1-3-386) ...

sparke67@shawnlinux:~ $ sudo ndiswrapper -l
Installed ndis drivers:
**bcmwl5  driver present, hardware present**
sparke67@shawnlinux:~ $ sudo ndiswrapper -e bcmwl5.inf
[B]Driver bcmwl5.inf is not installed. Use -l to list installed drivers
[/B]

??????? ](*,) 

Is it installed or not ????[/QUOTE]

sudo ndiswrapper -e bcmwl5

---

### Post by dglock on 2005-04-15
[QUOTE=sparke67]Ok thanks and I swear when I know what I am doing I will help those coming behind me :::

This is what I have now :

sparke67@shawnlinux:~ $ sudo dpkg -i *0.11*.deb
Selecting previously deselected package ndiswrapper-modules.
(Reading database ... 70487 files and directories currently installed.)
Unpacking ndiswrapper-modules (from ndiswrapper-modules_0.11-2.6.8.1-3-386_i386.deb) ...
dpkg - warning: downgrading ndiswrapper-utils from 1.1-1 to 0.11.
Preparing to replace ndiswrapper-utils 1.1-1 (using ndiswrapper-utils_0.11_i386.deb) ...
Unpacking replacement ndiswrapper-utils ...
Setting up ndiswrapper-utils (0.11) ...
Setting up ndiswrapper-modules (0.11-2.6.8.1-3-386) ...

sparke67@shawnlinux:~ $ sudo ndiswrapper -l
Installed ndis drivers:
**bcmwl5  driver present, hardware present**
sparke67@shawnlinux:~ $ sudo ndiswrapper -e bcmwl5.inf
[B]Driver bcmwl5.inf is not installed. Use -l to list installed drivers
[/B]

??????? ](*,) 

Is it installed or not ????[/QUOTE]

its installed. this line tells you  it is.

Installed ndis drivers:
[B]bcmwl5  driver present, hardware present[/

ndiswrapper doesn't install the .inf file, it installs the driver that the .inf file tells it to use.
use this command as root to verify.  ndiswrapper -l

don

---

### Post by sparke67 on 2005-04-15
thanks guys typing in the .inf was messing me up but now I am back to this:

sparke67@shawnlinux:~ $ sudo ndiswrapper -e bcmwl5
Password:
sparke67@shawnlinux:~ $ sudo ndiswrapper -l
No drivers installed
sparke67@shawnlinux:~ $ sudo ndiswrapper -i bcmwl5.inf
Installing bcmwl5
sparke67@shawnlinux:~ $ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
sparke67@shawnlinux:~ $ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid module format
sparke67@shawnlinux:~ $

do I have to reinstall the OS because I have messed something up so bad ? It was a mission to get DVD working but I need wireless to work for my project for work

---

### Post by az on 2005-04-15
Okay.

You are a moving target.

1.  This being the Hoary forum, I mistakenly guided you to a Hoary kernel version of the drivers.  They will not work for you unless you are using a Hoary kernel.
2.  Looking at your original post I saw "Can't find kernel sources in /lib/modules/2.6.8.1-3-386/build;"  Which is the stock Warty kernel.  No problem - I built modules for that too, months ago.  I assumed that you do not have internet access because your wireless does not work.
3.  You probably do have internet access and probably have an up-to-date system which mean that the kernel has undergone some revisions.  You are running an updated Warty kernel which is incompatible with the modules I made.  Just to be sure, post your
uname -a

Install build-essential and linux-headers (the version which corresponds to the kernel you are running - see the output of uname -a)

cd into the ndiswrapper source directory
sudo make clean
debian/rules binary
cd ..
install the ndiswrapper .deb packages you just built.



This is me running away screaming...



AAAAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa!

---

### Post by sparke67 on 2005-04-16
[QUOTE=azz]Okay.

You are a moving target.

1.  This being the Hoary forum, I mistakenly guided you to a Hoary kernel version of the drivers.  They will not work for you unless you are using a Hoary kernel.
2.  Looking at your original post I saw "Can't find kernel sources in /lib/modules/2.6.8.1-3-386/build;"  Which is the stock Warty kernel.  No problem - I built modules for that too, months ago.  I assumed that you do not have internet access because your wireless does not work.
3.  You probably do have internet access and probably have an up-to-date system which mean that the kernel has undergone some revisions.  You are running an updated Warty kernel which is incompatible with the modules I made.  Just to be sure, post your
uname -a

Install build-essential and linux-headers (the version which corresponds to the kernel you are running - see the output of uname -a)

cd into the ndiswrapper source directory
sudo make clean
debian/rules binary
cd ..
install the ndiswrapper .deb packages you just built.



This is me running away screaming...



AAAAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa![/QUOTE]

COME BACK !!!!! [-X  :smile:  :) 

sparke67@shawnlinux:~ $ uname -a
Linux shawnlinux 2.6.8.1-5-386 #1 Thu Apr 7 08:47:11 UTC 2005 i686 GNU/Linux
sparke67@shawnlinux:~ $

I'll wait for you to come back before I type anything else .....

---

### Post by az on 2005-04-16
[QUOTE=sparke67]COME BACK !!!!! [-X  :smile:  :) 

sparke67@shawnlinux:~ $ uname -a
Linux shawnlinux 2.6.8.1-5-386 #1 Thu Apr 7 08:47:11 UTC 2005 i686 GNU/Linux
sparke67@shawnlinux:~ $

I'll wait for you to come back before I type anything else .....[/QUOTE]


Install build-essential and linux-headers (the version which corresponds to the kernel you are running - see the output of uname -a)

cd into the ndiswrapper source directory
sudo make clean
debian/rules binary
cd ..
install the ndiswrapper .deb packages you just built.

---

### Post by sparke67 on 2005-04-16
Thanks fir hanging in there with me  O:) 

sparke67@shawnlinux:~ $ sudo apt-get install build-essential
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: gcc (>= 3:3.3) but it is not going to be installed
                   Depends: g++ (>= 3:3.3) but it is not going to be installed
  gnomebaker: Depends: libatk1.0-0 (>= 1.9.0) but 1.8.0-1ubuntu2 is to be installed
              Depends: libgconf2-4 (>= 2.9) but 2.8.1-0ubuntu1 is to be installed
              Depends: libglade2-0 (>= 1:2.5.1) but 1:2.4.0-1 is to be installed              Depends: libglib2.0-0 (>= 2.6.0) but 2.4.7-0ubuntu2 is to be installed
              Depends: libgnomevfs2-0 (>= 2.9.90) but 2.8.2-0ubuntu1 is to be installed
              Depends: libgtk2.0-0 (>= 2.6.0) but 2.4.10-1ubuntu1.1 is to be installed
              Depends: libogg0 (>= 1.1.2) but 1.1.0-1 is to be installed
              Depends: libpango1.0-0 (>= 1.8.1) but 1.6.0b-0ubuntu1 is to be installed
              Depends: libxml2 (>= 2.6.17) but 2.6.11-3ubuntu1.1 is to be installed
  ndiswrapper-modules-2.6.10-5-386: Depends: ndiswrapper-utils-1.1 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

If I do apt-get -f I lose my gnomebaker and then I am still stuck again if I get the same results as last time I went done this road --- what am I doing wrong now ? ](*,)

I went to synaptic and chose to fix broken dependancies and say it unsintalled gnomebaker and re ran :::

sparke67@shawnlinux:~ $ sudo apt-get install build-essential
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
  g++ g++-3.3 gcc gcc-3.3 libstdc++5-3.3-dev
Suggested packages:
  gcc-3.3-doc manpages-dev autoconf automake libtool flex bison gcc-doc
  libstdc++5-3.3-doc stl-manual
The following NEW packages will be installed:
  build-essential g++ g++-3.3 gcc gcc-3.3 libstdc++5-3.3-dev
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4128kB of archives.
After unpacking 13.2MB of additional disk space will be used.
Do you want to continue? [Y/n] y

Preconfiguring packages ...
Selecting previously deselected package gcc-3.3.
(Reading database ... 70416 files and directories currently installed.)
Unpacking gcc-3.3 (from .../gcc-3.3_1%3a3.3.4-9ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a3.3.4-1_i386.deb) ...
Selecting previously deselected package libstdc++5-3.3-dev.
Unpacking libstdc++5-3.3-dev (from .../libstdc++5-3.3-dev_1%3a3.3.4-9ubuntu5_i386.deb) ...
Selecting previously deselected package g++-3.3.
Unpacking g++-3.3 (from .../g++-3.3_1%3a3.3.4-9ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a3.3.4-1_i386.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_10ubuntu1_i386.deb) ...
Setting up gcc-3.3 (3.3.4-9ubuntu5) ...
Setting up gcc (3.3.4-1) ...

Setting up libstdc++5-3.3-dev (3.3.4-9ubuntu5) ...
Setting up g++-3.3 (3.3.4-9ubuntu5) ...
Setting up g++ (3.3.4-1) ...

Setting up build-essential (10ubuntu1) ...
sparke67@shawnlinux:~ $

Am I ok to proceed from here ?

I went ahead and now have :

sparke67@shawnlinux:~ $ sudo apt-get install linux-headers 2.6.8.1-5-386
Reading Package Lists... Done
Building Dependency Tree... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.8.1-5-k7-smp 2.6.8.1-16.14
  linux-headers-2.6.8.1-5-k7 2.6.8.1-16.14
  linux-headers-2.6.8.1-5-686-smp 2.6.8.1-16.14
  linux-headers-2.6.8.1-5-686 2.6.8.1-16.14
  linux-headers-2.6.8.1-5-386 2.6.8.1-16.14
  linux-headers-2.6.8.1-5 2.6.8.1-16.14
  linux-headers-2.6.8.1-4-k7-smp 2.6.8.1-16.10
  linux-headers-2.6.8.1-4-k7 2.6.8.1-16.10
  linux-headers-2.6.8.1-4-686-smp 2.6.8.1-16.10
  linux-headers-2.6.8.1-4-686 2.6.8.1-16.10
  linux-headers-2.6.8.1-4-386 2.6.8.1-16.10
  linux-headers-2.6.8.1-4 2.6.8.1-16.10
  linux-headers-2.6.8.1-3-k7-smp 2.6.8.1-16.1
  linux-headers-2.6.8.1-3-k7 2.6.8.1-16.1
  linux-headers-2.6.8.1-3-686-smp 2.6.8.1-16.1
  linux-headers-2.6.8.1-3-686 2.6.8.1-16.1
  linux-headers-2.6.8.1-3-386 2.6.8.1-16.1
  linux-headers-2.6.8.1-3 2.6.8.1-16.1
You should explicitly select one to install.
E: Package linux-headers has no installation candidate
sparke67@shawnlinux:~ $

---

### Post by sparke67 on 2005-04-16
sparke67@shawnlinux:~ $ uname -a Linux shawnlinux 2.6.8.1-5-386 #1 Thu Apr 7 08:47:11 UTC 2005 i686 GNU/Linux


sparke67@shawnlinux:~ $ sudo apt-get install linux-headers-2.6.8.1-5-386 2.6.8.1-16.14
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package 2.6.8.1-16.14
sparke67@shawnlinux:~ $

 ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by dglock on 2005-04-16
[QUOTE=sparke67]sparke67@shawnlinux:~ $ uname -a Linux shawnlinux 2.6.8.1-5-386 #1 Thu Apr 7 08:47:11 UTC 2005 i686 GNU/Linux


sparke67@shawnlinux:~ $ sudo apt-get install linux-headers-2.6.8.1-5-386 2.6.8.1-16.14
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package 2.6.8.1-16.14
sparke67@shawnlinux:~ $

 ](*,)  ](*,)  ](*,)  ](*,)  ](*,)[/QUOTE]

go to suse 9.3, it has support for your card right out of the box. all you have to do is put in the info for your accesss point.

wireless problems are the main reason i gave up on both ubuntu and xandros.
don

---

### Post by az on 2005-04-16
The arguments for apt-get install are <package1> <package2> <package3>

"linux-headers-2.6.8.1-5-386" is a valid package name, 
"2.6.8.1-16.14" is not.

Carry on....

---

### Post by sparke67 on 2005-04-17
[QUOTE=azz]The arguments for apt-get install are <package1> <package2> <package3>

"linux-headers-2.6.8.1-5-386" is a valid package name, 
"2.6.8.1-16.14" is not.

Carry on....[/QUOTE]

Duh - I forgot the - between headers and 2.6.8.1-5-386 !!!!!

The following NEW packages will be installed:
  linux-headers-2.6.8.1-5 linux-headers-2.6.8.1-5-386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3498kB of archives.
After unpacking 43.4MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main linux-headers-2.6.8.1-5 2.6.8.1-16.14 [3220kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main linux-headers-2.6.8.1-5-386 2.6.8.1-16.14 [277kB]
Fetched 3498kB in 8s (427kB/s)

Preconfiguring packages ...
Selecting previously deselected package linux-headers-2.6.8.1-5.
(Reading database ... 70712 files and directories currently installed.)
Unpacking linux-headers-2.6.8.1-5 (from .../linux-headers-2.6.8.1-5_2.6.8.1-16.14_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.8.1-5-386.
Unpacking linux-headers-2.6.8.1-5-386 (from .../linux-headers-2.6.8.1-5-386_2.6.8.1-16.14_i386.deb) ...The following NEW packages will be installed:
  linux-headers-2.6.8.1-5 linux-headers-2.6.8.1-5-386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3498kB of archives.
After unpacking 43.4MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main linux-headers-2.6.8.1-5 2.6.8.1-16.14 [3220kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main linux-headers-2.6.8.1-5-386 2.6.8.1-16.14 [277kB]
Fetched 3498kB in 8s (427kB/s)

Preconfiguring packages ...
Selecting previously deselected package linux-headers-2.6.8.1-5.
(Reading database ... 70712 files and directories currently installed.)
Unpacking linux-headers-2.6.8.1-5 (from .../linux-headers-2.6.8.1-5_2.6.8.1-16.14_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.8.1-5-386.
Unpacking linux-headers-2.6.8.1-5-386 (from .../linux-headers-2.6.8.1-5-386_2.6.8.1-16.14_i386.deb) ...
Setting up linux-headers-2.6.8.1-5 (2.6.8.1-16.14) ...

Setting up linux-headers-2.6.8.1-5-386 (2.6.8.1-16.14) ...
sparke67@shawnlinux:~ $

YES --- holding my breath :-)

---

### Post by az on 2005-04-17
Noe build and install 


cd into the ndiswrapper source directory
sudo make clean
debian/rules binary
cd ..
install the ndiswrapper .deb packages you just built.

---

### Post by az on 2005-04-17
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

---

### Post by sparke67 on 2005-04-17
[QUOTE=azz][http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)[/QUOTE]

thanks you I feel like I am almost there .. but of course its me so .....
following those directions to this point ....

1. Copy the bcmwl5.inf to your desktop

2. Follow the advice given here under How to add extra repositories

3. Open a terminal session and enter this code
Code:
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
4. Reboot your PC. On restarting

I get this :

sparke67@shawnlinux:~ $ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
sparke67@shawnlinux:~ $ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4307.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4321.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.conf: Permission denied
sparke67@shawnlinux:~ $
 ](*,)

re ran as root and now 
sparke67@shawnlinux:~ $ sudo modprobe ndiswrapper
Password:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid module format
sparke67@shawnlinux:~ $

---

### Post by az on 2005-04-17
Since you have broadband internet (I assume) can you just dist-upgrade to Hoary?

That will solve your problems.  Remove ndiswrapper-utils, first and then reinstall it from synaptic (hoary repo, not the one you made)

---

### Post by sparke67 on 2005-04-18
[QUOTE=azz]Since you have broadband internet (I assume) can you just dist-upgrade to Hoary?

That will solve your problems.  Remove ndiswrapper-utils, first and then reinstall it from synaptic (hoary repo, not the one you made)[/QUOTE]

Yeah I have fast connection - if you follow the other thread - you see that others are having the same problem that I am --- I feel a little better now ....

Some things that it has to do with the Diff btw release candidate and Hoary and other dist ?

Hmmm ...


Is the order to try ?

1. dist-upgrade to Hoary
2. remove ndiswapper-utils
3. reinstall from Synaptic - Hoary

---

### Post by az on 2005-04-18
Your card will work.  Most people do not have any problem.  You just need matching ndiswrapper modules and utils.  This has been screwed up on you system but can be fixed by removing, distupgading and then installing ndiswrapper-utils again.

---

### Post by sparke67 on 2005-04-18
Oh God !!! The nightmare is over.

All I did was remove NDISWRAPPER via synaptic. 
Reboot and re add it again !!
I re ran modprobe and  BOOM the lights show up at 100 % signal strength !!
All is re ran dmesg and it shows there also.

I did notice that after re installing ndiswrapper via synaotic I got different prompt about the the drivers not being supported by Ubuntu !!!

Thanks everyone who got me thinking along the right path -- especially  AZZ my hero.

Here is the  I had in terminal - edited of course for length

sparke67@shawnlinux:~ $ sudo ndiswrapper -l 
Password:
WARNING:
This tool allows you to use a driver written for the Windows operating
system on Ubuntu. Please note that the use of such drivers is entirely
unsupportable by the Ubuntu team, and not recommended, even if it is
theoretically possible with this tool.

Installed ndis drivers:
bcmwl5  hardware present
sparke67@shawnlinux:~ $ sudo ndiswrapper -i bcmwl5.inf 

WARNING:
This tool allows you to use a driver written for the Windows operating
system on Ubuntu. Please note that the use of such drivers is entirely
unsupportable by the Ubuntu team, and not recommended, even if it is
theoretically possible with this tool.

bcmwl5 is already installed. Use -e to remove it

sparke67@shawnlinux:~ $ sudo modprobe ndiswrapper 

sparke67@shawnlinux:~ $ dmesg
Linux version 2.6.8.1-5-386 (buildd@rothera) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Thu Apr 7 08:47:11 UTC 2005

CPU: AMD Mobile AMD Athlon(tm) XP 2400+ stepping 00
Enabling fast FPU save and restore... done.

blah blah blah .......

wlan0: ndiswrapper ethernet device 00:90:96:70:d3:68 using driver bcmwl5.sys
ndiswrapper device wlan0 supports WPA with AES/CCMP and TKIP ciphers
ndiswrapper: driver bcmwl5.sys (Broadcom,06/13/2003, 3.20.23.0) added
sparke67@shawnlinux:~ $

---

### Post by az on 2005-04-18
<CLAP CLAP CLAP>







...jumping of a cliff, now...

---

### Post by sparke67 on 2005-04-18
[QUOTE=azz]<CLAP CLAP CLAP>







...jumping of a cliff, now...[/QUOTE]

Noooo dont !!!

Sincerely thanks for all your help. I never did upgrade to Haory but you directions got me to thinking in a more logical path.

I have posted this in the other Broadcom wireless thread in the hopes it helps someone else ......

Next stop SAMBA - !!!!! so don't you die on me !!!

---

