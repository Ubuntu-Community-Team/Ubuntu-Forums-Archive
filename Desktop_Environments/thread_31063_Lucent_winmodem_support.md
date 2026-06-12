---
title: "Lucent winmodem support"
date: 2005-05-01
forum: Desktop Environments
---

### Post by Ptero-4 on 2005-05-01
Hi. My sister got herself a HP Pavilion 734n desktop PC. It's got a Lucent WinModem and I wanted to know. Is there any package that contains the modem drivers for that modem? and if there are How can I do to get them (We use dialup)? Is it posible to hook together my OSX Panther box to my sisters PC?

Thanks

---

### Post by Nob on 2005-05-01
install kernel restricted modules, and kernel headers
download
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7.tar.bz2](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7.tar.bz2)
and follow the readme file ;)

---

### Post by nad on 2005-05-01
This may be a little complicated and your modem might not be supported, but you can try the linux-restricted-modules package for your specific running kernel, uname -r . There is support for some soft modems by the ltmodem driver.

From windows, go to packages.ubuntu.com and search for linux-restricted-modules. Download the package for your running kernel (2.6.10-5-386 maybe) to an easy place to find, say c:\ . Now start up ubuntu, mount your windows partition and copy that deb file to your home directory. Issue the command: sudo dpkg -i path_name/full _name_of_package . This should install it as I believe that the default ubuntu install includes the modest dependencies. If the package is installed without errors, issue the command: sudo modprobe ltmodem . The module will install if your modem is supported by the driver.

Search these forums for issues and instructions regarding winmodems, soft modems, driver install, etc if you continue to have problems and post back for additional help.

---

### Post by Nob on 2005-05-01
[QUOTE=nad]This may be a little complicated and your modem might not be supported, but you can try the linux-restricted-modules package for your specific running kernel, uname -r . There is support for some soft modems by the ltmodem driver.

From windows, go to packages.ubuntu.com and search for linux-restricted-modules. Download the package for your running kernel (2.6.10-5-386 maybe) to an easy place to find, say c:\ . Now start up ubuntu, mount your windows partition and copy that deb file to your home directory. Issue the command: sudo dpkg -i path_name/full _name_of_package . This should install it as I believe that the default ubuntu install includes the modest dependencies. If the package is installed without errors, issue the command: sudo modprobe ltmodem . The module will install if your modem is supported by the driver.

Search these forums for issues and instructions regarding winmodems, soft modems, driver install, etc if you continue to have problems and post back for additional help.[/QUOTE]
 it wont work.. i tried... 
alk7 version is required to work properlly,,,

---

### Post by nad on 2005-05-01
Sorry you had to go through that, but, the alternative is finding, compiling and installing the correct driver. The procedure is described in several threads in these forums and requires additional kernel packages, some of which are on your cd. It looks like post#2 has your driver at least.

By the way, connecting to the mac box will be easy by comparison.

---

### Post by Nob on 2005-05-02
[QUOTE=nad]Sorry you had to go through that, but, the alternative is finding, compiling and installing the correct driver. The procedure is described in several threads in these forums and requires additional kernel packages, some of which are on your cd. It looks like post#2 has your driver at least.

By the way, connecting to the mac box will be easy by comparison.[/QUOTE]
 well i posted the linke to correct drivers ;)

---

### Post by nad on 2005-05-02
Looking through several posts regarding the linuxant drivers, compiling them is not for the newbie. There are several issues that need to be forced in order to do so.

I agree with  the consensus that purchasing a new hardware modem for $30-40 is certainly the easiest and most sure solution, especially since the free drivers are limited to 14400 baud.

---

### Post by Ptero-4 on 2005-05-04
[QUOTE=nad]Looking through several posts regarding the linuxant drivers, compiling them is not for the newbie. There are several issues that need to be forced in order to do so.

I agree with  the consensus that purchasing a new hardware modem for $30-40 is certainly the easiest and most sure solution, especially since the free drivers are limited to 14400 baud.[/QUOTE]
 Thanks. I think I'm better off hooking my sisters PC to my Mac. And for the linuxant drivers. I don't need them, The Mac is using Panther as it's only OS. The drivers I were lookin' for are the Lucent ones for the PC.

---

