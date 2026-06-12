---
title: "Help with program R of r-cran project"
date: 2010-05-23
forum: Education &amp; Science
---

### Post by rpgki on 2010-05-23
Hello everyone, I have installed R on my computer and i cant install any package from cran, only the ones from ubuntu repositories, so i need help in this, and maybe you can help me.
For example I have installed Rcmdr from ubuntu repos because i cant from cran and when I open R y write library(Rcmdr), it opens normally but it says that it needs this packages "leaps" and "aplpack", so I did this steps:

$sudo R

and when R opens I type

install.packages("aplpack", dep=T)
(A lot of words goes here)
and i get this:
Aviso en install.packages("aplpack", dep = T) :
 
The downloaded packages are in
	‘/tmp/Rtmp1aY55A/downloaded_packages’
Mensajes de aviso perdidos
In install.packages("aplpack", dep = T) :
  installation of package 'aplpack' had non-zero exit status


The same happens with 
>install.packages("leaps", dep=T)

Thanks for your attention, and have a nice day.

---

### Post by akniss on 2010-05-23
> **rpgki said:**
> Hello everyone, I have installed R on my computer and i cant install any package from cran, only the ones from ubuntu repositories, so i need help in this, and maybe you can help me.
For example I have installed Rcmdr from ubuntu repos because i cant from cran and when I open R y write library(Rcmdr), it opens normally but it says that it needs this packages "leaps" and "aplpack", so I did this steps:

$sudo R

and when R opens I type

install.packages("aplpack", dep=T)
(A lot of words goes here)
and i get this:
Aviso en install.packages("aplpack", dep = T) :
 
The downloaded packages are in
	‘/tmp/Rtmp1aY55A/downloaded_packages’
Mensajes de aviso perdidos
In install.packages("aplpack", dep = T) :
  installation of package 'aplpack' had non-zero exit status


The same happens with 
>install.packages("leaps", dep=T)

Thanks for your attention, and have a nice day.

Try first installing the build-essential package on your ubuntu system.
```
sudo apt-get install build-essential
```
then re-run R as sudo and try the install.packages command.

---

### Post by rpgki on 2010-05-23
thanks for the answer, I forgot to say that im running ubuntu 10.04 in spanish, so I tried it and it didn't work, i translated what it says in google.

```
solisbros @ carlos-desktop: ~ $ sudo apt-get install build-essential
Reading package lists ... Fact
Building dependency tree
Reading state information ... Fact
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Again, thanks for your help and answer.

---

### Post by akniss on 2010-05-23
> **rpgki said:**
> (A lot of words goes here)
Please post the entire output when you get the non-zero exit status. There will probably be some clues as to what is going wrong.

---

### Post by rpgki on 2010-05-23
oh yeah, sorry
```
> install.packages("Runit", dep=T)
Aviso en install.packages("Runit", dep = T) :
 argument 'lib' is missing: using '/usr/local/lib/R/site-library'
Mensajes de aviso perdidos
1: In getDependencies(pkgs, dependencies, available, lib) :
  package ‘Runit’ is not available
2: Perhaps you meant ‘RUnit’ ? 
> install.packages("RUnit", dep=T)
Aviso en install.packages("RUnit", dep = T) :
 argument 'lib' is missing: using '/usr/local/lib/R/site-library'
probando la URL 'http://cran.fhcrc.org/src/contrib/RUnit_0.4.25.tar.gz'
Content type 'application/x-gzip' length 244085 bytes (238 Kb)
URL abierta
==================================================
downloaded 238 Kb

