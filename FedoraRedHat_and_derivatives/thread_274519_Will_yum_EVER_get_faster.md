---
title: "Will yum EVER get faster??"
date: 2006-10-09
forum: Fedora/RedHat and derivatives
---

### Post by jdong on 2006-10-09
I'm not gonna do a FC6 Preview review, but I've just installed the test release on my AMD64 shuttle (32-bit edition). My overall review is quite positive with the overall FC6 polish. Performance is definitely a vast improvement from FC5, but compared to Edgy it's about the same, so I attribute it to general upstream improvements.

One gripe I have is, after installing it, there were 194 updates available as reported by puplet, but from the time I opened the updater to the time it finished resolving dependencies, 7 minutes passed. On a AMD64 hooked up to a 500KB/s download pipeline, this is quite unacceptable. It takes ubuntu's distribution updater around 5 seconds on that box to calculate a dapper to Edgy upgrade (25 seconds if you count an apt-get update to be fair).

Will yum ever get faster? I don't know, but that is one of the biggest turnoffs for me when it comes to Fedora Core.

---

### Post by tseliot on 2006-10-10
I know what you mean...

If only they used something like pacman (Arch Linux) or apt, things would be much faster.

---

### Post by clint1010 on 2006-10-11
Apt would be the way to go. But they would have to stick with yum and their rpm packaging system to prevent fedora/redhat kaos if it was changed.

---

### Post by bluenova on 2006-10-11
Yum was the biggest reason I moved to Ubuntu. I never again want to have to get my software from 30 differnt sources.

---

### Post by hey_ian on 2006-10-16
Everyone who tried APT will know that it is faster and better than YUM. Anyway I think you can install apt-rpm on a Fedora Core system. This is just the same APT as in Debian but ported to the RPM system instead of dpkg.

---

### Post by jdong on 2006-10-16
I prefer not to use APT4RPM.... IMO yum is more reliable and supported on RPM systems. Also, if you are on x86-64, yum is the only frontend that supports multiarch (i.e. yum install firefox.i386)

---

### Post by chaosgeisterchen on 2006-10-23
Question: Is KDE really performing faster than with Kubuntu with FC 6?

---

### Post by jdong on 2006-10-23
The difference is not significant.

---

### Post by chaosgeisterchen on 2006-10-23
Too bad.

---

### Post by tseliot on 2006-10-23
> **jdong said:**
> Also, if you are on x86-64, yum is the only frontend that supports multiarch (i.e. yum install firefox.i386)
That's a cool feature. I might try Fedora Core 6 x86-64.

Does Fedora 64bit work fine?

---

### Post by jdong on 2006-10-23
It works just as well as Ubuntu 64-bit or SUSE 64-bit or most other modern distro 64-bit support... nothing groundbreaking, nothing crippling other than the usual culprits (proprietary/non-free stuff), but most people don't run Fedora for out-of-the-box win32codecs support anyway :D

---

### Post by jdong on 2006-10-31
UPDATE: After using Yum for a while, it does get substantially better. Namely, once you grab a bunch of the RPM headers, you don't need to do it anymore, which greatly speeds up YUM work. It's better than I initially thought, but nonetheless the initial 30+ minute rpm header fetching session is unacceptably slow.

---

### Post by raqball on 2006-11-01
When I was on Suse I used smart and it worked great.

I don't think yum will ever get better :)

---

### Post by hey_ian on 2006-11-01
> **raqball said:**
> When I was on Suse I used smart and it worked great.

I don't think yum will ever get better :)

As a matter of fact that is also my opinion. I do not know why they do not want to change the package manager and take e.g. smart.

---

### Post by hey_ian on 2006-11-01
> **jdong said:**
> UPDATE: After using Yum for a while, it does get substantially better. Namely, once you grab a bunch of the RPM headers, you don't need to do it anymore, which greatly speeds up YUM work. It's better than I initially thought, but nonetheless the initial 30+ minute rpm header fetching session is unacceptably slow.


It is right you do not have to reload the RPM headers, but it is recommended to do that and it does not take 30+ minutes, but approx. 5 minutes. You should clean the YUM cache with "yum clean all" if you want to install new software. You do the same if you want to install a new package in Debian, but we call it apt-get update. :-D

---

### Post by jdong on 2006-11-01
This is my 5th or 6th fresh install of FC5/6, and I can say with consistency that the process of calculating the first upgrade takes no less than 30 minutes on the first run. apt-get update is never that laggy...

---

### Post by hey_ian on 2006-11-02
> **jdong said:**
> This is my 5th or 6th fresh install of FC5/6, and I can say with consistency that the process of calculating the first upgrade takes no less than 30 minutes on the first run. apt-get update is never that laggy...


Of course APT is not as slow and laggy as yum. I thing the only one alternative using Fedora Core is to install Smart Package Manager instead of yum.

---

