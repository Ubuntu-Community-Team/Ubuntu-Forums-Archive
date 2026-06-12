---
title: "Flightgear segmentation fault"
date: 2006-07-07
forum: Desktop Environments
---

### Post by SteinbergerNate on 2006-07-07
I posted a reply about this on a different thread but then I noticed that it was for Breezy so I figure since I'm running Dapper I'll get more attention here.

I installed Flightgear 0.9.9 on my machine yesterday and when I go to run fgfs, all I get is a segmentation fault. 
```
bassmannate@bassmannate-laptop:~$ fgfs
Segmentation fault
bassmannate@bassmannate-laptop:~$
```

I decided to run it under gdb and this is what I get:
```
bassmannate@bassmannate-laptop:~$ gdb fgfs
GNU gdb 6.4-debian
Copyright 2005 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) run
Starting program: /usr/games/fgfs
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1220020544 (LWP 19942)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1220020544 (LWP 19942)]
0xb78eec8f in glXGetConfig () from /usr/lib/libGL.so.1
(gdb) 
```

That last line in there looks to be pointing to my openGL but I KNOW that is working because I spent a few days just trying to get that working under Dapper. 
Anyone have any clues?

---

### Post by mlind on 2006-07-07
Although this won't solve your issue, but you can compile flightgear with debug symbols on using [https://help.ubuntu.com/community/DebuggingProgramCrash](https://help.ubuntu.com/community/DebuggingProgramCrash)

