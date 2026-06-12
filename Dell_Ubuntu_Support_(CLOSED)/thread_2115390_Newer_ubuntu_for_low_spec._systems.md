---
title: "Newer ubuntu for low spec. systems"
date: 2013-02-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by joco1500 on 2013-02-12
Hello all.
I am going to get right to the point.

I have a dell latitude d400 and running ubuntu 11.10 (barely) 
have to use gnome 2

I would like to know if there is a version of striped down ubuntu that will run on this. 

or if there is a verson of Lubuntu of Xubuntu that as gnome or unity.

thankyou

---

### Post by cwsnyder on 2013-02-12
GNOME 3, Unity, and KDE are full-fat DEs and strain any computer with less than 1G RAM, 2GHz dual processor, and video system capable of providing graphics acceleration.

You are either going to have to upgrade your hardware or downgrade your expectations to LXDE, Xfce, or another low demand DE if Ubuntu 11.10 with Unity barely runs on your machine.  Sorry.

---

### Post by ibjsb4 on 2013-02-12
I wouldn't necessarily call it a down grade.  Xubuntu is pretty full featured in my opinion and should run good on a box with 500M of ram.

  [http://xubuntu.org/screenshots/](http://xubuntu.org/screenshots/)

---

### Post by kurt18947 on 2013-02-13
+1 to Xubuntu or Lubuntu.  That machine has what may be an earlier Pentium M processor.  I wonder if it support PAE extensions?  As I understand it, some Pentium M processors do, others do not.  If not, you'll need a non-PAE kernel which* I think - not certain* that 12.04 Xubuntu & Lubuntu are.  Here's one way to tell if your processor supports PAE.  Run this command in a terminal

```
cat /proc/cpuinfo
```

Here's a porton of  mine
> 
flags        : fpu vme de pse tsc msr _**pae**_ mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm


so this processor does support PAE.  Also, Xubuntu and Lubuntu are less demanding of graphics subsystems.

---

