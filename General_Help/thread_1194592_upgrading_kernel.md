---
title: "upgrading kernel"
date: 2009-06-22
forum: General Help
---

### Post by linuxtu on 2009-06-22
When upgrading kernel on Ubuntu, what's the command that you use?
Is the following command that's normally used?
>  
apt-get dist-upgrade

 
When I run that, it auto installs other packages and I'm not sure if they're depenencies
>  
The following NEW packages will be installed:
libdns35 libisc35 linux-image-2.6.24-24-server
linux-ubuntu-modules-2.6.24-24-server
The following packages will be upgraded:
bind9-host dnsutils libbind9-30 libisccc30 libisccfg30 linux-image-server
linux-server
7 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.3MB of archives.

 
Thanx

---

### Post by Sub101 on 2009-06-22
If im understanding your problem correctly, and that is that you want to install new kernels, then the method you are using seems to work.

The package linux-image-****** is the new kernel.

It may not be the right way of doing things but I tend to upgrade my kernels using ```
sudo apt-get update
sudo apt-get updgrade
```

Im sure one way is better than the other. But I guess whatever works.

---

### Post by CatKiller on 2009-06-22
> **Sub101 said:**
> Im sure one way is better than the other. But I guess whatever works.

They do slightly different things. From **man apt-get**:

> 
       **upgrade**
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

       **dist-upgrade**
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages. The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.


---

### Post by linuxtu on 2009-06-23
Thanks for the replies.
When I do apt-get update && apt-get upgrade, it skips the kernel install.
If I do apt-get dist-upgrade, and when the new ubuntu version comes out, will it upgrade to the newest ubuntu version?  All I want to do is update to the kernel.

---

### Post by CatKiller on 2009-06-23
> **linuxtu said:**
> Thanks for the replies.
When I do apt-get update && apt-get upgrade, it skips the kernel install.

I'm pretty sure that I get kernel updates with apt-get upgrade. I normally use Update Manager, though, so I could be mistaken.

> 
If I do apt-get dist-upgrade, and when the new ubuntu version comes out, will it upgrade to the newest ubuntu version?  All I want to do is update to the kernel.

I don't think so, unless you've changed your sources.list to point to the new version - changing all the instances of jaunty to karmic, for example.

---

### Post by AlexsAntidote on 2009-06-23
Do you happen to know which kernel you want to upgrade to, specifically?

There's a nice tutorial here: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Have fun.

---

