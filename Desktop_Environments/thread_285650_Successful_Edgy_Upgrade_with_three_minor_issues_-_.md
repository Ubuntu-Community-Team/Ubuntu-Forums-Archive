---
title: "Successful Edgy Upgrade with three minor issues - some help please!"
date: 2006-10-27
forum: Desktop Environments
---

### Post by jackkerouac on 2006-10-27
Okay, I upgraded to Edgy using the package manager, got a mighty 21 kB/s (ha) and after several hours, the upgrade was done.

Three issues popped up, two of which I have solved.

**1. X Server Died**

I solved this by just using:

```
sudo apt-get install xserver-xorg-driver-radeon
```

Then I re-installed my ATI fglrx drivers using [this guide]("http://www.google.ca/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwiki.cchtml.com%2Findex.php%2FUbuntu_Edgy_Installation_Guide&ei=iKZBRZ-HFIr2gAKT8PzgCQ&usg=__oHzOJqUbFp84mV_Q_fAth1ST70o=&sig2=J71BjLh2UPM8zbwtti6Wqw").

**2. Themes would not appear.**

I solved this problem (I use XGl and Beryl with Kiba-Dock) by entering in:

```
gnome-settings-daemon
```

Under System -> Preferences -> Sessions -> Startup Programs

**3. My kernel is now 2.6.17-10-generic.**

Before the upgrade, I used the k7 version of the kernel, but I cannot find it in the repos. Can someone please let me know why it's not there or how I can find it? I noticed an immediate increase in speed with the k7 version.

Thanks!

---

### Post by Tux Aubrey on 2006-10-27
Hey. I know this one! I know this one!

> **3. My kernel is now 2.6.17-10-generic.**

Before the upgrade, I used the k7 version of the kernel, but I cannot find it in the repos. Can someone please let me know why it's not there or how I can find it? I noticed an immediate increase in speed with the k7 version.

As I understand it, the -686 and -k7 versions of kernels have been discontinued, at least for edgy, because all the relevant features have been built into the -generic version.  Basically, we no longer need them.

---

### Post by iamhugeinjapan on 2006-10-27
The K7 and 686 kernels were consolidated into "generic" for Edgy.

---

### Post by jackkerouac on 2006-10-27
> Hey. I know this one! I know this one!

Thanks guys! Awesome news. I also get giddy when I know an answer to someone's problem.

---

### Post by kolesarm on 2006-10-27
> **jackkerouac said:**
> Okay, I upgraded to Edgy using the package manager, got a mighty 21 kB/s

I got 14 kB/s - only took me 16 hrs:)

> **jackkerouac said:**
> (ha) and after several hours, the upgrade was done.

Three issues popped up, two of which I have solved.

**1. X Server Died**

Had the same problem - had to reinstall X. Wasn't good news after waiting all night!

> **jackkerouac said:**
> 

**3. My kernel is now 2.6.17-10-generic.**

good to know - I was also confused when I saw it first

---

