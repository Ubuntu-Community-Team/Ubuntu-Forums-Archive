---
title: "IRAF on Ubuntu 11.04 amd64 (64 bits)"
date: 2011-05-12
forum: Education &amp; Science
---

### Post by dmfaes on 2011-05-12
Hello everybody!

Recently I have installed the IRAF 2.15.1a on my Ubuntu 11.04 amd64 (64 bits). But I got some problems running specific tasks from STSDAS 3.13 (so far, only x86). 

So, I tried to install the IRAF 2.14 version and I could not install. That's because "libc5" of Ubuntu is not working for IRAF. 

So I would like to know if someone already has managed to install the IRAF 2.14 on Ubuntu 11.04 amd64.

Thank you,
Daniel

---

### Post by favilac on 2011-05-13
I have an installer for IRAF. It works on 32 and 64 bits.
It includes

        IRAF                 2.14.1
        STSDAS               3.13
        TABLES               3.13
        PyRAF                1.9
        DS9                  6.2
        X11IRAF              2.0BETA
        WCSTOOLS             3.8.1
        Telarchive           1.6.1
        PHIST                2.0
        STECF                1.5
        FV                   5.3
        XVISTA               7.10
        PLCREATE             1.0
        GEMINI               1.10

You can download the .iso from
[http://www.astro.uson.mx/favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso]("http://www.astro.uson.mx/favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso")

---

### Post by dmfaes on 2011-05-13
Hi favilac,

Are you sure that works on 64 bits version of ubuntu 11.04?
Because for me its not working...

Regards,
Dmfaes

---

### Post by apopovas on 2011-06-06
Hello, I have the same problem and am trying to solve it for some time now without any success

---

### Post by favilac on 2011-06-07
... if you put the error you are getting it will be much easier to help.

---

### Post by Dreamsfear on 2011-06-11
I'm extremely new to Ubuntu and linux altogether and I wont lie, I have very little understanding atm linux wise. Much more of a hardware person at the moment. Hopefully that's all soon to change. None the less one of the reasons for me switching to ubuntu is for my degree, I find myself beginning to use IRAF myself and I tried installing through this ISO and here is the errors it thrown my way. Now it could very well be my fault but here we are:

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 145548 files and directories currently installed.)
Preparing to replace ldso:i386 1.9.11-15 (using deb/ldso_1.9.11-15_i386.deb) ...
Unpacking replacement ldso:i386 ...
dpkg: dependency problems prevent configuration of ldso:i386:
 ldso:i386 depends on libc6 (>= 2.1.94).
dpkg: error processing ldso:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ldso:i386


if it's something stupid on my part please feel free to let me know because what better way to learn what exactly I am doing.

---

### Post by dmfaes on 2011-06-11
Hi dreamsfear,
On ubuntu 11.04 until now you have two options to run IRAF:
1) 32bits version of ubuntu, so you can use the ISO you mentioned
2) 64bits version of ubuntu, with IRAF 2.15.1a from iraf.net

The ISO will not work at 64bits!
Regards

---

### Post by favilac on 2011-06-11
It works in 64 bits, and has been working for over 3 years since I started (Ubuntu 8.04).

Now, this problem in particular is weird.

It's complaining that libc6 is not installed, but the installer pulls libc6-dev as a dependency which in turn should pull libc6 and is not doing it.

Try doing a "apt-get install libc6" before running the installer and let me know what happens.

One final note, research workstations usually run the same software for years. In this case, the script is developed in Ubuntu LTS which is supported for three years. I strongly recomend for this reason and others to stay in LTS versions for work that depends on consistency.

---

### Post by DarkTide on 2011-06-11
I have got the same problem. Does any one have a solution for it???
Thanks

---

### Post by Dreamsfear on 2011-06-12
After reading up a bit on ubuntu I decided to just do a clean install of the 32 bit version. After reading all the problems I just felt it would be the smarter move in all honesty but I'm gonna give this another shot so heres to hoping.

