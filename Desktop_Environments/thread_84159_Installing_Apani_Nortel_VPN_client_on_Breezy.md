---
title: "Installing Apani Nortel VPN client on Breezy"
date: 2005-10-30
forum: Desktop Environments
---

### Post by wakeboarder on 2005-10-30
I'm trying to install the Apani Nortel VPN client on Breezy.
[http://www.apani.com/vpn-clients/overview](http://www.apani.com/vpn-clients/overview)

This is probably supersimple but I'm new to Linux and I'm trying to setup an environment so I don't have to go back and dualboot with XP.

First of all they only have prebuilt packages for RH and Suse.
I've downloaded the RH package and tried to build it but maybe some kernel development packages are missing?

>>>
cd src && make all
make[1]: Entering directory `/opt/cvc_linux-rh-gcc3-3.3/src'
cd k2.6 && make
make[2]: Entering directory `/opt/cvc_linux-rh-gcc3-3.3/src/k2.6'
make -C /lib/modules/2.6.12-9-686/build SUBDIRS=/opt/cvc_linux-rh-gcc3-3.3/src/k2.6 modules
make: *** /lib/modules/2.6.12-9-686/build: No such file or directory.  Stop.
make: Entering an unknown directorymake: Leaving an unknown directorymake[2]: *** [kmod_build] Error 2
make[2]: Leaving directory `/opt/cvc_linux-rh-gcc3-3.3/src/k2.6'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/opt/cvc_linux-rh-gcc3-3.3/src'
make: *** [all] Error 2
<<<

Please help me find what I'm missing and where to find it?

The following is from the install docs
>>>
PACKAGES NEEDED PRIOR TO INSTALLATION OF VPN CLIENT

  1)  Development packages need to be installed prior to 
      installing the Apani Contivity VPN Client.  These 
      include the following RPM files (make, glibc and egcs) 
      in addition to any dependencies that are required.  
      These packages are usually already installed under 
      normal circumstances for Linux operating systems.

  2)  The kernel-headers-2.4.x package is needed if 
      installing on a system using the 2.4.x kernel.
      The kernel-headers-2.6.x package is needed if
      installing on a system using the 2.6.x kernel.
      
      If there is no such package, the kernel-source-2.4.x 
      package must be used.
      

  3)  The Contivity VPN Client is kernel dependent.  The package 
      contains source code that you will need to rebuild before 
      installing it on your host.  Make sure you have the kernel-headers 
      for your kernel version installed before you rebuild the package.  
      You can verify this by checking the UTS_RELEASE definition in
      the version*.h file in the /usr/src/linux/include/linux
      directory with the following command:

      # grep UTS_RELEASE /usr/src/linux/include/linux/version*.h
<<<

thanks,
Peter

---

