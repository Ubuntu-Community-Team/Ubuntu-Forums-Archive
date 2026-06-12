---
title: "Enabling awake from suspend by keyboard"
date: 2011-03-17
forum: Desktop Environments
---

### Post by tomster2300 on 2011-03-17
Hey all, 

I am trying to get my Ubuntu 10.10 desktop to awake from suspend by either mouse or keyboard.  Right now only the power button brings it back to a state where I can push a button / wiggle the mouse and get the log in box. 

I know the keyboard is plugged into the USBE device, because it awakes via keyboard after I do 

echo "USBE" > /proc/acpi/wakeup

and then try suspending. I hit the keyboard enter key and I get the login box. 

I'm trying to make all of my usb ports to respond at startup for wake, but I'm having trouble enabling all of them at startup. Here is what I've done so far:

1) sudo visudo
2) Underneath 

root    ALL=(ALL) ALL

I added 

Cmnd_Alias BROADBAND=/home/(my_username)/scripts/.suspend
(my_username) ALL=NOPASSWD: BROADBAND

(I know this is setting an alias, but I found it on the forums and wasn't sure how to continue dissecting it to not make the alias). 

3) Added my script to the startup applications list so that it would run on startup.  

My script is...

#!/bin/bash


echo "USB0" > /proc/acpi/wakeup
echo "USB1" > /proc/acpi/wakeup
echo "USB2" > /proc/acpi/wakeup
echo "USB3" > /proc/acpi/wakeup
echo "USB4" > /proc/acpi/wakeup
echo "USB5" > /proc/acpi/wakeup
echo "USBE" > /proc/acpi/wakeup
echo "USE2" > /proc/acpi/wakeup




When I do 

sudo /home/(my_username)/scripts/.suspend 

and then check the ports via 

cat /proc/acpi/wakeup

USB ports 0-5 are enabled, while the remaining two, USBE and USE2, remain disabled.  The sudo command does NOT ask for my root password, which means that my changes in sudoers.tmp have to be working to some extent.  

Does anyone know what I'm doing wrong / what else I need to do?  Any help would be greatly appreciated.  Thanks!

---

