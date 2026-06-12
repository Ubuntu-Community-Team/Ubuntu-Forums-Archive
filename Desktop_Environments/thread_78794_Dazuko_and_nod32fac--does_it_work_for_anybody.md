---
title: "Dazuko and nod32fac--does it work for anybody?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by dgermann on 2005-10-18
Hi--


Well, I have gotten nod32 to work for cron jobs and for auto update of the virus sig files, but this nod32fac does not seem to go for me.

I have gotten dazuko installed and run the example_c program and it appears to operate as advertised. nod32fac.log shows that it started up. But I download eicar.com, eicar_com.zip and eicarcom2.zip, and then try to double click on them to open them, and it allows me to do that. Should it not prevent me from doing so?

What am I missing? Any other place to go for an answer? nod's tech guy seems out of answers, is not really a linux command line guy....

Thanks for any help you can give me!:D

---

### Post by abandoned_hussam on 2005-10-22
Sorry for the irrelvant question, but how did you get dazuko module to install under breezy?

---

### Post by dgermann on 2005-10-22
hussam--

Here are my notes showing what I did:

I followed [http://ubuntuforums.org/archive/index.php/t-52385.html](http://ubuntuforums.org/archive/index.php/t-52385.html) :
```
upgraded dpkg and one related which were already installed.
wget http://www.dazuko.org/files/dazuko-source_2.1.0-1_all.deb
dpkg -i dazuko-source_2.1.0-1_all.deb
needs module-assistant
apt-get install module-assistant
m-a a-i dazuko 
Warning, /usr/src/linux seems to contain unconfigured kernel sourc!1
several like that, then:
Bad luck, ther kernel headers for this kernel version could not be found and you did not specify other kernel headers to use.
However you can install the header files for your kernel which are provided by the linux-header-2.6.10-5-386 package. For most modules packages, this files are perfectly sufficint whithou having the original kernel source. To install the package, run the PREPARE command from the main menu, or on the command line:
Pacage dazuko-source was not built successfully, see /var/cache/modass/dazuko-source*buildlog* for details!
module-assistant, hit esc when at a response, got menu and chose Prepare--done!
m-a a-i dazuko 
seemed to work!
gedit /etc/modules
and write in dazuko in this file (I've written it before ide-cd but I don't think it matters).
This makes it the first item.
Reboot the computer! You can test if dazuko loaded properly by issuing the "lsmod | grep dazuko" command
well, it's there!
```

Hope that helps you, hussam!

---

### Post by abandoned_hussam on 2005-10-22
the install worked but now, the dazuko kernel module will not load because of another module "capability". How do I get dazuko to load before capability?

---

### Post by fannymites on 2005-10-22
I've also been trying to compile dazuko (to work with AntiVir) but after the reboot lsmod | grep dazuko lists nothing and when I try modprobe I get this - 
```
FATAL: Error inserting dazuko (/lib/modules/2.6.12-9-k7/kernel/dazuko/dazuko.ko): Invalid argument
```
and with insmod I get this - 
```
insmod: error inserting '/lib/modules/2.6.12-9-k7/kernel/dazuko/dazuko.ko': -1 Invalid parameters
```

---

### Post by abandoned_hussam on 2005-10-22
If I sudo rmmod capability , I can sudo modprobe dazuko and then sudo modprobe capability.
So we need to find a way to load dazuko before capability. 
Anybody smart can help here :) ?

---

### Post by fannymites on 2005-10-22
It looks like capability is cause of my problem cos when I try what hussam said then it works.

---

### Post by abandoned_hussam on 2005-10-22
so somehow we either want to delay capabilty or make dazuko start very early in the boot process. anybody got an idea?

---

### Post by dgermann on 2005-10-23
HI all--

Yes, capability must be loaded after dazuko. I think you just need to unload capability, inser Dazuko, then insert capability.

```
rmmod capability
insmod dazuko.ko
modprobe capability
```
worked for me.

Instructuctions at [www.dazuko.org/tgen.shtml#DEBIAN](www.dazuko.org/tgen.shtml#DEBIAN) say this also.

I also gedited /etc/modules to put dazuko in as first line.

Does that help?

Is anybody working on installing nod32fac?

---

### Post by fannymites on 2005-10-23
Sorry, I have no knowledge of nod32fac.
Both Antivir and Clamav/Klamav background guards work fine if I manually reload the modules then start the background guard but there doesn't seem to be anyway to change the order they load at boot and adding dazuko to /etc/modules doesn't work for me. 
Doing it all manually everytime I load up ubuntu is too much of a pain.
It is possible to get dazuko loading before capability on Fedora Core by editing /etc/sysconfig.
Is there an ubuntu equivalant to sysconfig?

[EDIT]  I also read somewhere that capability can be disabled by adding capability=0 as a boot option in the grub config but I don't like the idea.  What exactly does capabilty do?  I've read it is a security module but I can't find any info.

---

### Post by fannymites on 2005-10-23
Ok, I sort of got this working in a round about sort of way.
I haven't had any experience of creating shell scripts but I tried creating a script like this - 
```
#!bin/bash
rmmod capability
modprobe dazuko
modprobe capability
```

This unloaded capability and loaded dazuko but didn't reload capability so I have tried making 2 scripts, one with ```
#!bin/bash
rmmod capability
modprobe dazuko

```

and then another with this - ```
#!bin/bash
modprobe capability
```

I named them dazuko and capability respectively then moved them to /etc/init.d

I checked the startup scripts for Antivir and made sure my new scripts started before them like this.

[EDIT] Just noticed a mistake with this next bit of code, I originally typed updaterc.d when it should have been - 
```
sudo update-rc.d dazuko defaults 10
sudo update-rc.d capability defaults 15
```

I have tried this with Antivir and on boot, dazuko and capability are both in lsmod and the Antivir background guard works.  I can't work out how to make the Klamav background scanner to start on every boot, it seems I have to manually start the background guard every time but it does run fine.

If anyone can tell me a less messy way to do the shell scripts such as being able to use one rather than two I would be grateful.

---

### Post by sk545 on 2005-10-30
anyone find a better way yet?  The latest dazuko pre release has the same problem with capability loading first.

---

### Post by ZoltanPatay on 2006-01-06
Proper module loading can be done using the modprobe.d:

Create a file in /etc/modprobe.d/dazuko

and add the following to it (copy paste and then save changes):

--copy bellow--(you dont need this line)

install dazuko /sbin/modprobe -r capability;\
/sbin/modprobe --ignore-install dazuko; \
/sbin/modprobe --ignore-install capability

--copy end---(you dont need this line)

add to your /etc/modules a single line (and save it) that says:

dazuko

Now when the dazuko module insertion is called, the capability gets removed, dazuko inserted and capability reinserted.

---

### Post by digiplaya on 2007-09-09
Am a straggler with Gusty System, trying this right now! Hope Dazuko plays nicely now thanks for the instructions Zoltan

Tom Anderson

---