*** buffer overflow detected ***: /usr/lib/R/bin/exec/R terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x1f2350]
/lib/tls/i686/cmov/libc.so.6(+0xe128a)[0x1f128a]
/lib/tls/i686/cmov/libc.so.6(+0xe33e1)[0x1f33e1]
/usr/lib/R/lib/libR.so(+0x7f0aa)[0x5460aa]
/usr/lib/R/lib/libR.so(+0x7f745)[0x546745]
/usr/lib/R/lib/libR.so(+0x114cdd)[0x5dbcdd]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(Rf_applyClosure+0x300)[0x592a90]
/usr/lib/R/lib/libR.so(Rf_eval+0x3fd)[0x58eafd]
/usr/lib/R/lib/libR.so(+0xc917f)[0x59017f]
/usr/lib/R/lib/libR.so(Rf_eval+0x64b)[0x58ed4b]
/usr/lib/R/lib/libR.so(+0xc917f)[0x59017f]
/usr/lib/R/lib/libR.so(Rf_eval+0x64b)[0x58ed4b]
/usr/lib/R/lib/libR.so(+0xfd576)[0x5c4576]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(+0xfd3d1)[0x5c43d1]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(+0xfd3d1)[0x5c43d1]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(+0xfd3d1)[0x5c43d1]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(+0xfd3d1)[0x5c43d1]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(+0xfd3d1)[0x5c43d1]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(+0xcacc4)[0x591cc4]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(+0xca0e0)[0x5910e0]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(Rf_applyClosure+0x300)[0x592a90]
/usr/lib/R/lib/libR.so(+0x117d81)[0x5ded81]
/usr/lib/R/lib/libR.so(Rf_usemethod+0x958)[0x5df8d8]
/usr/lib/R/lib/libR.so(+0x118fb4)[0x5dffb4]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(Rf_applyClosure+0x300)[0x592a90]
/usr/lib/R/lib/libR.so(Rf_eval+0x3fd)[0x58eafd]
/usr/lib/R/lib/libR.so(+0xc80a9)[0x58f0a9]
/usr/lib/R/lib/libR.so(Rf_eval+0x21b)[0x58e91b]
/usr/lib/R/lib/libR.so(+0x117a29)[0x5dea29]
/usr/lib/R/lib/libR.so(+0x119137)[0x5e0137]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(Rf_applyClosure+0x300)[0x592a90]
/usr/lib/R/lib/libR.so(Rf_eval+0x3fd)[0x58eafd]
/usr/lib/R/lib/libR.so(+0xca02a)[0x59102a]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(+0xcaf38)[0x591f38]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(+0xca0e0)[0x5910e0]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(Rf_applyClosure+0x300)[0x592a90]
/usr/lib/R/lib/libR.so(+0x117d81)[0x5ded81]
/usr/lib/R/lib/libR.so(Rf_usemethod+0x666)[0x5df5e6]
/usr/lib/R/lib/libR.so(+0x118fb4)[0x5dffb4]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(Rf_applyClosure+0x300)[0x592a90]
/usr/lib/R/lib/libR.so(Rf_eval+0x3fd)[0x58eafd]
/usr/lib/R/lib/libR.so(+0xc917f)[0x59017f]
/usr/lib/R/lib/libR.so(Rf_eval+0x64b)[0x58ed4b]
/usr/lib/R/lib/libR.so(+0xca0e0)[0x5910e0]
/usr/lib/R/lib/libR.so(Rf_eval+0x558)[0x58ec58]
/usr/lib/R/lib/libR.so(Rf_applyClosure+0x300)[0x592a90]
/usr/lib/R/lib/libR.so(+0x117d81)[0x5ded81]
/usr/lib/R/lib/libR.so(Rf_usemethod+0x958)[0x5df8d8]
======= Memory map: ========
00110000-00263000 r-xp 00000000 08:01 1708513    /lib/tls/i686/cmov/libc-2.11.1.so
00263000-00264000 ---p 00153000 08:01 1708513    /lib/tls/i686/cmov/libc-2.11.1.so
00264000-00266000 r--p 00153000 08:01 1708513    /lib/tls/i686/cmov/libc-2.11.1.so
00266000-00267000 rw-p 00155000 08:01 1708513    /lib/tls/i686/cmov/libc-2.11.1.so
00267000-0026a000 rw-p 00000000 00:00 0 
0026a000-00299000 r-xp 00000000 08:01 1704252    /lib/libreadline.so.6.1
00299000-0029a000 r--p 0002e000 08:01 1704252    /lib/libreadline.so.6.1
0029a000-0029d000 rw-p 0002f000 08:01 1704252    /lib/libreadline.so.6.1
0029d000-0029e000 rw-p 00000000 00:00 0 
0029e000-002cd000 r-xp 00000000 08:01 1704233    /lib/libpcre.so.3.12.1
002cd000-002ce000 r--p 0002e000 08:01 1704233    /lib/libpcre.so.3.12.1
002ce000-002cf000 rw-p 0002f000 08:01 1704233    /lib/libpcre.so.3.12.1
002cf000-002e2000 r-xp 00000000 08:01 1704290    /lib/libz.so.1.2.3.3
002e2000-002e3000 r--p 00012000 08:01 1704290    /lib/libz.so.1.2.3.3
002e3000-002e4000 rw-p 00013000 08:01 1704290    /lib/libz.so.1.2.3.3
002e4000-00301000 r-xp 00000000 08:01 1704175    /lib/libgcc_s.so.1
00301000-00302000 r--p 0001c000 08:01 1704175    /lib/libgcc_s.so.1
00302000-00303000 rw-p 0001d000 08:01 1704175    /lib/libgcc_s.so.1
00303000-00337000 r-xp 00000000 08:01 1704194    /lib/libncurses.so.5.7
00337000-00338000 ---p 00034000 08:01 1704194    /lib/libncurses.so.5.7
00338000-0033a000 r--p 00034000 08:01 1704194    /lib/libncurses.so.5.7
0033a000-0033b000 rw-p 00036000 08:01 1704194    /lib/libncurses.so.5.7
0033b000-00341000 r-xp 00000000 08:01 1708526    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00341000-00342000 r--p 00006000 08:01 1708526    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00342000-00343000 rw-p 00007000 08:01 1708526    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00343000-00349000 r-xp 00000000 08:01 1600054    /usr/lib/R/library/methods/libs/methods.so
00349000-0034a000 ---p 00006000 08:01 1600054    /usr/lib/R/library/methods/libs/methods.so
0034a000-0034b000 r--p 00006000 08:01 1600054    /usr/lib/R/library/methods/libs/methods.so
0034b000-0034c000 rw-p 00007000 08:01 1600054    /usr/lib/R/library/methods/libs/methods.so
00390000-0040b000 r-xp 00000000 08:01 1068205    /usr/lib/libblas.so.3gf.0
0040b000-0040c000 r--p 0007a000 08:01 1068205    /usr/lib/libblas.so.3gf.0
0040c000-0040d000 rw-p 0007b000 08:01 1068205    /usr/lib/libblas.so.3gf.0
00465000-00466000 r-xp 00000000 00:00 0          [vdso]
004c7000-00748000 r-xp 00000000 08:01 1600476    /usr/lib/R/lib/libR.so
00748000-00749000 ---p 00281000 08:01 1600476    /usr/lib/R/lib/libR.so
00749000-0074c000 r--p 00281000 08:01 1600476    /usr/lib/R/lib/libR.so
0074c000-00757000 rw-p 00284000 08:01 1600476    /usr/lib/R/lib/libR.so
00757000-007f0000 rw-p 00000000 00:00 0 
007fb000-00803000 r-xp 00000000 08:01 1708534    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00803000-00804000 r--p 00007000 08:01 1708534    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00804000-00805000 rw-p 00008000 08:01 1708534    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00838000-008fc000 r-xp 00000000 08:01 1068202    /usr/lib/libgfortran.so.3.0.0
008fc000-008fd000 ---p 000c4000 08:01 1068202    /usr/lib/libgfortran.so.3.0.0
008fd000-008fe000 r--p 000c4000 08:01 1068202    /usr/lib/libgfortran.so.3.0.0
008fe000-008ff000 rw-p 000c5000 08:01 1068202    /usr/lib/libgfortran.so.3.0.0
008ff000-00900000 rw-p 00000000 00:00 0 
00942000-009a4000 r-xp 00000000 08:01 1600169    /usr/lib/R/library/stats/libs/stats.so
009a4000-009a5000 r--p 00061000 08:01 1600169    /usr/lib/R/library/stats/libs/stats.so
009a5000-009a6000 rw-p 00062000 08:01 1600169    /usr/lib/R/library/stats/libs/stats.so
009a6000-009a7000 rw-p 00000000 00:00 0 
009cf000-009d9000 r-xp 00000000 08:01 1708530    /lib/tls/i686/cmov/libnss_files-2.11.1.so
009d9000-009da000 r--p 00009000 08:01 1708530    /lib/tls/i686/cmov/libnss_files-2.11.1.so
009da000-009db000 rw-p 0000a000 08:01 1708530    /lib/tls/i686/cmov/libnss_files-2.11.1.soAborted

