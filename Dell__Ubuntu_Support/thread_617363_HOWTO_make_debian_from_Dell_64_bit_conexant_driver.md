---
title: "HOWTO make debian from Dell 64 bit conexant driver"
date: 2007-11-19
forum: Dell  Ubuntu Support
---

### Post by Paul S on 2007-11-19
It's possible to make a ubuntu (debian) package from the hsfmodem source that Dell is providing for the amd64 (64 bit) system architecture.

1. Download it:

```
wget -c http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem-7.60.00.18x86_64oem.tar.gz

```
2. You also need the pdf version of the hsfmodem documentation from linuxant.  You can down load it using:

```
wget -c http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.68.00.04full/100498D_RM_HxF_Released.pdf

```
3. You also need all the debian package build scripts installed. Make sure you enable the Universe respository.  Then do:
```

sudo aptitude install debmake fakeroot build-essential dpkg-dev

```
4. Make a build directory in your home directory:

```
mkdir bld.hsfmodem

```
5. Enter the build directory and untar the source:

```
cd bld.hsfmodem
tar xzvf ../hsfmodem-7.60.00.18x86_64oem.tar.gz

```
6. Copy the pdf doc into this directory:

```
cp ../100498D_RM_HxF_Released.pdf hsfmodem-7.60.00.18x86_64oem

```
7. Enter the hsf directory and build the package:

```
cd hsfmodem-7.60.00.18x86_64oem
fakeroot make debdist

```
NOTE: IF YOU GET ANY ERROR MESSAGE AND THE BUILD FAILS, COPY THE EXACT MESSAGE AND REPORT BACK HERE.  IT'S PROBABLY BECAUSE YOU ARE MISSING SOME PACKAGE THAT I FORGOT TO LIST IN THE PREPARATION STEP 3.  FOR EXAMPLE, THE FIRST TIME I DIDN'T HAVE debmake INSTALLED AND I GOT THE FOLLOWING ERROR:

make[1]: debstd: Command not found
make[1]: *** [binary-arch] Error 127

SO, IF YOU GET SOMETHING LIKE THAT, REPORT BACK AND I'LL HELP FIGURE OUT WHICH PACKAGE YOU NEED.  IT'S EASY TO CHECK AT [http://packages.ubuntu.com/](http://packages.ubuntu.com/).  I JUST SEARCHED FOR debstd AND FOUND IT IS IN debmake.

8. A successful build will leave the package in the subdirectory packages/DEBS/amd64/hsfmodem_7.60.00.18x86-64oem_amd64.deb  Install it:

```
sudo dpkg -i packages/DEBS/amd64/hsfmodem_7.60.00.18x86-64oem_amd64.deb

```
It works fine here, hope you have success also.

---

### Post by curley_sue on 2008-04-30
Thanks for the howto - it is really clear BUT - 
It does not work for me on hardy:


debstd BUGS CHANGES CREDITS FAQ INSTALL LICENSE README 100498D_RM_HxF_Released.pdf
make[1]: debstd: Command not found
make[1]: *** [binary-arch] Error 127
make[1]: Leaving directory `/home/eldad/amministrazione/modem/bld.hsfmodem/hsfmodem-7.60.00.18x86_64oem'
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
rm -f debian/target.mak
mv ../hsfmodem_*.deb packages/DEBS/amd64/hsfmodem_7.60.00.18x86-64oem_amd64.deb
mv: cannot stat `../hsfmodem_*.deb': No such file or directory
make: *** [packages/DEBS/amd64/hsfmodem_7.60.00.18x86-64oem_amd64.deb] Error 1

---

### Post by Paul S on 2008-04-30
> **curley_sue said:**
> Thanks for the howto - it is really clear BUT - 
It does not work for me on hardy:


Dell hasn't released the new modem driver for hardy yet.  Check out the Dell wiki for status:  [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Driver_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Driver_Does_Not_Work)

regards,

---

### Post by hasta2003 on 2008-05-09
I have the same problem. But, why there is a Hardy directory on Dell's modem page? [http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/)

cheers

---

### Post by Paul S on 2008-05-10
> **hasta2003 said:**
> there is a Hardy directory on Dell's modem page? [http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/)


It just came out.  I gave it a try and it failed here (modem busy) and also killed sound.  Then, I noticed this thread on the Dell area:

[http://ubuntuforums.org/showthread.php?p=4927953&posted=1#post4927953](http://ubuntuforums.org/showthread.php?p=4927953&posted=1#post4927953)

After installing the alsa-driver-linuxant deb and rebooting, then the hsfmodem deb, then rebooting, sound and modem now work.

The alsa-driver-linuxant deb is all architectures, so should work with 64 bit too.  I'm running 32 bit so can't test it.

regards,

---

### Post by hasta2003 on 2008-05-11
thanks, it works for me: [http://ubuntuforums.org/showthread.php?p=4931849&posted=1#post4931849](http://ubuntuforums.org/showthread.php?p=4931849&posted=1#post4931849)

cheers :)

---

