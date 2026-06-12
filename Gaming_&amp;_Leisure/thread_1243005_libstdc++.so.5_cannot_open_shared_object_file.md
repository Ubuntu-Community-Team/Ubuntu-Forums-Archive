---
title: "libstdc++.so.5: cannot open shared object file"
date: 2009-08-17
forum: Gaming &amp; Leisure
---

### Post by SNOOPY817 on 2009-08-17
Okay well im playing on AA2 [Americas Army] and im trying to make a server but 
i keep on getting this error:

====== ASSIST SERVER MANAGER - Please Wait, Initializing ======
====== ASSIST SERVER MANAGER - Port Test Successful ======
 ====== AUTO STARTING SERVER ======
 ====== ASSIST SERVER MANAGER - Starting Server ====== 
====== ASSIST SERVER MANAGER - Loading Normal AA Mode Configuraion ====== /home/snoopy/25Assist/armyops/System/server-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
====== ASSIST SERVER MANAGER - Server Crashed, RESTARTING ======
 ====== ASSIST SERVER MANAGER - Shutdown Complete ======
 ====== ASSIST SERVER MANAGER - Starting Server ======
 ====== ASSIST SERVER MANAGER - Loading Normal AA Mode Configuraion ====== /home/snoopy/25Assist/armyops/System/server-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Anyone know?

---

### Post by Perfect Storm on 2009-08-18
If you read the error output:
```
 error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```
It tells you what's wrong.

Have you tried:

```
sudo apt-get install libstdc++5
```

---

### Post by SNOOPY817 on 2009-08-18
Yeah well im really kinda like a noob
to Ubuntu, trying to get the hand of it
but thanks the code worked. :D

---

### Post by mad_prince on 2009-11-19
hi, I've the same problem, but libstdc++.so.5 isn't available in repos anymore. Can u help me? I'd like to play in True Combat. but absence of the file makes that impossible

---

