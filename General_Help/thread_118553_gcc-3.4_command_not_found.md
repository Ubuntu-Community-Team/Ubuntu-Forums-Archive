---
title: "gcc-3.4: command not found"
date: 2006-01-17
forum: General Help
---

### Post by cborge on 2006-01-17
Hi
I have the newest version of gcc, but do I need the version 3.4 to get this to work? 


> cborge@cblinux:~/ndiswrapper-1.7$  sudo make install
Password:
make -C driver install
make[1]: Entering directory `/home/cborge/ndiswrapper-1.7/driver'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/cborge/ndiswrapper-1.7/driver \
        DRIVER_VERSION=1.7
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/cborge/ndiswrapper-1.7/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/cborge/ndiswrapper-1.7/driver/hal.o] Error 127
make[2]: *** [_module_/home/cborge/ndiswrapper-1.7/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/cborge/ndiswrapper-1.7/driver'
make: *** [install] Error 2
cborge@cblinux:~/ndiswrapper-1.7$

---

### Post by GeneralZod on 2006-01-17
Just FYI, ndiswrapper should be included on the CD :)

But yes, you do need gcc-3.4 to compile this as, in Breezy, the kernel is compiled using a completely different compiler (gcc-3.4) to every other package (gcc-4.0).  Come Dapper, this won't be an issue.

---

### Post by cborge on 2006-01-17
OK. thanks

So whats the easyest way to get the ndiswrapper?

And how do I get the gcc-3.4 to work?
I've tried apt-get install gcc-3.4 but that did not work.


As you understand folks, I'm new at this :)

---

### Post by jrib on 2006-01-17
[QUOTE=cborge]
And how do I get the gcc-3.4 to work?
I've tried apt-get install gcc-3.4 but that did not work.
[/QUOTE]

Assuming by "I've tried apt-get install gcc-3.4 but that did not work." you mean it installed successfully but when you tried to compile, it still tried to use gcc-4.0:

```
$ export CC=gcc-3.4;
```

then proceed as normal

---

### Post by cborge on 2006-01-17
when I type:

sudo apt-get install gcc-3.4  I get an error. Can't find the package

Is this the right command?

---

### Post by GeneralZod on 2006-01-17
[QUOTE=cborge]OK. thanks
So whats the easyest way to get the ndiswrapper?
[/QUOTE]


Hmmm...I've never had to do this myself as I only buy Linux-compatible hardware (it prevents a lot of tears and frustration, believe me! :)), but give this a whirl:

[http://ubuntuforums.org/showthread.php?t=110518&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=110518&highlight=ndiswrapper+howto)
[http://www.ubuntuforums.org/showthread.php?t=104539&highlight=ndiswrapper+howto](http://www.ubuntuforums.org/showthread.php?t=104539&highlight=ndiswrapper+howto)

Also, for just installing gcc-3.4 (which hopefully won't be necessary if you install ndiswrapper via the CD!) :

[http://ubuntuforums.org/showthread.php?t=79896](http://ubuntuforums.org/showthread.php?t=79896)


Edit: VVV

Cool :)

---

### Post by cborge on 2006-01-17
Thanks a lot !  That last part worked perfectly :p

---

