---
title: "Dell mini with Dell Lpia 8.04 &amp; Virtual Box - Anyone get it working?"
date: 2008-11-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RichTJ99 on 2008-11-11
Hi,

I am running the LPIA version of Ubuntu that Dell made for the mini 9.  I was curious if anyone has been able to get Virtual Box working on the mini?  I am using the mini as a mobile laptop for troubleshooting in windows but I would prefer to use Ubuntu. 

Plus with a 16gb drive, a dual boot XP/Ubuntu machine might not be so great in terms of space.  

Thanks,
Rich

---

### Post by yakker.yak on 2008-11-11
> **RichTJ99 said:**
> Hi,

I am running the LPIA version of Ubuntu that Dell made for the mini 9.  I was curious if anyone has been able to get Virtual Box working on the mini?  I am using the mini as a mobile laptop for troubleshooting in windows but I would prefer to use Ubuntu. 

Plus with a 16gb drive, a dual boot XP/Ubuntu machine might not be so great in terms of space.  

Thanks,
Rich

Just came across [this]("http://www.mydellmini.com/forum/*-deb-installing-t433.html") on another forum (scroll down to the last post on the page).

It should enable you to install i386 DEBs on the lpia Dell Ubuntu without needing to do any repackaging.

I can't test it myself (ETA for my Mini 9 was today but yet to arrive) but perhaps worth a try ...

---

### Post by RichTJ99 on 2008-11-12
I get the following error message:

Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-<version> whereby <version> can be determined by 'uname -r') and execute

  /etc/init.d/vboxdrv setup

as root.

Thats as far as I get. Am I doing something wrong?

---

### Post by RichTJ99 on 2008-11-12
Here is the log error:

Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

---

### Post by yakker.yak on 2008-11-12
Looks like you need to install the kernel header files.

Open up Synaptic:
System -> Administration -> Synaptic

Search for 'linux-headers'

Select the one that's most generic (i.e. linux-headers-2.6.24-19), right-click it, and mark it for installion.

Click on Apply to start the installation.

Then try to install VirtualBox again and see if it can successfully build the kernel modules.

---

### Post by abakus on 2008-11-12
No unfortunately installing linuxheader doesn't work , it always complain about something like "to many levels of symbolic links" when trying to compile.

---

### Post by RichTJ99 on 2008-11-12
Is the a terminal command for that?  I cant find it in syaptic

---

### Post by RichTJ99 on 2008-11-12
Hrmm, do you think VMware would work on a Lpia system?  

I actually renamed the folders that had a 386 in it to lpia, recompiled & the install worked perfectly with no errors, unfortunately, when I try to run the program, it doesnt work at all.

---

### Post by yakker.yak on 2008-11-12
> **RichTJ99 said:**
> Hrmm, do you think VMware would work on a Lpia system?  

I actually renamed the folders that had a 386 in it to lpia, recompiled & the install worked perfectly with no errors, unfortunately, when I try to run the program, it doesnt work at all.

The VMWare installer is command-line and builds modules for your kernel as part of the setup. Two thoughts come to mind:

1) Install the build-essential package from the repos.

2) Run the VMWare installer with administrator privileges (sudo).

That is, once you've extracted the vmware installer tar.gz open up a terminal, change directory to where you extracted the files, and do:
```
sudo ./vmware-install.pl
```

You may get a warning about gcc version incompatibilities during the install. Ignore these when given the option and try to continue. Worked fine for me on another (non Mini) Hardy system.

---

### Post by RichTJ99 on 2008-11-12
Im giving up for tonight.  I think I would like Virtualbox more since, well its free & I am used to it from my current laptop.  Maybe I will just do a dual boot?  I hate to do that though.

If 386 wasnt so much slower than Lpia, I would give it a try (I keep reading about how its much slower).

---

### Post by bturig on 2009-03-18
i had to enter the following commands in the terminal to get vbox to re-compile itself error free with the kernel.

sudo apt-get install build-essential

sudo apt-get install linux-headers-`uname -r`

---

