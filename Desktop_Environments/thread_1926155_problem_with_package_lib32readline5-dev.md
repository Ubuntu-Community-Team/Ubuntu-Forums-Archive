---
title: "problem with package lib32readline5-dev"
date: 2012-02-15
forum: Desktop Environments
---

### Post by forsubhi on 2012-02-15
when I execute the command sudo apt-get install   lib32readline5-dev I faces the following  problem 
what is the problem 
please help me ! 

```
subhi@subhi-pc:~$ sudo apt-get install   lib32readline5-dev  Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lib32readline5-dev : Depends: lib32readline5 (= 5.2-3build1) but 5.2-9ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.
subhi@subhi-pc:~$
```

---

### Post by jerrrys on 2012-02-16
Got your backports enabled?

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=lib32read](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=lib32read)

---

### Post by forsubhi on 2012-02-16
I don't understand what you mean , can you explain more ?

---

### Post by technophobe01 on 2012-10-14
Check out the following:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Stability of Backports
When using Backports, it is important to understand that there is an inherent risk in backporting software. Although backported packages are tested by the community before they are included in the repository, there are very occasionally bad interactions with the older software on your system that are overlooked.

Additionally, the very nature of Backports means that backported packages will change the behavior of the package in ways that may be unfamiliar to users of the older versions, and may be incompatible with configuration format and other options of the older versions.

For this reason, the Backports Team recommends configuring the package manager to only install backported packages when they are explicitly requested, which is the default for all Ubuntu releases after and including Ubuntu 11.04 (Natty Narwhal).

Using Backports
There are two steps to configuring Ubuntu Backports; due to changes in Ubuntu, each step may or may not be necessary on a given release.

First, you must ensure that apt is configured with Backports enabled. On releases after and including Ubuntu 11.10 (Oneiric Ocelot), this is not necessary, as apt is configured with Backports enabled by default.

Second, you must determine whether apt should automatically install packages from Backports, or only install packages from Backports when they are manually requested. The Ubuntu Backporters Team recommends the latter option, and this was made the default for all releases after and including Ubuntu 11.04 (Natty Narwhal). The default for releases prior to Ubuntu 11.04 was to automatically install packages from Backports.

Enabling Backports
Backports were not enabled by default for all releases before (but not including) Ubuntu 11.10 (Oneiric Ocelot). On these releases, backports must be manually enabled before you can install packages from Backports.

Enabling Backports on Ubuntu Desktop

Open the Software Sources control applet. On Ubuntu 10.10 and earlier, click System -> Administration -> Software Sources. On Ubuntu 11.04 and later, search for Software Sources in the Dash.

You will be asked to enter your password. Once you have done that, switch to the Updates tab.

Make sure Unsupported updates is checked.

Enabling Backports on Kubuntu

Search for and start the Muon Package Manager in the KMenu.

Once the Muon Package Manager opens, click Settings -> Configure Software Sources

You will be asked to enter your password. Once you have done that, switch to the Updates tab.

Make sure Unsupported updates is checked.

Enabling Backports Manually

---

