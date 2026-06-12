---
title: "Can't get Cisco VPN Client to Build"
date: 2006-07-29
forum: Desktop Environments
---

### Post by gandalf2041 on 2006-07-29
I'm trying to install the Cisco VPN client so that I can connect to the company network. I installed the kernel headers via Synaptic and saw that it put the sources in /usr/include/linux (as far as I can tell...I'm new to Debian from Fedora).  At any rate, I had an .rpm for the client which I converted to .deb via alien. The converted package installed fine but, when I tried to run the install script, it doesn't seem to find the headers. Here's the output:
```
[12:10:02]-rand:~/vpnclient(0)>> sudo ./vpn_install
Cisco Systems VPN Client Version 4.7.00 (0640) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]n

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by default

Directory containing linux kernel source code []/usr/include/linux

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-26-386/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/usr/include/linux" will be used to build the module.

Is the above correct [y]

Making module
make -C /usr/include/linux SUBDIRS=/home/kupdegrove/vpnclient modules
make[1]: Entering directory `/usr/include/linux'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/usr/include/linux'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```
Any help would be greatly appreciated.

Thanks!

Gandalf2041
Ubuntu Dapper Drake 6.06

---

### Post by ltmon on 2006-07-29
Hi,

I find an easier way to connect to VPNs is to use NetworkManager.  There are prebuilt packages available for that, search the forums and wiki for it and you'll find it easily.

If you do go ahead with building the vpn client you need the linux source package installed.

```

sudo apt-get install linux-source

```

should install the source package (or look for it in Synaptic).

Then do the following to unpack it:
```

cd /usr/source
sudo tar xvjf linux-source-2.6.15.tar.bz2

```

Then you should be right.

L.

---

### Post by gandalf2041 on 2006-07-30
Thank you.  I d/l the source OK but I'm just having too much trouble getting this thing to compile.  I see from various posts that I'm not the only one. One of the threads suggested vpnc as a Cisco compatible client - no muss, no fuss.  I'll give that a try. :)

---

### Post by andnobodyslept on 2006-07-30
I was having problems with the cisco vpn client as well, and I found this patch, just follow the link and follow the instructions, it worked for me.
[http://www.victortrac.com/cisco_vpn_patch]("http://www.victortrac.com/cisco_vpn_patch")
I also ended up useing vpnc because it was a bit easier to use, just remember to use sudo when starting it up.

---

### Post by gandalf2041 on 2006-07-30
vpnc is working great! Now if I can just get NetworkManager to work, I should be good to go.

---

