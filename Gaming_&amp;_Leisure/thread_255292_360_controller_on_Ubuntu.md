---
title: "360 controller on Ubuntu"
date: 2006-09-11
forum: Gaming &amp; Leisure
---

### Post by Ajguy on 2006-09-11
Hello. I just installed Ubuntu yesterday and I'm loving it so far. I was very proud of myself when I managed to install ATI drivers successfully. Now I've hit my first brick wall. The Xbox 360 Controller. I have followed the isntructions in this thread: [http://ubuntuforums.org/showthread.p...box+controller](http://ubuntuforums.org/showthread.p...box+controller)
So far, I managed to get the make package and install that, but the kernel directory isn't there. This is what I get after running the make file:
aj@aj-desktop:~/xpad360$ make
make modules -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/aj/xpad360
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory. Stop.
make: *** [all] Error 2
aj@aj-desktop:~/xpad360$

I look in that directory and there is no build. I was just going to make it, but it won't let me make a directory there. Anyone know how to work this out?

---

### Post by Raavea on 2006-09-11
Have you tried making the directory with the SUDO command?

 I don't know the terminal command to make a directory, but if you shove SUDO in front of the whole command it'll let you perform that command as a god-user, so no permissions errors.

 Like this;
```
sudo gedit godpermissionsneeded.txt
```

---

### Post by isnellgrove on 2006-09-15
It appears you have make and build-essential installed, but do you have the headers for your kernel vesion?  If I remember correctly it is 

sudo apt-get install linux-headers-2.6.15-26-386

make sure you're headers match up with your kernel build.
Good luck, my 360 controller works like a champ!

---

### Post by dk5151 on 2006-11-10
I'm having the same issue. I just installed my headers from the repos and I'm still getting the same error as the guy above.

---

### Post by GregLH on 2006-11-10
Would be kinda cool to use my x-box 360 controller on here. Same error as the other two.

---

### Post by po0f on 2006-11-10
Just to clarify, you need to install the headers for your running kernel.  If you use the *-686/*-generic kernel, install the headers for them.  Better yet, get it right the first time and:
```
$ sudo aptitude install linux-headers-`uname -r`
```

---

### Post by qrm on 2006-11-10
if you need to create a folder use this command:'

```
sudo mkdir nameofthefolder
```

---

### Post by GregLH on 2006-11-11
I still a'm not sure what I am doing wrong. Maybe one of you guys know better then me, lol.
```
greg@Razorarse:~$ cd ~/xpad360
greg@Razorarse:~/xpad360$ make
make modules -C /usr/src/linux-headers-2.6.15-27 SUBDIRS=/home/greg/xpad360
/usr/src/linux-headers-2.6.15-27/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.15-27/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-27/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/greg/xpad360/xpad.o
/bin/sh: gcc: command not found
make[2]: *** [/home/greg/xpad360/xpad.o] Error 127
make[1]: *** [_module_/home/greg/xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27'
make: *** [all] Error 2
greg@Razorarse:~/xpad360$

```

I get the same with linux-headers-2.6.15-27-386 also.

---

### Post by po0f on 2006-11-11
GregLH,

```
$ sudo aptitude install build-essential
```

That package installs gcc, along with [other stuff](http://packages.ubuntu.com/dapper/devel/build-essential) needed to do the most basic compiling of stuff.

---