The downloaded packages are in
	‘/tmp/RtmppHfXCW/downloaded_packages’
Mensajes de aviso perdidos
In install.packages("RUnit", dep = T) :
  installation of package 'RUnit' had non-zero exit status
```

I use RUnit, because it doesn't need any dependencies, but it happens with every package.

Thanks.

---

### Post by akniss on 2010-05-23
> **rpgki said:**
> oh yeah, sorry
I use RUnit, because it doesn't need any dependencies, but it happens with every package.

Thanks.

Not sure if this is exactly the same thing, but perhaps this is locale related. There is a post to the R-help mailing list that provides output nearly identical to yours:
[http://www.mail-archive.com/r-help@stat.math.ethz.ch/msg73313.html](http://www.mail-archive.com/r-help@stat.math.ethz.ch/msg73313.html)

However, this appears to be a thread from 2006, and should have been fixed from the sounds of things. Did you install r-recommended from the Ubuntu repos? or did you install R from another repo?

---

### Post by rpgki on 2010-05-23
it seems to be almost the same problem, and yes r-recommended is installed, and I followed instructions from  
[http://cran.r-project.org/](http://cran.r-project.org/), installation for ubuntu, i added the lucid repo, and then used apt-get update, and install r-base, then all the packages are installed, i don't know what went wrong, what confuse me is this, my architecture is i686 and when i use version in R this what i get

```
version
               _                            
