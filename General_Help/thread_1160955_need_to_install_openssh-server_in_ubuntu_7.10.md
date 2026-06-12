---
title: "need to install openssh-server in ubuntu 7.10"
date: 2009-05-16
forum: General Help
---

### Post by taimur on 2009-05-16
hi
i want to install openssh-server in ubuntu but this error is coming 
ubuntu@ubuntu-razza:~$ sudo -i
[sudo] password for ubuntu:
root@ubuntu-razza:~# apt-get install openssh-server
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

The following packages have unmet dependencies:
  openssh-server: Depends: openssh-client (= 1:4.2p1-7ubuntu3.5) but 1:4.6p1-5build1 is to be installed
E: Broken packages

what to do with it?

---

### Post by spiderbatdad on 2009-05-16
7.10 has reached end-of-life. I dont know if the archives are still maintained. Do you have a graphical environment? If so use synaptic package manager to fix broken packages, and install openssh. If not try:
```
sudo apt-get install -f
sudo apt-get upate && sudo apt-get upgrade
sudo apt-get install openssh-client openssh-server
```

---

### Post by taimur on 2009-05-16
i try it but still same error is coming

---

### Post by albinootje on 2009-05-16
> **taimur said:**
>  i want to install openssh-server in ubuntu


Ubuntu 7.10 has had its "end of life" already.
Did you add different lines in your /etc/apt/sources.list ?
See here : [http://old-releases.ubuntu.com/releases/7.10/](http://old-releases.ubuntu.com/releases/7.10/) 

... AND also read that warning in red color !!!

You better upgrade right away to 8.04/Hardy, which is a Long Term Support release.

---

