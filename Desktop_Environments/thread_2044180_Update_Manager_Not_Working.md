---
title: "Update Manager Not Working"
date: 2012-08-18
forum: Desktop Environments
---

### Post by ron177 on 2012-08-18
An unusual situation has happened to my computer.  There seems to be a bug with the "update-manger" package. When I click  on the "Software Up to Date" botton, I get the following error message:


 <<Could not initialize the package information
 An unresolvable problem occurred while initializing the package information.
 Please report this bug against the 'update-manager' package and include the following error message:
 'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'>>
 

[see also the attached photo]
 

Here's also an additional problem:
 

When I turn on my computer, I have an error sign on my upper screen  desktop toolbar (see the second attached photo). When I click on the red  error sign, I get the following error message:
 

<<An error occurred. Please run Package Manger from the right  click menu or apt-get in a terminal to see what is wrong.>>
 

I think these two problems are indeed one. If someone can help me with it, I would greatly appreciate that.
 

R

---

### Post by darkapec on 2012-08-18
try 

```
sudo apt-get clean all
sudo apt-get update
```

then try to open package manager again

---

### Post by darkapec on 2012-08-18
if that does not work please post contents of 

/etc/apt/sources.list

---

