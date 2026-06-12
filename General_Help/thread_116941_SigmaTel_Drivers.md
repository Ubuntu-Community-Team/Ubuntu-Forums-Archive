---
title: "SigmaTel Drivers"
date: 2006-01-13
forum: General Help
---

### Post by pianoboy3333 on 2006-01-13
I have an integrated SigmaTel card. Does anyone know where I can get linux/ubuntu drivers?

---

### Post by pianoboy3333 on 2006-01-14
Please?

---

### Post by pianoboy3333 on 2006-01-14
I downloaded the linux driver from here: [http://www.sigmatel.com/support/#drivers](http://www.sigmatel.com/support/#drivers) but how do I install them?

---

### Post by kosmic on 2006-01-14
Are you sure that your card is not been recognised ?
 
If the driver you donwload is for Window$ you can't install it in Ubuntu or any linux distro

---

### Post by pianoboy3333 on 2006-01-14
No, it's a linux driver, how do I use 'make' after I unzipped it onto my desktop?

---

### Post by kosmic on 2006-01-14
To compile a program you need the binutils package, the g++, and gcc all available in synaptic.
 
 
There should be a Readme file in the zip, but it should be something like this :
 
./configure
./make
./makeinstall or make install or also if you want to build a .deb ./checkinstall

---

### Post by pianoboy3333 on 2006-01-14
I have the binutils package, g++, and gcc. After I un zip (or I guess un-tar) I have the folder on my Desktop. Inside there is:

/home/alex/Desktop/irda4210/tools
/home/alex/Desktop/irda4210/gpl.txt
/home/alex/Desktop/irda4210/irda-ioctl.h
/home/alex/Desktop/irda4210/irda-usb.c
/home/alex/Desktop/irda4210/irda-usb.h
/home/alex/Desktop/irda4210/Makefile
/home/alex/Desktop/irda4210/README

Inside of the tools folder there is:

/home/alex/Desktop/irda4210/tools/getargs.c
/home/alex/Desktop/irda4210/tools/Makefile
/home/alex/Desktop/irda4210/tools/sgtlpatch
/home/alex/Desktop/irda4210/tools/stir42xx.c
/home/alex/Desktop/irda4210/tools/stir42xxi.h

---

### Post by kosmic on 2006-01-14
ok, in this file /home/alex/Desktop/irda4210/README with should give you the steps needed to install the driver

---

### Post by pianoboy3333 on 2006-01-14
OK, I have to run some errands, I'll brb in a couple of hours.

---

### Post by pianoboy3333 on 2006-01-14
Here's the README file, but I'm new to ubuntu, and I don't really understand it.

These driver files are here to help you get started.  You will at least 
need to install the driver into the kernel loadable modules directory
for IrDA (.../kernel/drivers/net/irda) and then insert the module (insmod).

The following modules are incompatible with this driver and on some
versions of Linux, these modules must be removed from the kernel:

   ir-usb
   irda-usb

You might need to insmod the "irda" module before starting.

Before running "make," check the values of LINUX_VERSION,
INLUDEDIR and MODPATH.

Before releasing anything, update the IRDA4210_VERSION string, which
gets embedded in the module.

All devices supported by this driver require a firmware patch to run.
Failing to install a patch into the device (or installing the wrong
patch) can result in a lockup of the USB bus (and the entire system).
For your protection, the driver will not allow you to open the device
unless you first apply the patch.

The "stir42xx" utility in the "tools" directory will install a patchfile.
The patch files are firmware that run in the device and are not available
with this distribution, since they are not covered under the GNU GPL.
Run "stir42xx --help" for more information.

The "sgtlpatch" script attemps to determine the version of the attached
device and will select the appropriate patch file that it finally passes
to the stir42xx utility.

---

### Post by kosmic on 2006-01-14
ok have a look at this page -> [http://www.hpl.hp.com/personal/Jean_Tourrilhes/IrDA/IrDA.html#config]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/IrDA/IrDA.html#config")

---

### Post by pianoboy3333 on 2006-01-15
But I don't compile my own kernal.

---

### Post by billevans100 on 2006-04-27
gday ive got aa infra red usb and i cant get it to work when i put it in it says "found new hardware - STI42xx". How can i get it to work please reply

---

### Post by dragonfixed on 2006-10-13
where did you get the drivers for the sigmatel stac9200 linux drivers from and can you provide a link to the drivers

---

### Post by mostafaberg on 2008-04-16
hello !,

did you get any luck making it run ?, i have a USB IrDA dongle.

the link you gave us in this thread doesn't contain any linux drivers.

I think the link is outdated, can you give us a new link ? or just send it to me and i'll host it for other members to download 

Thanks !.

---

