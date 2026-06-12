---
title: "Installing Parallels Desktop on Ubuntu 6.10"
date: 2006-10-28
forum: Desktop Environments
---

### Post by fps on 2006-10-28
Hi

Got the .deb package from Parallels (v2.2). Installed the linux-headers package as well.

When running parallels-config I get:

frederic@phoenix:~$ sudo parallels-config 
Password:


[: 141: ==: unexpected operator
     Compiling Parallels Workstation 2.2 drivers...

Can not compile and/or link drivers. Read /usr/lib/parallels/doc/INSTALL
and follow instructions specified in this document.

Compilation log is available at /usr/lib/parallels/comp.log.14314.error



frederic@phoenix:~$ cat /usr/lib/parallels//comp.log.14314.error 
cd drivers && make clean && cd ../
make[1]: Entering directory `/usr/lib/parallels/drivers'
cd drv_main/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
cd common; rm -rf *.o .*.cmd .tmp_versions; cd ..
cd mm; rm -rf *.o .*.cmd .tmp_versions; cd ..
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
/bin/sh: [[: not found
make[2]: Leaving directory `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_net/linux'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_net/linux'
cd drv_virtualnic/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_virtualnic'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_virtualnic'
make[1]: Leaving directory `/usr/lib/parallels/drivers'
cd drivers && make all && cd ../
make[1]: Entering directory `/usr/lib/parallels/drivers'
cd drv_main/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
cd common; rm -rf *.o .*.cmd .tmp_versions; cd ..
cd mm; rm -rf *.o .*.cmd .tmp_versions; cd ..
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
/bin/sh: [[: not found
make[2]: Leaving directory `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_net/linux'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_net/linux'
cd drv_virtualnic/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_virtualnic'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_virtualnic'
cd drv_main/ && make && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/usr/lib/parallels/drivers/drv_main SRCROOT=/usr/lib/parallels/drivers/drv_main modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.17-10-386/build: No such file or directory. Stop.
make: Leaving an unknown directory
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
make[1]: *** [vmmain] Error 2
make[1]: Leaving directory `/usr/lib/parallels/drivers'
make: *** [build] Error 2

Thx for any help.

---

### Post by Morpsemia on 2006-10-29
It looks like you don't have all the packages installed. These threads will help, it helped me:
[http://forum.parallels.com/showthread.php?t=4707&highlight=ubuntu+6.10](http://forum.parallels.com/showthread.php?t=4707&highlight=ubuntu+6.10)

After you get everything installed, you'll need to edit some of the install scripts so that everything will work right in 6.10

---

### Post by Cal6171 on 2006-10-30
On 6.06 I found that when the Parallels software said to install the kernel headers they really meant the kernel sources.  

sudo apt-cache search linux-source

will get you the correct package to install.  


It will be linux-source-(kernel version)

It is likely the same for 6.10.

---

### Post by Alexander Heß on 2006-11-05
> [: 141: ==: unexpected operator

Looks like the usual problem with the used /bin/sh which changed from Dapper to Edgy.

Open up the following files in an editor using **sudo -e**.

[LIST]
[*]/usr/lib/parallels/autostart/drivers_start
[*]/usr/lib/parallels/autostart/drivers_stop
[*]/usr/bin/parallels-config
[/LIST]

Change the first line from
```
#!/bin/sh
```
to
```
#!/bin/bash
```

Then open up the parallels init-script (**/usr/lib/parallels/autostart/parallels**).
```
sudo -e /usr/lib/parallels/autostart/parallels
```

Change lines 19 and 22 from
```
/bin/sh ...
```
to
```
/bin/bash ...
```

The drivers should now compile without any problems, and the virtual network-interface should load now during boot.

And while you're at it, open up the parallels start-script (**/usr/bin/parallels**).
```
sudo -e /usr/bin/parallels
```

Add **XLIB_SKIP_ARGB_VISUALS=1** to the run-Variable.

It should look like this afterwards:
```
run="XLIB_SKIP_ARGB_VISUALS=1 /usr/lib/parallels/parallels-linux $@"
```

This will fix any problems (green window borders, semi-transparent window and stuff) that are caused by AIGLX which is enabled by default in Edgy.

If you don't have any of these mentioned problems, you can skip the last part.

Thanks for listening. ;)

---

### Post by fontnest on 2006-11-05
I just went through this and found this answer from the Parallels user forums.  I tried and the install worked great.  First, though, follow the earlier post for the 'apt-get' for gccc, libc, etc.  Then do this:

It's the transition from bash to dash. Open up the parallels-config script and change the first line from #!/bin/sh to #!/bin/bash. You'll need to do this for a couple more I recall, like some networking scripts
instead, you may solve this problem once and for all. first find out which shell is default
Code:

ls -la /bin/sh

if it links to dash you're in trouble. if it links to bash your ok. amend it with
Code:

sudo ln -sf /bin/bash /bin/sh

For more info, look at this bug filing. The right thing to do would be to change all scripts that are broken (like show in this thread) but if you just want an easy fix for all third party scripts...

Worked for me, although I just stopped after the install and config and haven't gotten to creating a vm yet.

Fontnest

---

