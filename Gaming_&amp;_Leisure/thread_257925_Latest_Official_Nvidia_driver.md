---
title: "Latest Official Nvidia driver"
date: 2006-09-15
forum: Gaming &amp; Leisure
---

### Post by jdunn on 2006-09-15
When will 1.0.8774 be added to the repositories so I can update?

---

### Post by mtron on 2006-09-15
i'm using a script to install them, give it a try ;)

```
#!/bin/bash
# Licence GPL
# Written by Tseliot, adopted by mtron
# release: 0.0.3
# Nvidia Driver Version 8774
# For ubuntu 6.06 32 bit ONLY!!!

function installer {
echo -n "Do you want to install or uninstall the Nvidia driver 8774? (Type "i" to install or "u" to uninstall) (or press CTRL+C to exit)"
read inst
if [ "$inst" = "i" ]
then	

 wget ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/NVIDIA-Linux-x86-1.0-you can start the xserver now-pkg1.run;

#	sudo apt-get --assume-yes --force-yes --purge remove linux-restricted-modules-`uname -r` linux-restricted-modules-common nvidia-glx nvidia-kernel-common;
	sudo rm /etc/init.d/nvidia-*;

	sudo apt-get --assume-yes install linux-headers-`uname -r` xorg-dev build-essential gcc;

 	sh NVIDIA-Linux-x86-1.0-8774-pkg1.run --extract-only;
	cd NVIDIA-Linux-x86-1.0-8774-pkg1;

	sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_`date +%Y%m%d%H%M`;

	if [ -f /usr/lib/xorg/modules/extensions/libglx.so ]
	then sudo cp /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/xorg/modules/extensions/libglx.so.backup
	fi;

	sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`;



	choice="nada";
	while [ "$choice" = "nada" ]; do
	    echo -n "Do you want your xorg.conf to be automatically configured? (y/n) \ "No" is the default answer";
	    read choice;
	    if [ "$choice" = "y" ]
	    then sudo /usr/bin/nvidia-xconfig
	    elif [ "$choice" = "" ]
	    then echo "set the Driver to nvidia in xorg.conf"
	    elif [ "$choice" = "n" ]
	    then echo "set the Driver to nvidia in xorg.conf"
	    elif [ "$choice" = "no" ]
	    then echo "set the Driver to nvidia in xorg.conf"
	    else choice="nada"
	    fi;
	done;

	sudo modprobe nvidia;

	echo -n "Start the Xserver? (y/n) \ "Yes" is the default answer";
	read server;
	if [ "$server" = "y" ]
	then sudo /etc/init.d/gdm start
	elif [ "$server" = "" ]
	then sudo /etc/init.d/gdm start
	elif [ "$server" = "n" ]
	then echo "you can start the xserver now"
	elif [ "$server" = "no" ]
	then echo "you can start the xserver now"
	fi;

elif [ "$inst" = "u" ]
then 	sudo apt-get --assume-yes --force-yes --purge remove linux-restricted-modules-`uname -r` linux-restricted-modules-common nvidia-glx nvidia-settings nvidia-kernel-common;
	
	cd NVIDIA-Linux-x86-1.0-8774-pkg1;
	sudo ./nvidia-installer --uninstall;
	
	sudo rm /etc/init.d/nvidia-*;
	sudo rm /usr/lib/xorg/lib/libX*;
	sudo rm /usr/lib/xorg/modules/libX*;

	sudo rm /usr/lib/xorg/lib/modules/drivers/nvidia_drv.*;
	sudo rm /usr/lib/xorg/modules/drivers/nvidia_drv.*;

	sudo rm /usr/lib/xorg/lib/modules/extensions/libglx.so*;
	sudo rm /usr/lib/xorg/modules/extensions/libglx.so;
	sudo rm /usr/lib/xorg/modules/extensions/libglx.so.1.0.*;
	if [ -f /usr/lib/xorg/modules/extensions/libglx.so.backup ]
	then sudo cp /usr/lib/xorg/modules/extensions/libglx.so.backup /usr/lib/xorg/modules/extensions/libglx.so;
	fi
else echo 'You should type either "i" or "u" ! (or press CTRL+C to exit)'; installer
fi
}

#set -x
#set -v
sudo /etc/init.d/gdm stop
installer

```

---

### Post by frodon on 2006-09-15
Or just use the new tseliot's repository and use synaptic :cool: :
[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

---