### Post by Perfect Storm on 2009-11-19
[http://packages.ubuntu.com/search?keywords=libstdc%2B%2B5&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=libstdc%2B%2B5&searchon=names&suite=jaunty&section=all)

---

### Post by mad_prince on 2009-11-19
thx, but I still have "libstdc++.so.5: cannot open shared object file: No such file or directory"
Maybe it's becouse I have karmic not jaunty?

---

### Post by aberke on 2009-11-19
> **Artificial Intelligence said:**
> [http://packages.ubuntu.com/search?keywords=libstdc%2B%2B5&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=libstdc%2B%2B5&searchon=names&suite=jaunty&section=all)

This worked for me and fixed my shared object file error! Installing the .deb found through that link allowed me to access my Mathematica again. Thanks. :)

(for future reference should anyone need it: this is Mathematica 6 in Karmic, post upgrade, when it worked in Jaunty)

---

### Post by Perfect Storm on 2009-11-19
> **mad_prince said:**
> thx, but I still have "libstdc++.so.5: cannot open shared object file: No such file or directory"
Maybe it's becouse I have karmic not jaunty?

You're on 64-bit?

---

### Post by mad_prince on 2009-11-19
Yes I am. And I also have downloaded package for 64bit.

---

### Post by Perfect Storm on 2009-11-19
> **mad_prince said:**
> Yes I am. And I also have downloaded package for 64bit.

True Combat is 32-bit app/game. So you need to install the 32-bit version of libstdc++5 on your 64-bit system.

```
cd ~/Desktop
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
wget http://nl.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb
sudo dpkg -i getlibs-all.deb
getlibs -i libstdc++5_3.3.6-17ubuntu1_i386.deb
```

---

### Post by mad_prince on 2009-11-19
It works! Thank YOU very much :D:popcorn:

---

### Post by DenisGLX on 2009-11-19
I found this problem when compiling a code in fortran...
I performed the procedures list (thanks AI) but the same mesage remains... 
My fortran is 64-bit. Maybe I need a 64-bit libstdc++5. 
Plz, how should be the procedures in this situation??

---

### Post by Perfect Storm on 2009-11-19
If you're compiling in 64-bit for 64-bit, you need the 64-bit version of libstdc++5
The problem is that libstdc++5 is obsolete and the -dev package you need for compiling is old. You have to get an old package back from hardy version. (as the -dev package you need to compile is only available there)
You need to uninstall your previous version of libstdc++5 and install the version from hardy and then install the -dev package of it for compiling as it isn't maintained anymore.

[http://packages.ubuntu.com/search?keywords=libstdc&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=libstdc&searchon=names&suite=hardy&section=all)

---

### Post by DenisGLX on 2009-11-19
Hi,

I followed the link that you furnished. Instead downloading and installing manually I changed my
[FONT=Verdana][/FONT]
/etc/apt/sources.list
[FONT=Verdana]adding: 

[/FONT]deb [http://*cz.archive.ubuntu.com/ubuntu](http://*cz.archive.ubuntu.com/ubuntu)* hardy main universe

[FONT=Verdana]After that I used the Synaptic Package Manager and fixed the issue. The details are in
[http://packages.ubuntu.com/hardy/amd64/gcc-3.3/download](http://packages.ubuntu.com/hardy/amd64/gcc-3.3/download)

[/FONT][FONT=Verdana]Thanks AI.[/FONT]

---

### Post by Perfect Storm on 2009-11-19
Just disable the line afterwards, as it's not a good idea to mix repos.

---

### Post by keeswouters on 2009-11-21
Thanks AI, your recipe worked fine for getting Code Aster (FEA program) running again.
kind regards - kees

---

### Post by uniden9 on 2009-11-28
Thanks, this fixed dell openmanage under ubuntu 9.10 for me.

---

### Post by hienkyoku on 2010-01-04
THNX AI it work for me too :)

---

### Post by Plague on 2010-02-10
I did as AI had suggested but when I run 
```
sudo dpkg -i getlibs-all.deb
getlibs -i libstdc++5_3.3.6-17ubuntu1_i386.deb
```
I get the following error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++5_3.3.6-17ubuntu1_i386.deb
```

both of the downloaded files are on desktop.

---

### Post by Perfect Storm on 2010-02-10
> **Plague said:**
> I did as AI had suggested but when I run 
```
sudo dpkg -i getlibs-all.deb
getlibs -i libstdc++5_3.3.6-17ubuntu1_i386.deb
```
I get the following error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++5_3.3.6-17ubuntu1_i386.deb
```

both of the downloaded files are on desktop.

If it's on your Desktop, you need first to do:
```
cd ~/Desktop
```

---

### Post by Plague on 2010-02-11
> **Artificial Intelligence said:**
> If it's on your Desktop, you need first to do:
```
cd ~/Desktop
```

hehehe I was on Desktop, otherwise the other command would have failed as well. It s fixed now [found a solution somewhere].

Cheers

---

### Post by lbthrice on 2010-08-10
THANK YOU AI.
You saved me SO much pain.

Worked for me in:
Ubuntu 9.10 (karmic)
Linux 2.6.31-22-generic x86_64 GNU/Linux

:KS

---

### Post by hkgangwar on 2010-09-07
I am Ununtu Lucid 64 bit and have same problem and I resolved it
Basically you need to link 32 bit version of libstdc++.so.5 
Here is the detailed procedure to do that as a part of Ifort installtion 
[http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/](http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/)

---

### Post by habschi on 2010-10-27
> **DenisGLX said:**
> 
[FONT=Verdana][/FONT]
/etc/apt/sources.list
[FONT=Verdana]
adding: 
[/FONT]deb [http://*cz.archive.ubuntu.com/ubuntu](http://*cz.archive.ubuntu.com/ubuntu)* hardy main universe


I did it the same way... adding the line, then
```
sudo apt-get install libstdc++5
```
and disabling the line in sources.list afterwards. 
Thanks, too

---

### Post by utkarshspat on 2011-02-03
Thanks a lot. Thank you very much. Although I wasn't gaming but your help solved my problem that I was getting during the installations of J2EE SDK and while executing a friend's C++ executable file. Artificial Intelligence, you're a :KS.

---

### Post by flang3r on 2011-02-12
> **habschi said:**
> I did it the same way... adding the line, then
```
sudo apt-get install libstdc++5
```
and disabling the line in sources.list afterwards. 
Thanks, too

Thanks a lot! This saved me some time.

I was trying to install Xilinx WebPACK 9.2i on Ubuntu 10.04.
This package is so old that I needed libstdc++5 to install. Ubuntu 10.04 only has libstdc++6 installed by default but that was not enough.

Any way, thanks !

EDIT: 

Also if ```
sudo apt-get install libstdc++5
```
 does not work, remember to do 
```
sudo apt-get update
```

---

### Post by tonyjunk on 2013-02-13
this works on 12.04:

sudo apt-get -f install libstdc++5 libaio1 libsdl-mixer1.2  libsdl-net1.2  libsdl-ttf2.0-0 xaw3dg libmikmod2 oss-compat

---

