---
title: "Problems compiling Q965 chipset drivers"
date: 2006-10-17
forum: Desktop Environments
---

### Post by j0217995 on 2006-10-17
I hope this is in the right forum, but I'm having problems compiling the drivers for the Intel Chipset Q965 which is w/ the Intel Core Duo.  I need to build the driver against the 2.6.15.1 kernel for a project at work.  I'm using an install of Xubuntu (dapper) w/ gcc and as far as I know everything installed.
I have downloaded the 2.6.15.1 kernel from Kernel.org, and built the modules against the .config file I needed to use.
Now I need to build the driver, so I type make -C [INDENT]/home/j0217995/linux-2.6.15.1 SUBDIRS=$PWD modules and receive:
Entering directory /home/j0217995/linux-2.6.15.1
Building modules
MODPOST
make leaving directory /home/j0217995/linux-2.6.15.1

[/INDENT]

Any help?

---