platform       i486-pc-linux-gnu            
arch           i486                         
os             linux-gnu                    
system         i486, linux-gnu              
status                                      
major          2                            
minor          11.0                         
year           2010                         
month          04                           
day            22                           
svn rev        51801                        
language       R                            
version.string R version 2.11.0 (2010-04-22)
```

i don't know if I did something wrong when i added the repo, but i will try to solve this tomorrow, anyways thanks for your attention and reply.

---

### Post by akniss on 2010-05-23
> **rpgki said:**
> I followed instructions from  
[http://cran.r-project.org/](http://cran.r-project.org/), installation for ubuntu, i added the lucid repo, and then used apt-get update, and install r-base, then all the packages are installed

The R package is in fact in the default Ubuntu repositories. So unless you have some reason to use the CRAN repos (like needing the very most up to date version of some package), I would try reinstalling with the default Ubuntu repos to see if that solves the problem. (No guarantees that this will work.)
```
sudo apt-get remove r-base
```
Then remove the line:
```
deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu lucid/
``` from your /etc/apt/sources.list file. Then
```
sudo apt-get update
sudo apt-get install r-recommended
```

---

### Post by spinoza666 on 2010-05-24
You will need to install r-base-dev to install packages from CRAN, so issue:

sudo apt-get install r-base r-recommended r-base-dev

Installing r-recommended may install r-base-dev as well, but thought I should point out what package you are actually missing, which is r-base-dev. If you follow the instructions on CRAN precisely you should not get any trouble.

---

### Post by rpgki on 2010-05-24
yay, it worked, thanks akniss and spinoza too, both of you helped me, actually this is what I did:
```
$sudo apt-get remove r-base-core
$sudo apt-get autoremove
```

Then I removed  deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu lucid/, repo from 
/etc/apt/sources.list and then
```
sudo apt-get install r-base r-recommended r-base-dev
```
then
```
$sudo R
>install.packages("leaps", dep=T)
```

And finally, installed it, only one package gave me problem RODBC, but I solved it with this:
```
sudo apt-get install r-cran-RODBC
```

And it worked, thanks a million really, specially to you akniss.

Thanks for your time and reply.
Have a nice day.

---

