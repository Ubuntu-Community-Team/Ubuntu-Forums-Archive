---
title: "USB Serial Convert support"
date: 2009-01-05
forum: General Help
---

### Post by Clandestine_Ghost on 2009-01-05
Hello all, not sure if this is the correct forum to post this in, but here goes.

New to Ubuntu but not completely lost. I have had some slight exposure to various Linux OS's years ago so I have been able, thus far, to figure out things as I go. However, I have been trying to get my Garmin USB driver to interface with MapSource and have failed miserably. I have the garmin_gps-0.32 driver, but I am unsure how to install it. I am hoping that if I post the instructions it has given me in the readme, somebody will be able to give me a great step by step, how to get there and what to click on walkthrough. This is what it says:

[B]"The driver requires 'USB Serial Convert support' to be configured.
To compile it put all the files into a directory and and use the 
supplied shell script to compile/install the module:
	/bin/sh compile.sh <kernel-source-dir>"[/B]

If anybody can tell me how to do that along with how to enable the USB Serial Convert support, I would greatly appreciate it. I have a huge fishing trip this Firday, already planned out on MapSource, but I cannot send it to my GPS if they do not interface!!!

---

### Post by Clandestine_Ghost on 2009-01-07
Somebody.....anybody....please help me.

---

### Post by jon zendatta on 2009-09-05
Yes I have the same problem!

[PHP]j0n@j0n-laptop:~/Desktop$ cd garmin_gps-0.32
j0n@j0n-laptop:~/Desktop/garmin_gps-0.32$ ./config
bash: ./config: No such file or directory
j0n@j0n-laptop:~/Desktop/garmin_gps-0.32$ sudo sh ./garmin_gps-0.32
[sudo] password for j0n: 
sh: Can't open ./garmin_gps-0.32
j0n@j0n-laptop:~/Desktop/garmin_gps-0.32$ 
[/PHP]

So here is the install instructions.


The driver requires 'USB Serial Convert support' to be configured.

To compile it put all the files into a directory and and use the 
supplied shell script to compile/install the module:

	/bin/sh compile.sh <kernel-source-dir>
	
Any idea's thanks people, keep instructions simple:KS

---

### Post by Rhubarb on 2009-09-05
Could you let me know what exactly this garmin usb driver allows me to do?

As currently I have no problems being able to use gpsbabel to communicate with my Garmin etrex Vista HCx unit under Ubuntu 9.04

I found the kernel module driver from here:
[http://sourceforge.net/projects/garmin-gps/](http://sourceforge.net/projects/garmin-gps/)
So I assume this is where you get it from.

To install this driver you'll need to install software that allows you to compile stuff:
```
sudo aptitude intsall build-essential
```

To compile the garmin kernel module, and to install it (must be run from the extracted directory containing the driver downloaded from the sourceforge site):
```
sudo ./compile.sh /usr/src/linux-headers-$(uname -r)
```

I haven't actually intsalled this, as I'm not sure why it's needed.

Once installed you may need to restart your machine, then you may need to run the kernel module by running:
```
sudo modprobe garmin-gps
```
This will work until you shutdown / restart your computer.

I can't quite remember how / where the configuration file is to get this module loaded automatically upon boot, but I'm sure it's just an internet search away.

I hope this is of help to you, and it'd be very much appreciated if you let me know why you need this kernel module.
ie if it magically can be made to work with gpsd I'd be a very happy man :) - but for gpsbabel, this driver isn't required (atleast for Ubuntu 9.04 anyway)

**Edit1:** Also, everytime you get a kernel update, you'll need to re-compile this kernel module.

**Edit2:** It looks as if the garmin-gps kernel module already comes with Ubuntu, it's just not loaded up upon boot.
- So you shold just be able to run the following to get your garmin-gps kernel module loaded (without having to compile anything):
```
sudo modprobe garmin-gps
```

---

