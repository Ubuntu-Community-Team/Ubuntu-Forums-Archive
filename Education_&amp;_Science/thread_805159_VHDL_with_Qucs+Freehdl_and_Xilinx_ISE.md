---
title: "VHDL with Qucs+Freehdl and Xilinx ISE"
date: 2008-05-23
forum: Education &amp; Science
---

### Post by Jonas85 on 2008-05-23
Hello

I spent hours this week to find how to install to drivers for Xilinx ISE and I finally find how.

So, I decided to make a summary of how to do that.

My installation works with the usb programming cable, and I think that most of the steps will works for the parallel programming cable.

I did the installation under Ubuntu Hardy, kernel 2.6.24-16, and I used Xilinx ISE 10.1
By default, gcc 4.2.3 was used.

**Installation of freehdl and Qucs**

First of all, we need to install freehdl. The version available on Ubuntu didn't work with Qucs, so I downloaded the last version of freehdl (version 0.0.6) on [http://www.freehdl.seul.org/](http://www.freehdl.seul.org/). I wasn't able to compile freehdl with gcc-4.2, so I downloaded and compiled gcc-4.3.0 on [http://gcc.gnu.org/](http://gcc.gnu.org/) first.

Warning : the link /usr/bin/gcc was replaced by the new gcc; if you would like to have gcc 4.2 by default, you should correct that.

Once we have installed freehdl (or verilog instead), we can install Qucs. As for me, I also installed it from source.
In the help manual of Qucs, there is a simple howto to make a digital simulation with Qucs.
There is also a longer one in
[http://qucs.sourceforge.net/docs/digital.pdf](http://qucs.sourceforge.net/docs/digital.pdf).

We can use kwrite or kate for a VHDL editor because they have the syntaxic coloration of VHDL.

see [http://stefan.endrullis.de/en/vhdl_editors.html](http://stefan.endrullis.de/en/vhdl_editors.html)

**Installation of Xilinx ISE an the drivers**

I downloaded the last Xilinx ISE on the official website and I lanched the installation. Everything happened well, except that at the end of the installation, I get an error message telling me that it wasn't able to install the cable drivers. Xilinx ISE is support until now only under Red Hat and Suse.

Then we need to install manually the drivers, and now the things become more complicated.

There is 3 ways to install the drivers
The easiest way that seems to me to be also the best is to install the userspace cable driver. Unfortunately I didn't work to me. The light on the appliance that programs the FPGA was on like it should, but when I would send a programm to the FPGA, I got this error message :

```
ERROR : iMPACT - Windriver open error
```

According to me, I wasn't missing a lot of things to make it works.

I followed the instructions here : [https://wiki.kip.uni-heidelberg.de/KIPwiki/index.php/EDV:Xilinx-USB-Treiber](https://wiki.kip.uni-heidelberg.de/KIPwiki/index.php/EDV:Xilinx-USB-Treiber)

Une autre serait d'installer Xup et XC3Sprog (voir [http://gentoo-wiki.com/HOWTO_Xilinx](http://gentoo-wiki.com/HOWTO_Xilinx)), mais je ne l'ai pas essayée

The solution that worked for me was to install the windriver of Jungo and the driver xilinx

I read the instructions here [http://stefan.endrullis.de/en/xilinx_ise_7.1.html#installation_ise_edk](http://stefan.endrullis.de/en/xilinx_ise_7.1.html#installation_ise_edk), and also a little here [http://gentoo-wiki.com/HOWTO_Xilinx](http://gentoo-wiki.com/HOWTO_Xilinx), but everything didn't work without modifications.

So, here is how I did it :

First, we need to download the last windriver :
```
wget http://www.jungo.com/st/download/WD920LN.tgz
```
The problem is that the kernel 2.6.24 has changed the API of the scatterlist (see [http://lwn.net/Articles/256368](http://lwn.net/Articles/256368)). I don't know what that is, but I found that I had to change the lines containing "sgl[i].page" in the file linux_wrappers.c
Also the file wdreg contains 3 lines with "==" and I had to replace them by a simple "="
Here is the patch that does that :

[http://b.imagehost.org/download/0313/windriver-sglpage_2equals.patch](http://b.imagehost.org/download/0313/windriver-sglpage_2equals.patch)

Once the WD920LN.tgz file is uncompressed, exec the following lines:
```
cd WinDriver
patch -Np1 < ../windriver-sglpage_2equals.patch
cd redist
./configure
make
sudo make install
chown stefan:users /dev/windrvr6 (Replace stefan by your name)
chmod 660 /dev/windrvr6
```

Now, we are going to install the xilinx driver.
I tried to install the driver for the kernel 2.6 that is located here [ftp://ftp.xilinx.com/pub/utilities/M1_workstation/linuxdrivers.2.6.tar.gz](ftp://ftp.xilinx.com/pub/utilities/M1_workstation/linuxdrivers.2.6.tar.gz),
but I wasn't able to compile it

So, we are going to install the driver for the kernel 2.4 :
```
wget ftp://ftp.xilinx.com/pub/utilities/fpga/linuxdrivers.tar.gz
wget http://stefan.endrullis.de/downloads/fpga/linuxdrivers.patch
tar xzf linuxdrivers.tar.gz
cd linuxdrivers
patch -Np1 <../linuxdrivers.patch
```

To make the driver compile, I also had to make a second patch.
Here it is :
[http://b.imagehost.org/download/0064/linuxdrivers-autoconf_h_setmoduleowner.patch](http://b.imagehost.org/download/0064/linuxdrivers-autoconf_h_setmoduleowner.patch)
```
patch -Np1 < ../linuxdrivers-autoconf_h_setmoduleowner.patch
cd xpc4drvr
mv Makefile Makefile_old
```
Download the new Makefile : [http://b.imagehost.org/download/0334/Makefile](http://b.imagehost.org/download/0334/Makefile)
```
make
sudo insmod ./xpc4drv.ko
```

And if everything goes well:
```
sudo make install
```
Now the 2 drivers are installed, they should be loaded with :
```
modprobe xpc4drv
modprobe windrvr6
```

If you have this following error message :

```
FATAL: Module xpc4drv not found.
```

Do instead :
```
insmod /lib/modules/`uname -r`/kernel/drivers/misc/xpc4drv.ko

```
**Installation of the last firmware**

```
wget ftp://ftp.xilinx.com/pub/utilities/fpga/xusbdfwu-1025.zip
unzip xusbdfwu-1025.zip
sudo cp xusbdfwu.hex /usr/share
```
**Install of fxload: (maybe not necessarly)**
apt-get install fxload

**Configuration of Xilinx:**

```
sudo mv /chemindelise/bin/lin/xusbdfwu.hex /opt/xilinx/bin/lin/xusbdfwu.hex.old
sudo cp /usr/share/xusbdfwu.hex /opt/xilinx/bin/lin/
sudo bash /pathofise/bin/lin/setup_pcusb
```
Replace pathofise by the path of your folder ISE (for me it is : /opt/Xilinx/10.1/ISE)

If I lanch setup_pcusb with another shell thant the bash, the script stop with an error :
```
setup_usb: 205: Bad substitution
```
One thing that does the script setup_pcusb is to copy the file xusbdfwu.rules, that is in the same path than it, to the folder /etc/udev/rules.d. It will complain that it can't find this file in the udev rules folder, so it will copy it in the folder.

Here is a script that loads the drivers if they are not yet loaded, and that launch ISE with work directory ~/.xilinx

```
#!/bin/bash
 ############################
 #     ISE start script     #
 #                          #
 #    by Stefan Endrullis   #
 #                          #
 #    and modified after    #
 ############################

# Check if the modules are loaded, if not : it loads them
if [ ! -e /dev/windrvr6 ]; then

	sudo xilinx_modules

fi

 # Please adapt these values to your system configuration.
 XILINX_DIR=/opt/Xilinx/10.1/ISE/
 # less importantly
 XILINX_USER_DIR=~/.xilinx
 
 
 ### script begin ###
 
 # create XILINX_USER_DIR if nessessary and change dir
 if [ ! -d ${XILINX_USER_DIR} ]; then
 mkdir ${XILINX_USER_DIR}
 fi
 cd ${XILINX_USER_DIR}
 
 # load settings
 . ${XILINX_DIR}/settings32.sh
 
 # start xilinx ise
 ${XILINX_DIR}/bin/lin/ise
```

Of course, you should adapt this script to your installation by putting the path of your ISE directory.
In my computer, after each reboot, the file /dev/windrvr6 disapears, so if it isn't the case for you, replace the "if [ ! -e /dev/windrvr6 ]; then" by something like :

r=`lsmod | grep windrvr6`
if [ ${#r} -gt 0 ] ; then

And you would also need to change a little the script xilinx_modules

And there it is :

```
#!/bin/bash

modprobe windrvr6
modprobe xpc4drv

# Only useful if the file /dev/windrvr6 disapears after each reboot
major=`grep -w windrvr6 /proc/devices | cut -f1 -d" "`
mknod /dev/windrvr6 c $major 0
chown jonas.users /dev/windrvr6 (replace jonas by your name)
chmod 660 /dev/windrvr6
```

If you cannot use Xilinx correctly without being root, add this following udev rule in /etc/udev/rules.d/z25-xilinx.rules:

```
ACTION!="add", GOTO="xilinx_rules_end"
SUBSYSTEM!="usb_device", GOTO="xilinx_rules_end"

# xilinx xup cable
SYSFS{idVendor}=="03fd", SYSFS{idProduct}=="000d", MODE="664", GROUP="users"

LABEL="xilinx_rules_end"
```
Of course, you need to belong to the group "users"

Now, we reload the udev rules :
```
sudo udevcontrol reload_rules
```

That's all, unless I forgot to tell something, and everything should work now.
There is some more scripts that can be useful for you in the links I put.

---

### Post by 3SV on 2008-06-11
thank you for the effort. I also just installed ISE 10.1 with USB drivers and there is now a **much easier way**.

There seems to be now the option to not use a self compiled kernel module but just use libusb that runs in user space. although the documentation is not updated yet.
You can just install the ISE 10.1 webpack with "sudo ./install" and use the graphical installer. If you check that you want to install the usb drivers you get an error at the end of the installation, but that's not a problem, that is for the old usb method.
Once installed you can set the environment variabele XIL_IMPACT_USE_LIBUSB to 1 and start using the ISE enviroment with usb support. See that the libusb is installed on you're machine but that was the case by default for me.
More info about setting an environment variable on [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

By default there is no launcher for the program so you has to create that yourself.

QUICK installation guide
> 
- Install with graphical installer "sudo ./install"
- Launch with "XIL_IMPACT_USE_LIBUSB=1 /opt/Xilinx/10.1/ISE/bin/lin/ise" 

That's it:)


thanks to this [http://www.rmdir.de/~michael/xilinx/](http://www.rmdir.de/~michael/xilinx/) site for pointing me to this easy solution.

---

### Post by Jonas85 on 2008-06-13
Hello

Thanks for your answer. I installed the libusb driver and launched Xilinx with XIL_IMPACT_USE_LIBUSB=1 /opt/Xilinx/10.1/ISE/bin/lin/ise
and it works.

Jonas

---

### Post by balagosa on 2008-06-21
hi people.

How did you get Xilinx for Linux? A non-Trial Xilinx (not the one on the website).

---

### Post by flaggh on 2008-06-23
Download the Xilinx ISE WebPack from the xilinx website.  It is a fully functioning development environment.

---

### Post by RebounD11 on 2008-07-02
> **flaggh said:**
> Download the Xilinx ISE WebPack from the xilinx website.  It is a fully functioning development environment.

and it's free... and it got me off Windows on my work computer. Thanks all for the howto :D

---

### Post by ashijit007 on 2008-07-15
Thanks for the howto! The installation finished with the "could not install drivers" message as said above. Then i did 
export XIL_IMPACT_USE_LIBUSB=1 in my home dir in the terminal (was this correct?)

/opt/Xilinx/10.1/ISE/bin/lin/ise gives me nothing in the terminal.
With Alt-F2 it gives : 

The command "/opt/xilinx10.1/ISE/bin/lin/ise" failed to run:
Failed to execute child process "/opt/xilinx10.1/ISE/bin/lin/ise" (No such file or directory):confused:

Plz help!
(BTW, should i have started a new thread?)

---

### Post by flaggh on 2008-07-15
Make sure you are using capital letters where required:

```
/opt/Xilinx/10.1/ISE/bin/lin/ise
```

---

