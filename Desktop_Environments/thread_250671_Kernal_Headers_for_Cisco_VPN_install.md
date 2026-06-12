---
title: "Kernal Headers for Cisco VPN install"
date: 2006-09-04
forum: Desktop Environments
---

### Post by eschreib on 2006-09-04
Hello, I tried KVpnc as a VPN client, to no avail, so I treid to install the Cisco "vpnclient-linux-4.7.00.0640-k9" client.
When I run the install from a root terminal, I get stuck when it asks me where the linux kernal source code is located:

Any ideas?

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by default

Directory containing linux kernel source code []

---

### Post by meng on 2006-09-04
Did you install vpnc? kvpnc is only a frontend for various clients which include vpnc, vpnc is a suggested package but is not a dependency. The important thing is to have vpnc, kvpnc is just the icing on the cake. I suspect you may have only installed kvpnc which would explain why it failed.

Installing and using vpnc, IMHO, is a much easier task than trying to install the Cisco VPN client. And it's easy to invoke vpnc from the command line, without needing a GUI frontend at all.

---

### Post by paultjeb on 2006-09-04
I managed to install the cisco-client with this manual: [http://www.popey.com/node/62](http://www.popey.com/node/62)

---

### Post by eschreib on 2006-09-05
Thanks. i downloaded vpnc-0.3.3, how do I compile (?) it so that KVpnc recognizes it?

thanks

---

### Post by eschreib on 2006-09-06
I'm sure I'm a moron, but it does not appear I have the 'make' command????

Is the above correct [y]

Making module
./driver_build.sh: line 50: make: command not found
Failed to make module "cisco_ipsec.ko".
root@eschreibman-laptop:/home/eschreibman/Desktop/vpnclient#

---

### Post by jacrider on 2006-09-08
The link to [http://www.popey.com/node/62](http://www.popey.com/node/62) worked perfectly for me.

I have made a connection that has been authenticated.

How do I open a terminal/viewer to get into the other network?  I tried several ways with little success.

Thanks!

---

### Post by Maxtorm on 2006-09-08
> **eschreib said:**
> I'm sure I'm a moron, but it does not appear I have the 'make' command????


You're most certainly not a moron.  Ubuntu's design assumes the user will be using aptitude instead of compiling from source, so I don't believe it includes make by default.  Use ```
sudo apt-get install make
``` to install it.

However, as other users have noted, vpnc is an easier method.  You can run it from the command line (as root), it prompts you for the target IP, group name, etc. and runs in the background once connected.  You can, of course, automate the process by creating vpnc profiles.  Then it's simply a matter of using ```
vpnc profile-name
``` to connect.

---

### Post by elpuerco on 2006-09-23
I am trying to install the cisco vpn as it is supplied by my employer for me to connect to their network.

I tried the steps on the poey.com site but get stuck when trying to run the patch.

I enter at the prompt from the directory where all the files are and get the following errors?

patch p0 < vpnclient-linux-4.7.patch.txt

missing header for unified diff at line 3 of patch
patch: **** Can't find file p0 : No such file or directory

anyone got any ideas?

Thnx

---

### Post by Maxtorm on 2006-09-23
> **elpuerco said:**
> 
patch p0 < vpnclient-linux-4.7.patch.txt

I think you need a "-" in front of "p0".  From the popey site:
```
patch -p0 < vpnclient-linux-4.7.patch.txt
```

---

### Post by elpuerco on 2006-09-23
Hi, thanks what a dope!!

However this is what I get....

vpnclient$ patch -p0 < vpnclient-linux-4.7.patch.txt
missing header for unified diff at line 3 of patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|-- linuxcniapi.c       2005-11-12 11:53:06.000000000 -0600
|+++ 2.6.14-vpnclient-linux-4.7.00.0640-linuxcniapi.c   2005-11-12 11:49:20.000000000 -0600
--------------------------
File to patch:

---

### Post by hajk on 2006-09-23
> **elpuerco said:**
> I am trying to install the cisco vpn as it is supplied by my employer for me to connect to their network.

I tried the steps on the poey.com site but get stuck when trying to run the patch.

I enter at the prompt from the directory where all the files are and get the following errors?

patch p0 < vpnclient-linux-4.7.patch.txt

missing header for unified diff at line 3 of patch
patch: **** Can't find file p0 : No such file or directory

anyone got any ideas?

Thnx

The vpnc package is a drop-in replacement for the Cisco VPN Client and, what's more, is available in one of the Ubuntu repositories (it could be universe or multiverse, so uncomment those in /etc/apt/sources.list if necessary). There is no need to download source code and compile this yourself, unless using the Ubuntu-supplied vpnc did not work... Vpnc works very well indeed, I use it myself from home to become an "inside" computer at my university. I take it that your employer has given you the required information: URL of VPN server, the password secret, your own ID and password -- you would also need these when using the Cisco client.

I'm making no apology about directing you to the vpnc package instead of helping you with compiling non-Ubuntu stuff...

---

### Post by Maxtorm on 2006-09-23
I must agree with hajk.  Why beat your head against a wall trying to get the patch to work when vpnc is a stable alternative.  Install it via Synaptic and it will create an example.conf under /etc/vpnc.  Copy this file to, e.g., myvpn.conf and then modify to suit your VPN credential requirements.  Then it's a simple as ```
vpnc myvpn
``` to connect.  No patching required.

---

### Post by elpuerco on 2006-09-23
lol, no apology required.  I too prefer the idea of installing the one for Kubuntu, however should I have problems vpnc I can guess work would have issues with it.

But I have justed installed vpnc but know little of it.

I have always used vpn with windows with problems.

I see in the uncompressed guff from work there is a sample.pcf file.  I cannot see anything re work though?

I am to beleive then that they should supply me with various settings?  When I installed the Windows equivalent it went through with no setting required on my part as it was preconfigured to connect to work, I therefore presumed the Linux one would have been the same.

---

### Post by hardhatamoeba on 2006-09-29
hi all this is what i get

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.15-27-386/build]
* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-27-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.15-27-386/build" will be used to build the module.

Is the above correct [y]

Making module
./driver_build.sh: line 50: make: command not found
Failed to make module "cisco_ipsec.ko".
jacques@ubuntu-laptop:~/cisco/vpnclient$



why is it failing to make the module?? any helo will be appreciated to thi Ubuntu newby

---

### Post by Maxtorm on 2006-09-29
> **hardhatamoeba said:**
> 
./driver_build.sh: line 50: make: command not found
Failed to make module "cisco_ipsec.ko".

```
sudo apt-get install make
```
See previous post on first page of this thread.

---

### Post by hardhatamoeba on 2006-09-30
thanks Max, i must have missed that yesterday

---

### Post by hardhatamoeba on 2006-09-30
i am still failing however>>>
i get this error:

jacques@ubuntu-laptop:~/cisco/vpnclient$ make
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/jacques/cisco/vpnclient modules
/usr/src/linux-headers-2.6.15-27-386/scripts/gcc-version.sh: line 11: gcc: command not found/usr/src/linux-headers-2.6.15-27-386/scripts/gcc-version.sh: line 12: gcc: command not foundmake[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /home/jacques/cisco/vpnclient/linuxcniapi.o
/bin/sh: gcc: command not found
make[2]: *** [/home/jacques/cisco/vpnclient/linuxcniapi.o] Error 127
make[1]: *** [_module_/home/jacques/cisco/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [default] Error 2


and this when i try install:

jacques@ubuntu-laptop:~/cisco/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.6.02 (0030) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.15-27-386/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-27-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.15-27-386/build" will be used to build th e module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/jacques/cisco/vpnclient m odules
/usr/src/linux-headers-2.6.15-27-386/scripts/gcc-version.sh: line 11: gcc: comma nd not found
/usr/src/linux-headers-2.6.15-27-386/scripts/gcc-version.sh: line 12: gcc: comma nd not found
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /home/jacques/cisco/vpnclient/linuxcniapi.o
/bin/sh: gcc: command not found
make[2]: *** [/home/jacques/cisco/vpnclient/linuxcniapi.o] Error 127
make[1]: *** [_module_/home/jacques/cisco/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


therefore i am still confused.](*,)

---

### Post by Maxtorm on 2006-09-30
Looks like you need gcc as well.  Similar to installing make:
```
sudo apt-get install gcc
```

---

### Post by hardhatamoeba on 2006-10-03
thanks again, i will give iot a try when i get in

---

### Post by x64Jimbo on 2006-11-16
The package you need is called build-essential. It's a meta-package that includes all the binaries that are necessary for compiling source on your machine. 
sudo aptitude install build-essential

---

### Post by BlackManda on 2006-12-06
Hi EveryBody,

I have problem to find the package "vpnclient-linux-4.7.patch.txt", the website victortrac is unresolvable by DNS.
Can someone share the package to me?

Please Help me ;-)

---

### Post by GrumpyBob on 2006-12-10
> **hajk said:**
> The vpnc package is a drop-in replacement for the Cisco VPN Client and, what's more, is available in one of the Ubuntu repositories (it could be universe or multiverse, so uncomment those in /etc/apt/sources.list if necessary). There is no need to download source code and compile this yourself, unless using the Ubuntu-supplied vpnc did not work... Vpnc works very well indeed, I use it myself from home to become an "inside" computer at my university. I take it that your employer has given you the required information: URL of VPN server, the password secret, your own ID and password -- you would also need these when using the Cisco client.

I'm making no apology about directing you to the vpnc package instead of helping you with compiling non-Ubuntu stuff...

I agree - I've just spent the weekend failing to get the Cisco client installed and connecting.  In the end I installed vpnc and kvpnc from the repos.  kvpnc is a neat front end that I found very useful as you can import Cisco client profiles - I had one available on my WinXP partition from a WinXP client installation.  Worked a treat for me and I wish I hadn't wasted all that time with the Cisco client.

Robert

---

