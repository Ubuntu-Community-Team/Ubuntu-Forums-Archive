---
title: "Nvidia Gforce8600GT/Beryl"
date: 2007-09-17
forum: Desktop Environments
---

### Post by polemical on 2007-09-17
Well first of all I just want to say that I`m a total newbie when it comes to linux, so hopefully there are some of you who can work with that :P

Anyhow, I got the Nvidia Gforce 8600 GT graphic card, witch alot of you got problems with it seemes, well I got the api mismatch thingie during installation of the drivers(this didn't happen when running x64) and tried the 27 step tutorial:

First I did atp-get remove nvidia*

Only 27 steps:)
1)Install packages xserver-xorg-dev,pkg-config,libc6-dev.
You an find them at packages.ubuntu.com.
2)Press ctrl+alt+F2.
3)sudo nano /etc/init.d gdm stop
4)cd /there/your/driver/location
5)sudo sh NVIDIA-100.14...-xxx.run --ui=none
(without GUI menu)
To the question with nvidia-xconfig answer "Yes".
6)sudo nano /etc/default/linux-restricted-modules-common
Edit line
DISABLED_MODULES="nv nvidia_new"
7)sudo cp /lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia.ko /lib/modules/2.6.20-15-generic/volatile/
8)sudo modprobe nvidia
9)/sbin/ldconfig
10)/sbin/depmod -aq
11)reboot
12)step 7
13)cd /lib/modules/2.6.20-15-generic/volatile/
13)sudo insmod ./nvidia,ko
14)sudo modprobe nvidia
15)step 9
16)step 10
17)sudo /etc/init.d/gdm start
18)reboot
19)cd /lib/modules/2.6.20-15-generic/kernel/drivers/video/
20)sudo cp nvidia.ko nvidia_new.ko
21)sudo insmod ./nvidia.ko
22)step 9
23)step 10
24)ctrl+alt+F7
25)sudo nvidia-xconfig
26)reboot

But I stopped at step 7. because that file didn't exist, the closest I got was  /lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia/nvidiafb.ko, but I was uncertain this was the same thing so I stopped here. And just tried to start up gdm again(after removing the restricted drivers and installing the driver I got from nvidia) and it seemed to work.

But then, when I downloaded Beryl & Emerald and tried to do a beryl --replace I got this:

beryl: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Reloading options
beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl: Plugin 'dbus':initDisplay failed
beryl: Couldn't activate plugin 'dbus'
Couldn't initialise dbus. This should not happen!

Hopefully there are those of you willing and capable of helping :)

Ty, Loke Wilhelmsen

---

### Post by reset3x on 2007-09-22
Envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)... Be sure to use Envy to uninstall your nVidia drivers before installing them again....  Worked like magic for me...

Good luck!!

---

