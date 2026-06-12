---
title: "Bash script not setting device permissions correctly"
date: 2009-05-14
forum: General Help
---

### Post by radiocognition on 2009-05-14
Hey Everyone:

I am setting up an astronomy camera on a system that runs Ubuntu Linux.  I have all of the drivers and firmware successfully compiled and installed.  The device management is handled through the udev daemon - so that every time the camera's usb cable is plugged into the machine, udev automatically runs a script to load the drivers.

My problem is with the script that udev executes to set the device up.  The script is supposed to simultaneously upload the drivers and change the permissions of the device so that any user can operate it.  Here is the script that I wrote.
```

#!/bin/bash                                                                                                      

# Name:     sbig_init_permission.sh                                                                              
# Version:  1.0                                                                                                  

# Author:   True Merrill (true.merrill@gatech.edu)                                                               
#     Copyright (C) 2009 True Merrill                                                                            
#     Georgia Institute of Technology                                                                            
#     Released under the terms of GPLv3 or later                                                                 

# Synopsis: Simple shell script to give SBIG ST-3200ME camera correct permissions                                

# History:                                                                                                       
# 2009-05-13   Initial release                                                                                   

DEVICE_NAME=$1
/sbin/fxload -I /lib/firmware/sbigfcam.hex -D $DEVICE_NAME -t fx2

BUS_NUMBER=$2
DEV_NUMBER=$[$3+1]
# Append on zeros to make strings the correct length                                                             
if [[ ${#BUS_NUMBER} == 1 ]]; then
   BUS_NUMBER="00"$BUS_NUMBER
elif [[ ${#BUS_NUMBER} == 2 ]]; then
   BUS_NUMBER="0"$BUS_NUMBER
fi
if [[ ${#DEV_NUMBER} == 1 ]]; then
   DEV_NUMBER="00"$DEV_NUMBER
elif [[ ${#DEV_NUMBER} == 2 ]]; then
   DEV_NUMBER="0"$DEV_NUMBER
fi

sudo /bin/chmod 666 /dev/bus/usb/$BUS_NUMBER/$DEV_NUMBER

```

Here is the relevant piece of the /etc/udev/rules.d/ file that runs the script:
```

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0d97", ATTR{idProduct}=="0003", \
RUN+="/usr/local/bin/sbig_init_permission.sh $env{DEVNAME} $attr{busnum} $attr{devnum}"
```

The script automatically runs when the device is plugged in (udev is working) and successfully loads the drivers using fxload.  The rest of the script takes the bus number and device number and uses it to change the permissions of the device.  The script correctly formats the chmod command (I saved the output to text while I was debugging) but for some reason the permissions are not changed! However, when I run the command on my own, the permissions are changed (I have to have root access to do this).

I need this to execute automatically without requiring root access.  I've tried everything I could - including changing the permissions on the script so that it always executes as root
```
chown root scriptname.sh
chmod 4755 scriptname.sh
```
with no success.  Any ideas?

---

### Post by radiocognition on 2009-05-14
Anyone?

---

