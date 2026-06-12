---
title: "VirtualBox USB PROBLEMS"
date: 2010-11-15
forum: Desktop Environments
---

### Post by feng shui on 2010-11-15
Hi this is one post that i found in very old discussion about virtual box usb problems on detecting devices from the host, i did test all solutions found at this topic
[http://ubuntuforums.org/showthread.php?t=341740](http://ubuntuforums.org/showthread.php?t=341740)
so i need some help to fix my problem if possible.

"Hey guys, all of you have been very helpful, and i'm up and running on  XP and seeing my external HD.  I usually write myself short text files  with step that work for my installs, so i hope this helps other  people...

-Install XP or other OS

-Create a group called "usbfs" and add yourself to it.

-In terminal issue the following command:

    sudo gedit /etc/fstab

-In this file paste the following lines, and change the group ID according to the group ID that is shown for the group "usbfs".


# 1001 is the USB group ID
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0


-Save and close file.


-In terminal, issue the following command:

    VBoxManage list usbhost

-Use the output of this command to set up the filters for USB devices under VirtualBox.

-Reboot


*USB DEVICES HAVE TO BE UNMOUNTED BEFORE VIRTUAL MACHINE CAN RECOGNIZE THEM*


...I hope this helps.


UPDATE: I've noticed that if you don't unmount or eject the external  drive before booting the virtual machine, the virtual machine will take  precedence over it, and eject it from ubuntu.  So, when the virtual  machine is running i've had to just unplug the usb cord and plug it back  in, and the virtual machine picks it up."

After add such string "none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0" on the file /etc/fstab i restart and in the prelogin screen ubuntu say me "error when try to load /proc/bus/usb"  press S to skip or B to fix. Any help will be apreciate
thanks a lot

---