---

### Post by IraGainesUK on 2011-08-14
I also get the same error as above on 64-bit Ubuntu 11.04.

For what it's worth to anyone else trying to install this, I managed to get IRAF to install by editing the 'install.sh' file within the above .iso file.

Place a '#' at the start of the two lines that start 'dpkg -i ...  ldso...' and 'dpkg -i ... libc5...' on lines 37/38 or 47/48 depending on your architecture (32-bit/64-bit respectively).

This will allow the script to successfully install IRAF, although probably breaking a few things along the way.  All I want to use IRAF for is the ellipse routine however, and I can confirm this works, so I'm happy.  Using this .iso for IRAF install is still a lot easier than trying to follow the joke install instructions on the IRAF website!

Good luck!

---

### Post by radioboy on 2011-08-23
I suggest reading these notes regarding 64-bit IRAF (v2.15) :)

[http://www.stsci.edu/resources/software_hardware/stsdas/iraf64]("http://www.stsci.edu/resources/software_hardware/stsdas/iraf64")

---

### Post by favilac on 2011-08-28
NEW INSTALLER!!!

It has the new STSCI_IRAF with TABLES 3.14, STSDAS 3.14 and STECF.

The new version now supports Ubuntu 11.04 AMD 64 (the previous bug has been fixed and several symlinks corrected, as far as I can tell).

To install you must run first the uninstall script included in this version, because the packages ldso, libc5 and termcap_compat are not needed anymore (thanks IraGainesUK for the insight!).

The installer in the same place as always:

[http://www.astro.uson.mx/favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso]("http://www.astro.uson.mx/favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso")

Test away!!

---

### Post by abdulras on 2011-10-10
Just so people know,the ISO works for my Ubuntu 11.04(64bits).I dont know why exactly people are saying its not.

---

### Post by gimpeller on 2011-11-29
favilac

Thanks for the installer! Everything works fine! And perhaps add a MSCRED package in IRAF. If you add in the installer ESO-MIDAS and IDL, it would be a great alternative Scisoft, but only for Ubuntu. It would be great!!!!!!

---

### Post by favilac on 2011-11-30
>add a MSCRED package in IRAF. 
Done!

>If you add in the installer ESO-MIDAS
Haven't used MIDAS, so for the moment have no idea how feasible is this.

>and IDL
IDL is a propietary system, and needs a license from the company to run. Therefore, it's not legally possible to include it.

Also, the new version I have uploaded now, doesn't need the iraf user. For this reason you must run the uninstall-previous.sh script to delete the previous version and iraf user before you can install the new one.

---

### Post by gimpeller on 2011-12-01
favilac

Excellent! Now I can do data processing and science:guitar:, instead of the "Kama Sutra with Linux programm installation" :)


Thank you very much! What you are doing is really important!

---

### Post by bromhide on 2012-02-02
I have no problem running the install script, but get Ioads of "unmet dependencies" errors. Anyone else with similar issues or know what they are indicative of? 

Thanks in advance for your help!

---

### Post by favilac on 2012-02-03
bromhide>

Have you done an "apt-get update" first?
Are the universe and multiverse repos enabled?

---

### Post by mihalybaci on 2012-02-20
I haven't used it myself, but there is also PyRAF, a python implementation of IRAF. For those of you who know some python it may be easier to install/run.

[http://www.stsci.edu/institute/software_hardware/pyraf](http://www.stsci.edu/institute/software_hardware/pyraf)

---

### Post by favilac on 2012-02-20
PyRAF is an extension shell to IRAF, so you need IRAF installed first.

PyRAF is an alternate shell to the standard ECL that IRAF uses.
Also, it has pyhton bindings so you can include IRAF routines in your python code.

---

### Post by gimpeller on 2012-07-02
A new version of SAO DS9 :p:
 [http://hea-www.harvard.edu/RD/ds9/site/Download.html](http://hea-www.harvard.edu/RD/ds9/site/Download.html)

---

