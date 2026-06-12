---
title: "Help w/ Ruby God and Linode"
date: 2009-04-06
forum: General Help
---

### Post by ericindc on 2009-04-06
I have a Ruby gem (god.rubyforge.org) that per the listed requirements needs either the cn (connector) module installed or compiled into the kernel.

> God currently only works on Linux (kernel 2.6.15+), BSD, and Darwin systems. No support for Windows is planned. Event based conditions on Linux systems require the cn (connector) kernel module loaded or compiled in to the kernel and god must be run as root.

From what I've found, this is compiled into the kernel ("zgrep CONNECTOR /proc/config.gz" --> CONFIG_CONNECTOR=y) but the Ruby gem does not actually work when the module is compiled into the kernel, as also confirmed by others who have experienced similar.

I'm not to savvy with Linux, especially when it comes to compiling kernels and the like.  That said, can someone get me started or in the right direction on how to solve this?

Any help is appreciated.  I am looking to have this done on a Linode server with 2.6.18.8-linode16.

Thanks

---

### Post by geraldm on 2009-04-06
The documentation shown has CONFIG_CONNECTOR=y which means that that
documentation wants the source compiled into the kernel.  
If a compiling into a module were to be desired the .config file would show
CONFIG_CONNECTOR=m
It should work, but if you use the module, you will have to have the module loaded by a command such as:
sudo modprobe cn

There is quite a bit of work left, as the module requires socket, bind, and 
net send, recv.  Perhaps google some information on the linode server.
There should be some easy access to more helpful information than I can provide.
The documentation in the kernel source is very sparse.

regards,
Gerald

---

### Post by ericindc on 2009-04-07
> **geraldm said:**
> The documentation shown has CONFIG_CONNECTOR=y which means that that
documentation wants the source compiled into the kernel.  
If a compiling into a module were to be desired the .config file would show
CONFIG_CONNECTOR=m
It should work, but if you use the module, you will have to have the module loaded by a command such as:
sudo modprobe cn

There is quite a bit of work left, as the module requires socket, bind, and 
net send, recv.  Perhaps google some information on the linode server.
There should be some easy access to more helpful information than I can provide.
The documentation in the kernel source is very sparse.

regards,
Gerald

The CONFIG_CONNECTOR=y is from our server, not from the documentation.  The documentation states that it should run with either the compiled version or installed moduled, but unfortunately the compiled version doesn't seem to work.

---

