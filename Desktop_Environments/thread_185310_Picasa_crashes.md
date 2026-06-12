---
title: "Picasa crashes"
date: 2006-05-31
forum: Desktop Environments
---

### Post by HJB on 2006-05-31
HI all. Last night I enjoyed picasa both in Gnome and Xfce. I played with it the whole night and today (after a few updates via synaptic for Dapper) it crashes. Both in Xfce and Gnome????

Please help. I don't think the problem is only Xfce because Xfce welcomes me every now and then with a login screen which I assume happens after a screensaver crash??
Where should I look for logs to find out whats happening here?

Bye
H

---

### Post by Travisty on 2006-06-01
HJB,

I'm not sure what log to look in. I checked the syslog and did not see that picasa was logged there. have you tried launching Picasa via the command line? Does it give you any errors there?

---

### Post by wylie348 on 2006-06-01
i just upgraded yesterday and no issues with picasa under dapper - although I have not upgraded with anything from the 'official release' tonight.

This on inspiron 8600 nvidia.

---

### Post by coolclassic on 2006-06-01
[QUOTE=wylie348]i just upgraded yesterday and no issues with picasa under dapper - although I have not upgraded with anything from the 'official release' tonight.

This on inspiron 8600 nvidia.[/QUOTE]

If you just upgraded you will have to reinstall nvidia drivers. Picasa needs direct rendering which you will find has now been dissabled.

You can check with this command:

glxinfo | grep direct

---

### Post by HJB on 2006-06-01
coolclassic, that command is deadly. It crached the system same way as picaso (or screensaver).
Im gonna do a reinstall of nividia now. Im using 8178 with patch.
Hopes it goes well...

---

### Post by PriceChild on 2006-06-01
Seems like i don't need direct rendering... picasa still works, and that command didn't crash my system.

((btw. using xgl/compiz))

---

### Post by PriceChild on 2006-06-01
Whoops double post sorry

---

### Post by HJB on 2006-06-01
It worked !!!!
Great now its only firefox and samba which give probes but Ill start different threads.
If this might help someone I compiled this script from a few different [sources:]("http://www.ubuntuforums.org/showthread.php?t=52924")

> #!/bin/bash
# ver 1.0

# current version
version=8762
cd ~/NVIDIA
sudo /etc/init.d/gdm stop

if [ "$1" = "-new" ]; then
	echo "Running new script for new version...  "$version
	wget -c http://download.nvidia.com/XFree86/Linux-x86/1.0-$version/NVIDIA-Linux-x86-1.0-$version-pkg1.run
	sudo apt-get install build-essential gcc linux-headers-`uname -r`
	sudo apt-get --purge remove linux-restricted-modules-`uname -r` linux-restricted-modules-common nvidia-glx nvidia-settings nvidia-kernel-common
	sudo rm /etc/init.d/nvidia-*
fi

sh NVIDIA-Linux-x86-1.0-$version-pkg1.run --extract-only
cd NVIDIA-Linux-x86-1.0-$version-pkg1
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_1_$version
#patch -p0 < ../NVIDIA_kernel-1.0-8178-U012206.diff.txt
sudo ./nvidia-installer -n --x-prefix=/usr/lib/xorg/
sudo cp /usr/lib/xorg/lib/libX* /usr/lib/xorg/modules/
sudo cp /usr/lib/xorg/lib/modules/drivers/* /usr/lib/xorg/modules/drivers/
sudo cp /usr/lib/xorg/lib/modules/extensions/* /usr/lib/xorg/modules/extensions/
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_2_$version
sudo rm -r N*$version*pkg1
sudo /etc/init.d/gdm start
exit



Thank you all!
Bye
H

---

