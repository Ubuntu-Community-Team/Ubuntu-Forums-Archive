---
title: "My dial-up catch 22"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Justus on 2005-12-07
So here's my problem: I am unable to connect to Dial-up using Ubuntu and my internal Conexant modem, and all the solutions I've tried involve having to compile things with the make command, which I can't do, because make isn't installed, and I can't install it, because I can't connect. Is there anyway to download the package that contains "make" on Windows and then transfer it to Linux and install it? Or any solutions that don't involve compiling source code? Thanks everyone

EDIT: I'd also be very greatful if people who have been able to connect with a Conexant modem could post here (or even people who are still trying). Thanks!

---

### Post by shadow07 on 2005-12-08
Have you tried using the sl-modem-daemon pacakage?  It appears to work for some modems on laptops.  You can download it from your Windows machine:  [here]("http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb")

---

### Post by Justus on 2005-12-08
Not on a laptop...any other suggestions?

---

### Post by shadow07 on 2005-12-08
I would still download it and try.  It's a LOT easier then trying to download the build essential package, kernel source/headers, g++, make, etc. packages.

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=Justus]Not on a laptop...any other suggestions?[/QUOTE]
Isn't the "build-essentials" package included on the install CD?  Can you install it from there?

---

### Post by Justus on 2005-12-08
I'll give sl-modem-daemon a try then right now. Thanks for the suggestion. And as for the build-essentials package being on the install CD, even if it was, I would have no clue on how to get it. I'm a completely noob...just installed Linux for the first time 3 days ago :P

---

### Post by RAOF on 2005-12-08
The way to get "build-essentials" from the install CD would be to have the CD in the drive, and type "sudo apt-get install build-essential" from a terminal window.  Alternatively, search for "build-essential" in synaptic (System->Administration->Package Manager), select it to install, and apply the changes.

---

### Post by Justus on 2005-12-08
I was able to install the build essentials package, but it still isn't working...in the installation instructions for Gnome PPP, it just says to go to the folder, type ./configure, and then type make. But it says "no targets specified, or something like that.

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=Justus]I was able to install the build essentials package, but it still isn't working...in the installation instructions for Gnome PPP, it just says to go to the folder, type ./configure, and then type make. But it says "no targets specified, or something like that.[/QUOTE]
Can you copy the output to a floppy or USB key and post it back here?  You can usually redirect the error output to a file by doing something like this:
```

$ ./configure 2> configure_errors.txt
$ make 2> make_errors.txt

```

---

