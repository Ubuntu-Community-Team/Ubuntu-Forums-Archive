---
title: "Can't reinstall Unity, Help???"
date: 2011-08-12
forum: Desktop Environments
---

### Post by mclizardman on 2011-08-12
Hello, I decided that I wanted to use the desktop cube in Ubuntu Classic (Gnome), and apparently when I installed the older version of Compiz Fusion to run on Gnome it uninstalled Unity. I now want to use unity, but when i try the unity --reset code, it says that that Unity is not installed, and to install it by using 
sudo apt-get install unity
I try that, but It says that some packages were not installed properly:
```
jake@jake's pc:~$ sudo apt-get install unity
sudo: unable to resolve host jake's pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: compiz-core-abiversion-20110322
         Depends: compiz-plugins-main but it is not going to be installed
E: Broken packages

```

Can anyone help? Thanks!

---

### Post by mclizardman on 2011-08-12
> **mclizardman said:**
> Hello, I decided that I wanted to use the desktop cube in Ubuntu Classic (Gnome), and apparently when I installed the older version of Compiz Fusion to run on Gnome it uninstalled Unity. I now want to use unity, but when i try the unity --reset code, it says that that Unity is not installed, and to install it by using 
sudo apt-get install unity
I try that, but It says that some packages were not installed properly:
```
jake@jake's pc:~$ sudo apt-get install unity
sudo: unable to resolve host jake's pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: compiz-core-abiversion-20110322
         Depends: compiz-plugins-main but it is not going to be installed
E: Broken packages

```Can anyone help? Thanks!

Solved the problem, disregard.

---

