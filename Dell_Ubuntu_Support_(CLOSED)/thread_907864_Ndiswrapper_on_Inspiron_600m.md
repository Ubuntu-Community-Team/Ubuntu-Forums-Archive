---
title: "Ndiswrapper on Inspiron 600m"
date: 2008-09-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zrs_12 on 2008-09-01
Ok, I am dual booting Win XP and Kubuntu 8.04.1 KDE 4.  I downloaded the ndiswrapper (on XP because I have my drivers installed on it) and put it on a flash drive.  I booted Kubuntu and extracted ndiswrapper.  Then I went and read the file it gives about how to install it.  I followed the directions word for word (except it didn't say make uninstall and make as root but I had to because I didn't have sufficient permission otherwise).  However, on the make and make install parts I kept getting errors, but I kept going.  When it got to the part to install the driver ("ndiswrapper -i driver.inf"), I was notified that ndiswrapper wasn't installed and I needed to apt-get it.  Well, that won't work because the whole reason I need it is to connect to the internet (apt-get and surf and stuff).  I can't figure out what the problem is.  Any ideas?  TIA

---

### Post by prshah on 2008-09-01
> **zrs_12 said:**
> I was notified that ndiswrapper wasn't installed and I needed to apt-get it.  Well, that won't work because the whole reason I need it is to connect to the internet

ndiswrapper is available on the CD from which you installed ubuntu. For more details, including how to install ndiswrapper from the CD, refer to [[SOLVED] How to activate WG311v3 (or any ndiswrapper or native) wireless]("http://ubuntuforums.org/showthread.php?t=756260") for a step-by-step command line process to install ndiswrapper and setup wireless.

Post back here if you run into problems.

---

### Post by zrs_12 on 2008-09-02
Well, that didn't work.  Here's what I get:

```
zachary@laptop:~$ sudo apt-get install ndiswrapper-utils*
[sudo] password for zachary:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndiswrapper-utils*
```

(Note: This is while I had the CD from which I installed Kubuntu in the CD drive)

---

### Post by prshah on 2008-09-03
> **zrs_12 said:**
> 
E: Couldn't find package ndiswrapper-utils*


Try this: Type "sudo apt-get install ndis" (without quotes), but DON'T press enter.

Now, immediately after the "ndis" bit, press tab, twice, in rapid succession.

If you've done it correctly, you should immediately get a list of packages available to your system, which start with the word "ndis". Eg, on my system:```
Wed Sep 03 00:39:40 ~:$ sudo apt-get install ndis<Tab><Tab>
ndisc6                   ndiswrapper-modules-1.9  ndiswrapper-utils-1.9
ndisgtk                  ndiswrapper-source       
ndiswrapper-common       ndiswrapper-utils    

```

Select one from the list and type it out fully. You should choose ndiswrapper-common and ndiswrapper-utils-1.9 (or equivalent shown in your list).

btw, this process of having the system suggest suitable choices is called "Tab completion". It is a feature of bash, and is relatively intelligent; when you use it with "cd" it will only list directories, when you use it with "modprobe" it will only list available modules, with "apt-get" it will list available package names.

Post back if no suitable choices are shown.

---

