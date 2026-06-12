---
title: "X11 issues with SheepShaver"
date: 2009-04-02
forum: Desktop Environments
---

### Post by afrodeity on 2009-04-02
I am trying to compile SheepShaver to use on Ubuntu, but stuck with this last problem:


checking for mon... no
configure: WARNING: Could not find mon, ignoring --with-mon.
checking for sem_init in -lposix4... no
checking for cos in -lm... yes
checking for X... no
configure: error: You need X11 to run SheepShaver.

X11 is installed, I don't get it. Unless it has something to do with perl? Also, am supposed to "Make" the resulting file, but can't figure out how to use make, at least when I do, its says: no makefile

---

### Post by stderr on 2009-04-03
I'm currently using the dreaded Winblows and hating every second (blame the iPhone), so I can't check what the lib names are. But you need to install X11's development packages.

You can probably find the right ones with something like:

```
apt-cache search x11 dev
```

and install them like so:

```
sudo apt-get install PACKAGE_NAME
```

The procedure for compilation is normally something along the lines of:

./configure
make
make install

depending on the package. You may not need the last stage. It may need to be run with sudo. You should get a README or INSTALL file along with it that gives you a better indication.

---

### Post by afrodeity on 2009-04-03
You need pthreads to run SheepShaver.


and locate:

 locate pthread
/lib/libpthread-2.7.so
/lib/libpthread.so.0
/lib32/libpthread-2.7.so
/lib32/libpthread.so.0
/usr/bin/wine-pthread
/usr/lib/libgpgme-pthread.so.11
/usr/lib/libgpgme-pthread.so.11.6.4
/usr/lib/kde4/lib/libgpgme++-pthread.so.1.0.0
/usr/lib/perl/5.8.8/bits/pthreadtypes.ph
/usr/share/man/man7/pthreads.7.gz


glibc is installed.

Is this a specific pthread needed to run SheepShaver or SheepShaver compiler can't find the pthreads installed?

am downloading Kaffe Pthreads to check if this is what is missing.

---

### Post by afrodeity on 2009-04-03
I've checked [Posix Threads on Wiki ]("https://computing.llnl.gov/tutorials/pthreads/#Compiling")[https://computing.llnl.gov/tutorials/pthreads/#Compiling](https://computing.llnl.gov/tutorials/pthreads/#Compiling)

and I have gcc and g++ installed. What gives. This should compile?

---

### Post by afrodeity on 2009-04-03
configure: error: You need pthreads to run SheepShaver.

I have g++ and gcc installed. What gives, this should compile?

---

### Post by snova on 2009-04-03
Install the **build-essential** package.

---

### Post by afrodeity on 2009-04-03
SOLVED: using this excellent [How To]("http://ubuntuforums.org/showthread.php?t=670336"), wish I had found it to begin with.

[Use this page to get the CVS]("http://gwenole.beauchesne.info/en/projects/sheepshaver#getting_help")

---

### Post by bodhi.zazen on 2009-04-03
Threads merged.

---

### Post by afrodeity on 2009-04-04
> **bodhi.zazen said:**
> Threads merged.

Thanks bodhi.zazen for this piece of zen. Do you know where I can get an older Apple Rom? Mac is Very scarce in the third world. Have tried all the torrents but no luck. I actually own two Powerbooks, but they not working.

---

