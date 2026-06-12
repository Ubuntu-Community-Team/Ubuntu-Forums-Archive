---
title: "PC freezes frequently"
date: 2009-05-28
forum: General Help
---

### Post by satimis on 2009-05-28
Hi folks,

Ubuntu 9.04 workstation, newly installed

The PC freezes frequently. Pressing [Num Lock] doesn't turn on the LED light.  It requires pressing the reset switch on the box to restart PC.  Please advise where to check and how to fix the problem.  TIA

B.R.
satimis

---

### Post by spiceminesofkessel on 2009-05-28
What is occurring when the system freezes? How old is the system? Does it randomly freeze without any warning or symptom? How long does it take for the system to freeze once the system is booted?

---

### Post by satimis on 2009-05-28
> **spiceminesofkessel said:**
> What is occurring when the system freezes? How old is the system? Does it randomly freeze without any warning or symptom? How long does it take for the system to freeze once the system is booted?
Hi,

The PC is about 2 years old running AMD X2 with 4G RAM onboard.  Freezing occurs randomly.  I can't forecast when it'll freeze.  Now I have been working for about 20 min. without problem.

B.R.
satimis

---

### Post by DeMus on 2009-05-28
> **satimis said:**
> Hi,

The PC is about 2 years old running AMD X2 with 4G RAM onboard.  Freezing occurs randomly.  I can't forecast when it'll freeze.  Now I have been working for about 20 min. without problem.

B.R.
satimis

Do you run Compiz?
It's a source for trouble. If you use it, try switching it of for some time to see if the problems are gone.

---

### Post by ptn107 on 2009-05-28
I have had similar problems on Jaunty 64-bit when manipulating files and folders that were big (>3gb) and when exiting games that utilized my proprietary graphics drivers.  I've upgraded to a more recent kernel* (along with recent video drivers) and that has seemed to fix all the freeze problems so far.

*The latest Jaunty kernels are based on 2.6.28.9, but the most *recent* stable version is 2.6.29.4.  These packages are NOT supported by Ubuntu and you will not receive bug fixes and security updates to these kernels if you decide to use them.

For 32-bit you need these:
[linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb")
[linux-headers-2.6.29-02062904-generic_2.6.29-02062904_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904-generic_2.6.29-02062904_i386.deb")
[linux-image-2.6.29-02062904-generic_2.6.29-02062904_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_i386.deb")

For 64-bit you need these:
[linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb")
[linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb")
[linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb")

Either architecture can be installed by typing the following in the folder containing those downloaded files:
```
sudo dpkg -i *.deb
```
A reboot will be required.

---

### Post by satimis on 2009-05-28
> **DeMus said:**
> Do you run Compiz?
It's a source for trouble. If you use it, try switching it of for some time to see if the problems are gone.
No.

satimis

---

### Post by satimis on 2009-05-28
> **ptn107 said:**
> I have had similar problems on Jaunty 64-bit when manipulating files and folders that were big (>3gb) and when exiting games that utilized my proprietary graphics drivers.  I've upgraded to a more recent kernel* (along with recent video drivers) and that has seemed to fix all the freeze problems so far.

*The latest Jaunty kernels are based on 2.6.28.9, but the most *recent* stable version is 2.6.29.4.  These packages are NOT supported by Ubuntu and you will not receive bug fixes and security updates to these kernels if you decide to use them.

For 32-bit you need these:
[linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb")
[linux-headers-2.6.29-02062904-generic_2.6.29-02062904_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904-generic_2.6.29-02062904_i386.deb")
[linux-image-2.6.29-02062904-generic_2.6.29-02062904_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_i386.deb")

For 64-bit you need these:
[linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb")
[linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb")
[linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb")

Either architecture can be installed by typing the following in the folder containing those downloaded files:
```
sudo dpkg -i *.deb
```
A reboot will be required.

Hi ptn107,

Thanks for your advice.

Ubuntu 9.04 32bit

$ uname -a```

Linux server1.satimis.com 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

```
I think I have to upgrade the kernel.


B.R.
satimis

---

### Post by ptn107 on 2009-05-28
> **satimis said:**
> 
I think I have to upgrade the kernel.


I'd give it a try.  It can always be removed if you don't see an improvement.

---

