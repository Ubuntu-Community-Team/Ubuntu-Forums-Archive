---
title: "Emerald broken!"
date: 2008-03-02
forum: Desktop Effects &amp; Customization
---

### Post by tom66 on 2008-03-02
I get an 'E: Broken Packages' error whenever I try to install Emerald. 

```

thomas@orpheus:~$ sudo apt-get install emerald
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  emerald: Depends: libemeraldengine0 but it is not going to be installed
           Depends: libwnck18 (>= 2.15.90) but it is not installable
E: Broken packages
thomas@orpheus:~$ 

```

Please help! I've tried forcing versions, installing dependencies, uncommenting sources, etc. but it doesn't work. 

Thanks!

---

### Post by dolphinbrain on 2008-03-03
Hi tom66,

do you have feisty references in you /etc/apt/sources.list? That might cause the problem.

I had the following repositories acitvated for some other stuff:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe

This produced the same error that you described. When I commented the refs to feisty from /etc/apt/sources.list, I could install emerald just fine.

---

### Post by FuturePilot on 2008-03-03
Yes, make sure you don't have *any* Feisty repos in your sources.list

---

