---
title: "a million problems!"
date: 2006-02-04
forum: Desktop Environments
---

### Post by thejoeandchip on 2006-02-04
where do i start...

     So today i was installing loads of browsers on my machine, having fun! my little sister comes in and is like "you desktop is so cool, wow frozen bubble is free, wow you have firefox too!" and so she asked me to convert her windows machine into an all ubuntu machine, I was so proud! so i got started and installation was going smoothly. when the system was up i tried to download ndiswrapper from from apt-get only to remember that her pc had no internet other than her WG111T usb wifi adapter, duh. so i set her pc up in my room that has ethernet and ran automatix. i told automatix to include ndisgtk. i get the driver off the website, put it in ndisgtk, and got nothing. i then try to install ndiswrapper. it wasn't in the repository! so i get the source. do a quick apt-get of make and open the terminal and type "sudo make" enter my password and get 

make -C driver
make[1]: Entering directory `/home/sister/Desktop/ndiswrapper-1.9/driver'
Can't find kernel sources in /lib/modules/2.6.12-10-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/sister/Desktop/ndiswrapper-1.9/driver'
make: *** [all] Error 2

LAME! i dont know what to do! if you can help, i will be very grateful!

---

### Post by invalid on 2006-02-04
I'm not sure how this is "a million problems!".. but in any case. What it looks like you need is the kernel tree or kernel header files, so that it can compile against the source code. Use your internet connected machine to search the repos for the one matching your kernel, and install this.

---

### Post by thejoeandchip on 2006-02-04
i have search the forum, i just got a lot of mixed and confusing answers. if i cant install this, my sister will always think linux is lame, that'd be weak after how long it took me to convince her it rocked out loud.

---

### Post by towsonu2003 on 2006-02-04
in sister's computer, put in the install cd, ```
sudo apt-get update
sudo apt-get install linux-headers-`uname -r`
```, try again.isn't ndiswrapper in the cd as well???

---

### Post by thejoeandchip on 2006-02-04
ok, headers and tree installed and now i get this:

make -C driver
make[1]: Entering directory `/home/sister/Desktop/ndiswrapper-1.9/driver'
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/sister/Desktop/ndiswrapper-1.9/driver \
        DRIVER_VERSION=1.9
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/sister/Desktop/ndiswrapper-1.9/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/sister/Desktop/ndiswrapper-1.9/driver/hal.o] Error 127
make[2]: *** [_module_/home/sister/Desktop/ndiswrapper-1.9/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/sister/Desktop/ndiswrapper-1.9/driver'
make: *** [all] Error 2

i have gcc up to date. i used sudo. when i tried apt-get for ndiswrapper with the cd in i still got nothing. i think i have something wrong with the repositories. if you can think of a solution, please help.

---

### Post by thejoeandchip on 2006-02-04
is there a way i can add repositories in terminal? i searched synaptic for ndiswrapper and got nothing :(

---

### Post by stoffe on 2006-02-04
gcc-3.4 is a separate package, as it is an older version. Try installing that.

The list of repositories is in /etc/apt/sources.list if you need to look at it manually.

---

### Post by Mustard on 2006-02-04
To get the system to use gcc 3.4 (after you install it), you will probably need to do this command in terminal..

```
export CC=gcc-3.4
#a variation on this command, which sets the CC variable is this
export CC=/usr/bin/gcc-3.4
#either one should work

```

---

### Post by ORF1000 on 2006-07-29
You need ndiswrapper 1.10 or higher to run the WG111T.  That means getting the source and compiling.  [I followed these instructions with great results.]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")  Go to section 4.  Also, you need to install both Windows drivers: athfmwdl.inf and netwg11t.inf.

---

