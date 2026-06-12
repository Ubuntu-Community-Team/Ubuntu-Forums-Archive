---
title: "Fedora 2 vs Fedora 10 vs Ubuntu"
date: 2009-06-22
forum: General Help
---

### Post by RealG187 on 2009-06-22
So I am attending college and there is an upcoming Linux coarse. The book comes with disks (CD or DVD?) for Fedora 2, but there is an ISO on the school server for Fedora 10.

I am wondering which OS I should use. Fedora 2/10 or Ubuntu.

I am not sure if I should use Ubuntu, it might not be as true to the book as Fedora although I have been using Ubuntu more. However, maybe that is a reason why I should not use Ubuntu. I should really try another distro and this would be a good chance to.

Does Fedora 2 allow you to use USB flash drives, because that can be an issue, can it connect to Samba severs? Fedora 2 seems to be outdated, but Fedora 10 might not be as true to the book...

---

### Post by michy99 on 2009-06-22
If you have enough disk space, install them all!

---

### Post by RealG187 on 2009-06-22
Triboot? Is there any reason to have Fedora 2 if I have Fedora 10? Maybe I could run a VM of it just to see. Can I run VMs in Fedora?

---

### Post by Simian Man on 2009-06-22
Don't install Fedora 2.  It is ancient and has no support whatsoever. Fedora 10, however, is a great release.  There are a few differences between Fedora and Ubuntu, but the ideas are the same.

---

### Post by RealG187 on 2009-06-22
Someone I am taking the class with has Fedora 2 and I tried plugging in a USB drive with no luck and I could not transfer the file by plugging the device into my Windows PC and using samba.

Fedora 10 should be good right, like the basic OS is still the same, I think lots of the book is commands...

---

### Post by blueridgedog on 2009-06-22
> **RealG187 said:**
>  there is an ISO on the school server for Fedora 10.


There are ample differences in how the two systems start and shutdown as well as how the networking is configured.  The layout of the /etc files are generally different (but possessing the same files).

If your instructor expects a fedora system, then you are more likely to be able to follow along in class with FC10 than Ubuntu.

---

### Post by ibutho on 2009-06-22
Fedora 2 is really old and not worth the hassle in my opinion. Its no longer supported anyway, so personally I'd download Fedora 10 or 11.

---

### Post by RealG187 on 2009-06-23
Is 11 the newest? I kinda thought FC2 (FC=Fedora Core?) was old. FC10 isn't that old is it?

I will ask my instructor for advice as well...

---

### Post by kingchipo on 2009-06-23
unless ur in history class go with the fedora 10 or burn yourself a fedora 11

---

### Post by RealG187 on 2009-06-24
I [burned a copy of Fedora 10 and setup a VM](http://operation420.net/forum/viewtopic.php?f=20&t=320&p=1734#p1734) and installed VMWare tools, but when I run the config.pl it asks me for the location of GCC or something.

---

### Post by ibutho on 2009-06-24
> **RealG187 said:**
> I [burned a copy of Fedora 10 and setup a VM](http://operation420.net/forum/viewtopic.php?f=20&t=320&p=1734#p1734) and installed VMWare tools, but when I run the config.pl it asks me for the location of GCC or something.

You need to install the gcc compiler using the packaging tools e.g.
```
yum install gcc
```

---

### Post by RealG187 on 2009-06-24
Is yum like apt-get in Ubuntu?

---

### Post by sedawk on 2009-06-24
You need a basic compilation environment to compile VMWare kernel modules.

If you are running Ubuntu (on the host OS):
 sudo apt-get install build-essentials

If you are running Fedora (on the host OS) try
 yum install gcc

(I'm not sure the later one is sufficient, you might need more,
 e.g. linux headers. I can't check currently as I do not have
 a Fedora/RedHat system at hand ...)

---

### Post by sedawk on 2009-06-24
I forgot to tell:

* Use Fedora 10. There are (too) many changes between Fedora 10 and 11.

* There are major differences between Fedora and Ubuntu.
  E.g /etc/inittab exists in Fedora (but not in Ubuntu)
  and many Fedora configuration files are located in /etc/sysconfig
  which doesn't exist in Ubuntu. Fedora/RedHat has many configuration
  tools (/usr/[s]bin/system-* ?) that Ubuntu doesn't have.
  Stick to Fedora (for the training ...).

---

### Post by snowpine on 2009-06-24
My advice, do whatever the teacher tells you--if the assignment is to figure out how to do something in Fedora 2, then you'd better do it in Fedora 2 if you want an A! You can set up a virtual machine so you don't have to replace your nice Ubuntu install. ;)

---

### Post by blueridgedog on 2009-06-24
> **sedawk said:**
> 
 sudo apt-get install build-essentials




oddly enough, the package is build-essential, without the s.

---

### Post by RealG187 on 2009-06-24
> **sedawk said:**
> You need a basic compilation environment to compile VMWare kernel modules.
They should include that in the RPM package I installed.

Anyways, for some reason my Fedora 10 VM doesn't start. After the loading bar it just stays there. The screen blanks like power saver is on, so I assume it loaded that much OS.

---

