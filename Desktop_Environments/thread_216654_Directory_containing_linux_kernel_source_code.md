---
title: "Directory containing linux kernel source code???"
date: 2006-07-15
forum: Desktop Environments
---

### Post by hfranco on 2006-07-15
When executing the script for the Cisco VPN 4.6, one of the question is this:

```
In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by default

Directory containing linux kernel source code []
```

What directory will I find this?

---

### Post by vigleik on 2006-07-15
> **hfranco said:**
> 
What directory will I find this?

That should be /usr/src/linux, I think. But you have to install them first. Something like "sudo apt-get install linux-headers-xxx" where xxx is your kernel version. To find your kernel version, "uname -r".

Vigleik

---

### Post by art on 2006-07-15
You need to install them first. 
```
sudo apt-get install linux-headers-`uname -r`
```
and then they are gonna be in /usr/src

---

### Post by hfranco on 2006-07-16
Guys, thanks for your reply.  

I did what you told me. 

```
sudo apt-get install linux-headers-`uname -r`
```

I tried install again and this is the error that I get

```

root@franco-laptop:/root/vpnclient# ./vpn_install
Cisco Systems VPN Client Version 4.6.02 (0030) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]yes

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.15-25-386/build] /usr/src/linux-headers-2.6.15-25-386

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-25-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/usr/src/linux-headers-2.6.15-25-386" will be used to buil d the module.

Is the above correct [y]

Making module
make -C /usr/src/linux-headers-2.6.15-25-386 SUBDIRS=/root/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
  CC [M]  /root/vpnclient/linuxcniapi.o
/root/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/root/vpnclient/linuxcniapi.c:312: error: ‘struct sk_buff’ has no member named ‘stamp’
/root/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/root/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/root/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/root/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
root@franco-laptop:/root/vpnclient#

```

---

### Post by kaptainlange on 2006-07-16
I could be wrong here, but shouldn't he be pointing to the linux-src directories and not the header directories.

I think it's common practice to extract your linux-src archives in /usr/src then create a symbolic link called linux linking to the extraction directory.  That way you can just say, /usr/src/linux whenever something asks for your source directory.

I'm pretty sure the sources are added when you install the headers but just in case the command is:

```
sudo apt-get install linux-source
```

Now to extract the source assuming you're using kernel 2.6.15:

```
cd /usr/src
sudo tar -jxvf linux-source-2.6.15.tar.bz2
```

Then to create that symbolic link.

```
sudo ln -s /usr/src/linux-src-`uname -r` /usr/src/linux
```

Hope that helps.

---

### Post by viraptor on 2006-07-16
> **kaptainlange said:**
> I could be wrong here, but shouldn't he be pointing to the linux-src directories and not the header directories.

Headers are enough to compile a module (usualy).
They are in this case. It's just that cisco soft is not prepared for this version of kernel. In path selection they suggest linux-2.4.10 dir... It would work with 2.4.XX probably - but you'll have hard time with compiling it for 2.6.XX.

If you want to try hacking it, until it works -> sk_buff::stamp is called tstamp now probably. But I don't think it will work after minor changes only.

---

### Post by bonzodog on 2006-07-16
I would agree with that. This looks like an incompatability problem with the 2.6.xx series of kernels, that VPN client was written for the 2.4.xx series of kernels, and there have been some major changes since then to the kernel code. See if you can find a much more recent VPN client that will communicate with Cisco hardware.
You will need version number 4.6.03.190 (Linux) from what I can see on the site.

---

### Post by skeeterflea on 2007-04-30
Hey all, similar problem for me.

When I run  ```
sudo apt-get install linux-headers- `uname -r`
```

I get the following.
```

Reading package lists... Done
Building dependency tree... Done
Package linux-headers is not installed, so not removed
E: Couldn't find package 2.6.15-28-686
```


Any idea what I am doing wrong?
Thanks

---

### Post by jimccogg on 2007-05-29
Not sure if anybody still cares, but I found a site with a patch that seems to work for me:

[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/]("http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/")

---

### Post by hfranco on 2007-05-29
Thanks jim

---

