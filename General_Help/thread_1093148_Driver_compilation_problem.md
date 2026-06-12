---
title: "Driver compilation problem"
date: 2009-03-11
forum: General Help
---

### Post by Sinedbret on 2009-03-11
Hi,

I am not an Linux expert at all but I try to solve my problem by myself whenever possible.

I am facing something I can not solve by myself.

I am using Ubuntu 8.10 Desktop edition installed in a VM.
I have bought a serial server in order to share serial devices over the network (VMWare ESXi does not support physical serial ports).

The device I bought is a Quatech QSE-100 with 4 serial ports attached. This device is quite old and was initially supported under Linux (Fedora Core 4, Suse 9.1).
I have dowloaded the driver from their website. I have read the help file in order to compile the driver (this is my first attempt to compile). The compilation is supposed to create 4 additional virtual serial ports in /dev.

I have installed the following packages:
build-essential
linux-headers for my distribution

The help states the following:
".. In this distribution the module must be built against the currently running kernel's configured and built kernel tree. For Suse and Fedora it was found that these were provided with the distribution if the kernel source is selected to be installed as part of the initial installation and no other special configuring was necessary. If other methods are used to obtain a built kernel tree, search for  documention for building external modules for the linux  2.6 kernel ..."

".. Run the "startup" script present in the "sprd_scripts" by executing the command "./startup at the command prompt. This will do the neccessary configuration settings for the installation of serial port redirector driver modules. NOTE: You will get several warnings due to functions only used between the installed modules not exported by the kernel.  Ignore these, you should not get any errors. .."

When I try to execute this I got errors (I attached the output of the make command) stating "unknown field ‘tiocmset’ specified in initializer" and other similar errors.
I really don't know what this means.

I would really appreciate if someone could help me with this.

I have attached in a zip file, the make output as well as the full driver source file.

Thank you again

Sined

---