It will generate more accurate info about the crash, and useful dump to attach on a bug report to [https://launchpad.net/distros/ubuntu/+source/flightgear/+bugs](https://launchpad.net/distros/ubuntu/+source/flightgear/+bugs)

---

### Post by SteinbergerNate on 2006-07-10
I tried that and the build failed. Looks like some test failed during the build of the deb.
Edit: I tried running it with valgrind. Looks like it's going to run until it gets to the point where it says it's loading the airports and navigation info and it just sits there. I kill it in the terminal and valgrind comes back with some memory leaks.

---

### Post by mlind on 2006-07-10
> **SteinbergerNate said:**
> I tried that and the build failed. Looks like some test failed during the build of the deb.
Edit: I tried running it with valgrind. Looks like it's going to run until it gets to the point where it says it's loading the airports and navigation info and it just sits there. I kill it in the terminal and valgrind comes back with some memory leaks.

I'll try building version 0.9.10-2 from Debian, and send it to you.

---

### Post by SteinbergerNate on 2006-07-10
Ok. Thanks. I hope I can get it working. Do you think that maybe a backup and clean install would work if nothing else?

---

### Post by mlind on 2006-07-10
> **SteinbergerNate said:**
> Ok. Thanks. I hope I can get it working. Do you think that maybe a backup and clean install would work if nothing else?

Clean install won't help you, I think it's bug either on software or kernel driver.

I dunno if newer version will help you, but it's worth a shot
[LIST]
[*]add to your /etc/apt/sources.list
```

deb http://www.elisanet.fi/mlind/ubuntu dapper testing

```
[*]then import gpg key (not absolutely necessary)
```

gpg --keyserver pgp.mit.edu --recv-key D0AFFF5E937215FF
gpg -a --export D0AFFF5E937215FF | sudo apt-key add -

```
[*]Then install plugin
```

sudo aptitude update && sudo aptitude install flightgear

```
[/LIST]

---

### Post by SteinbergerNate on 2006-07-11
All installed fine. Still won't run because I don't have the correct version of the base package. Downloading the source for the package now and gonna try to compile it later.

---

### Post by mlind on 2006-07-11
> **SteinbergerNate said:**
> All installed fine. Still won't run because I don't have the correct version of the base package. Downloading the source for the package now and gonna try to compile it later.

Could you elaborate?

Do you mean fgfs-base package? I had to modify debian/control and downgrade it's version, so it would work with Dapper.
I also had to build against newer simgear, but that's on the repository too.

---

### Post by SteinbergerNate on 2006-07-11
Yes. fgfs-base. It says that it detected 0.9.9 and that I should upgrade. I'm working on getting that stuff upgraded but can't quite figure out where to put everything.

---

### Post by mlind on 2006-07-11
> **SteinbergerNate said:**
> Yes. fgfs-base. It says that it detected 0.9.9 and that I should upgrade. I'm working on getting that stuff upgraded but can't quite figure out where to put everything.

When you did *sudo aptitude install flightgear* it's supposed to install all dependencies automatically.

I assume you don't have **multiverse** repository enable, which contains fgfs-base ?
(official Dapper repository)

---

### Post by SteinbergerNate on 2006-07-11
Oh, I do except that it contains 0.9.9. I got it to install but I'm still getting a segfault now that everything is configured "properly."
```
bassmannate@bassmannate-laptop:~$ fgfs
Error reading properties:
Failed to open file
 at /usr/share/games/FlightGear/data/mice.xml
 (reported by SimGear XML Parser)
Segmentation fault
bassmannate@bassmannate-laptop:~$

```

---

### Post by mlind on 2006-07-11
> **SteinbergerNate said:**
> Oh, I do except that it contains 0.9.9. I got it to install but I'm still getting a segfault now that everything is configured "properly."


I'm unsure what version of flightgear, fgfs-base and simgear you have installed now. If purging these all, and reinstalling won't help, you should build flightgear against newest simgear and fgfs-base which I didn't because fgfs-base was too damn big to download.

I tested to launch fgfs, and gui showed up like it probably should. Seems to work for me.

---

### Post by SteinbergerNate on 2006-07-12
Ok. I tried to build from source and I just get errors when I run make. It looks like it comes up with errors when it's trying to run some sort of tests.

---

### Post by mlind on 2006-07-12
> **SteinbergerNate said:**
> Ok. I tried to build from source and I just get errors when I run make. It looks like it comes up with errors when it's trying to run some sort of tests.

Have you built packages on Debian/linux before? If you check that pbuilder HOWTO on my signature, it should give you one safe way of doing it.

Get the source from debian unstable, then just build it using
```

sudo pbuilder build fgfs-base_0.9.10-1.dsc

```


Package seems to build fine.

---

### Post by SteinbergerNate on 2006-07-12
Yes, I've built from source on Ubuntu before. I've already attempted to run make once so not all the info from before is there but here is the output from make:
```
bassmannate@bassmannate-laptop:~/FlightGear-0.9.10$ make
Making all in tests
make[1]: Entering directory `/home/bassmannate/FlightGear-0.9.10/tests'
g++  -g -O2 -D_REENTRANT  -L/usr/X11R6/lib -L/usr/local/lib -o test-up  test-up.o -lsgmath -lsgxml -lsgmisc -lsgdebug -lsgstructure -lsgtiming -lplibsg -lplibul -lz -ldl -lm  -ljpeg
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libsgtiming.so: undefined reference to `logbuf::~logbuf()'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libsgtiming.so: undefined reference to `logbuf::logClass'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libsgtiming.so: undefined reference to `SGPath::append(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libsgtiming.so: undefined reference to `SGPath::~SGPath()'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libsgtiming.so: undefined reference to `global_logstream'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libsgtiming.so: undefined reference to `SGPath::set(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libsgtiming.so: undefined reference to `logbuf::logbuf()'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libsgtiming.so: undefined reference to `logbuf::logPriority'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libsgtiming.so: undefined reference to `logbuf::logging_enabled'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libsgtiming.so: undefined reference to `SGPath::SGPath(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libsgtiming.so: undefined reference to `logbuf::set_sb(std::basic_streambuf<char, std::char_traits<char> >*)'
collect2: ld returned 1 exit status
make[1]: *** [test-up] Error 1
make[1]: Leaving directory `/home/bassmannate/FlightGear-0.9.10/tests'
make: *** [all-recursive] Error 1
bassmannate@bassmannate-laptop:~/FlightGear-0.9.10$

```
I'll take a look at what you posted right after I post this.

---

### Post by mlind on 2006-07-12
> **SteinbergerNate said:**
> Yes, I've built from source on Ubuntu before. I've already attempted to run make once so not all the info from before is there but here is the output from make:


I looked at debian/rules, here's how the package is being configured

```

./configure --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info \
                    --bindir=\$${prefix}/games --datadir=\$${prefix}/share/games \
                    --with-simgear=/usr --with-multiplayer --with-threads

```


If you don't want to use pbuilder, use dpkg-buildpackage instead which is found on dpkg-dev package.
You will need to install all build-time dependencies on your running system this way though.

---

### Post by SteinbergerNate on 2006-07-13
Well, I created a package using pbuilder. Built just fine. However, when I went to go install the package, it said there was an error installing the package. I dunno. Maybe it's my computer (Dell laptop...should work just fine right?)

---

### Post by mlind on 2006-07-13
> **SteinbergerNate said:**
> Well, I created a package using pbuilder. Built just fine. However, when I went to go install the package, it said there was an error installing the package. I dunno. Maybe it's my computer (Dell laptop...should work just fine right?)

Could you copy paste the error here?
If it's a dependency error, just run *sudo apt-get install -f* to fix it.

btw. Did you have any problems setting up the pbuilder environment? or was there something that was vaguely explained/you didn't understand? I'd like to improve the HOWTO if there's something wrong with it.

---

### Post by SteinbergerNate on 2006-07-14
Never mind. I figured it out. I was trying to install from Nautilus instead of the command line (had I done that I would have seen clearly what the problem was :)) It was still seeing that I had fgfs-base 0.9.10 on there even though I had reinstalled 0.9.9. I just uninstalled 0.9.9 from Synaptic and then manually deleted the remaining files. I built all three packages and installed them. fgfs starts without a hitch. Thanks for all your help. Now I can build good packages from source :)

---

### Post by mlind on 2006-07-16
> **SteinbergerNate said:**
> Never mind. I figured it out. I was trying to install from Nautilus instead of the command line (had I done that I would have seen clearly what the problem was :)) It was still seeing that I had fgfs-base 0.9.10 on there even though I had reinstalled 0.9.9. I just uninstalled 0.9.9 from Synaptic and then manually deleted the remaining files. I built all three packages and installed them. fgfs starts without a hitch. Thanks for all your help. Now I can build good packages from source :)

Good you got the problem solved.

---

