---
title: "Apple II emulator"
date: 2010-06-21
forum: Emulators
---

### Post by Linux BASHer on 2010-06-21
Could someone point me to a capable Apple II emulator for Linux?

I tried to set up MESS and MAME to no avail, and I'm not even sure they support the Apple II. At this point, I'd prefer to go with a standalone emulator.

---

### Post by Grishka on 2010-06-22
I'd think that your best bet is MESS. I remember running Apple II games with it at some point in the past. MESS is a great piece of software, only it takes a bit to get used to. as for standalone emulators, there's [KEGS](http://kegs.sourceforge.net/), but it only emulates Apple IIGS, and I don't think I've managed to run any games with it at all.

---

### Post by Mike'sHardLinux on 2010-06-22
Kegs is good. It does play games fine. Also, don't forget, a IIgs has an Apple IIe on a chip. Kegs plays 140k DSK images just fine. You can even set the emulation speed to 1mHz so it runs more like an 8-bit II. 

The Kegs source is pretty easy to compile. I compiled it in Ubuntu 10.04 32-bit. *To compile in 64 bit, see my note below *

You'll need the build-essential package and the xorg-dev package.
```
sudo apt-get install build-essential xorg-dev
```

cd to the source directory
```

cd ~/Desktop/kegs.0.91/src

```

Be sure to follow the instructions in the x86 Linux section in the README.compile.txt file. It just says to enter this command before make: rm vars; ln -s vars_x86linux vars


*If you are compiling in 64-bit, you need to change the -march flag in the vars file to -march=amdfam10 before running the make command.

```

rm vars; ln -s vars_x86linux vars
make

```

Now,you have a file called xkegs in the main kegs directory. Change to that directory and run the xkegs file.
```

cd ..
./xkegs

```

Almost forgot: You'll need an image of the system ROM for this to work, as with any emulator.

---

### Post by csmth on 2012-03-04
This is continuation of the FAQ developed by Mike.

Because there is no /dev/dsp in 11.10 and later release of ubuntu, use this command instead directing invoking ./xkegs:

```
padsp ./xkegs
```

padsp will emulate /dev/dsp (OSS) device for a command.

If it is acceptable to run a silent application:

```
./xkegs -audio 0
```

---

