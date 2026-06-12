---
title: "VMWare not working."
date: 2006-08-26
forum: Desktop Environments
---

### Post by ebeyer on 2006-08-26
I have a celeron-based machine with 6.06 ubuntu running.

I have been trying to get VMWare player to work with virtual machines of Open SUSE 10.1 and Fedora core 5 I downloaded.  Using the VMWare player I installed using add/remove I get the error 'cannot find /dev/vmmon' and the whole player quits.

Then I tried a complete uninstall of the VMWare player and supporting kernels using Synaptic; then installing VMWare server using the tarball from the vmware web site.  But running the install script gives me an error saying that a previous version of VMWare is installed and it quits.  I get the same error trying to install the vmware player's tarball.

I have pretty much run out of ideas here.  Any new ones would be truly appreciated.

EB

---

### Post by ebeyer on 2006-08-26
Additional information:

I tried installing VMWare player straight from the terminal:

sudo apt-get install vmware-player

and I get the error:
Starting VMware services:
  Virtual machine monitor                                failed
  Virtual ethernet                                             failed
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vm-ware player
E: Sub-process /usr/bin/dpkg returned an error code (1)

I did run the vmware-config.pl, which looked at subnets and seemed to finish without errors. However, VMware still doesn't work.  In fact, now it doesn't even launch.

Help!

---

