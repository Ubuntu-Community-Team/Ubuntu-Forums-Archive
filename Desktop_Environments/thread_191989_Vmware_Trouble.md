---
title: "Vmware Trouble"
date: 2006-06-08
forum: Desktop Environments
---

### Post by g77s80 on 2006-06-08
I'm running vmware workstation on a windows machine at work and trying to get Dapper up and running on the vmware workstation.
When I try to inst all the vmware tools in Dapper it tells me that that Dapper's kernel does'nt support vmware 5.5 tools
does anyone have a sollution to this problem?
ThanX

---

### Post by MartinG on 2006-06-08
The vmware install script should offer to compile the necessary module for you ... mine does.

To enable it to do so you need to install the "build-essential" package and the kernel headers for your running, Dapper, kernel (all this in the Dapper installation you are trying to get to work).


```
sudo apt-get install build-essential linux-headers-`uname -r`
```(The `uname -r` bit detects and inserts the kernel version.)
Once these are installed, try the vmware script again.

---

