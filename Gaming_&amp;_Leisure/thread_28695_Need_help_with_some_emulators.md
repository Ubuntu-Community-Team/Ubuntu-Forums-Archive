---
title: "Need help with some emulators"
date: 2005-04-21
forum: Gaming &amp; Leisure
---

### Post by NTolerance on 2005-04-21
I've been looking to emulate some consoles, and I've had some success so far, and also some problems.  I've searched through what's in the Ubuntu/Debian repositories and also at [www.apt-get.org](www.apt-get.org).  Here's where I'm at:

**SNES**:  Compiled the latest version of ZSNES from source, runs great

**GB/GBA**:  Installed a version of VisualBoyAdvance with Synaptic.  I also installed the Gnomeboyadvance frontend which I need to configure my joystick.  I can run it as root but when I try as a regular user I get this:

```
You must have python-gtk2, python-gnome2 and python-glade2 installed.

```

I have all of those packages installed, but it still gives me that error ONLY when running gnomeboyadvance as a regular user.   

**Genesis**:  I get this error compiling Gens from source as root:

```
./configure
bash: ./configure: Permission denied

```

**Sega Master System**:  I downloaded two different Linux versions of Mekanix.  For some reason there's no source, but there are exe files:

```
changes.txt  meka.blt  meka.exe  meka.nam     meka.thm   tech.txt
compat.txt   meka.cfg  meka.inp  mekanix.txt  meka.txt
icons.zip    meka.dat  meka.msg  meka.pat     multi.txt

```

---

### Post by jdodson on 2005-04-22
[QUOTE=NTolerance]I've been looking to emulate some consoles, and I've had some success so far, and also some problems.  I've searched through what's in the Ubuntu/Debian repositories and also at [www.apt-get.org](www.apt-get.org).  Here's where I'm at:

**SNES**:  Compiled the latest version of ZSNES from source, runs great

**GB/GBA**:  Installed a version of VisualBoyAdvance with Synaptic.  I also installed the Gnomeboyadvance frontend which I need to configure my joystick.  I can run it as root but when I try as a regular user I get this:

```
You must have python-gtk2, python-gnome2 and python-glade2 installed.

```[/quote]

goto [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) and fill out a bug report please.  this can get fixed in the next version.

[QUOTE=NTolerance]I have all of those packages installed, but it still gives me that error ONLY when running gnomeboyadvance as a regular user.   

**Genesis**:  I get this error compiling Gens from source as root:

```
./configure
bash: ./configure: Permission denied

```[/quote]

strange problem.  as regular user try "sudo sh ./configure", dunno worth a shot to try it a different way.

[QUOTE=NTolerance]**Sega Master System**:  I downloaded two different Linux versions of Mekanix.  For some reason there's no source, but there are exe files:

```
changes.txt  meka.blt  meka.exe  meka.nam     meka.thm   tech.txt
compat.txt   meka.cfg  meka.inp  mekanix.txt  meka.txt
icons.zip    meka.dat  meka.msg  meka.pat     multi.txt

```[/QUOTE]

yeah looks like the developers are asleep at the wheel and put the win version where the gnu/linux version should be.  i would send them an email telling them the problem.  so they can get it fixed.

---

### Post by NTolerance on 2005-04-26
[QUOTE=jdodson]goto [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) and fill out a bug report please.  this can get fixed in the next version.



strange problem.  as regular user try "sudo sh ./configure", dunno worth a shot to try it a different way.



yeah looks like the developers are asleep at the wheel and put the win version where the gnu/linux version should be.  i would send them an email telling them the problem.  so they can get it fixed.[/QUOTE]

I entered the GnomeBoyAdvance bug in bugzilla.

I also tried to configure Gens via sudo, no luck.  Do you know of another way to try to install this emulator?  Surely someone has done this with Ubuntu...

As far as Meka goes, I downloaded several older "Linux" versions and they all had just Windows executables.  I don't get it.  Know of any other SMS/GG emulators for Linux?  

Thanks.

---

### Post by srettub on 2005-05-06
[QUOTE=NTolerance]
**Genesis**:  I get this error compiling Gens from source as root:

```
./configure
bash: ./configure: Permission denied

```
[/QUOTE]
I had the same problem.  I grabbed the cvs version instead and it works fine.  To get it:

```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gens login
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gens co -P GensForLinux

```
Just hit enter when prompted for a password.

edit:  You'll also need nasm.  apt-get install nasm

---

### Post by linuxfanatic1024 on 2005-07-08
For Gens: try this as a normal user (NOT root):
```
chmod a+x ./configure
./configure
make
sudo make install 
```

In general, it is not a good idea to compile source code as root. I am surely someone who has compiled Gens in Ubuntu... :wink:

For Meka: Meka used to be binary-only. What you're seeing is not Windows executables. The author, Omar Cornut, decided to put the .exe onto the end of the emulator's executable name (and I have no idea why). But it works. Just type ./meka.exe at the prompt and it should work. Last April it went open-source, so you should have better luck with it soon. If it doesn't work, then do a 
```
chmod +x meka.exe
```
and try again.

There are two other Master System emulators for Linux that I know of: MasterGear and Osmose. Meka and Osmose are open-source, but MasterGear is proprietary but free-as-in-beer. Windoze users have to pay for it...  :grin: 

There used to be an excellent site devoted to emulation on Linux, but it seems to have been rebuilt recently. It was at [http://tuxemu.com](http://tuxemu.com)

Good luck....

---

### Post by graabein on 2005-07-22
I need help with the Amiga emulator uae. I installed version 0.8.22-1 through Synaptic and when I start it with "uae" I get:

```
Testing the RDTSC instruction ... done.
Calibrating delay loop.. ok - 2029.23 BogoMIPS
```
and nothing happens... Any help would be appreciated!

---

### Post by mulperi on 2005-08-04
I get stuck in the same place, however:
Testing the RDTSC instruction ... done.
Calibrating delay loop.. ok - 1527.90 BogoMIPS

Something positive...Guess you have a faster machine :-)

Did you solve this?

---

### Post by linuxfanatic1024 on 2006-01-09
There are Slackware packages for Meka that can be converted to deb format easily using Alien. Visit [http://www.smspower.org/forums/viewtopic.php?t=7120](http://www.smspower.org/forums/viewtopic.php?t=7120) for more info.

---

