---
title: "Installing KDE header files for KDevelop"
date: 2009-01-12
forum: Desktop Environments
---

### Post by Ianprime0509 on 2009-01-12
Okay, so I'm developing with KDevelop, and in order to Build and Run, I need the KDE Header files. When I try to install them, this is what happens:

ian@ian-laptop:~$ sudo apt-get install kdelibs4-dev
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
  kdelibs4-dev: Depends: libpcre3-dev but it is not going to be installed
E: Broken packages
ian@ian-laptop:~$ sudo apt-get install libpcre3-dev
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
  libpcre3-dev: Depends: libpcre3 (= 7.6-2.1ubuntu1) but 7.8-2ubuntu1~intrepid1~ppa1 is to be installed
E: Broken packages
ian@ian-laptop:~$ sudo apt-get install libpcre3
Reading package lists... Done
Building dependency tree
Reading state information... Done
libpcre3 is already the newest version.
The following packages were automatically installed and are no longer required:
  gnome-system-monitor gdm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ian@ian-laptop:~$

It seems like I need to downgrade my libpcre3, but I don't know how to do that.

---

### Post by laluz on 2009-10-04
I have the same problem with Intrepid. In my case 
```
The following packages have unmet dependencies:
  libpcre3-dev: Depends: libpcre3 (= 7.6-2.1ubuntu1) but 7.8-2ubuntu1~intrepid1~ppa1 is to be installed
                Depends: libpcrecpp0 (= 7.6-2.1ubuntu1) but 7.8-2ubuntu1~intrepid1~ppa1 is to be installed
E: Broken packages

```

---

