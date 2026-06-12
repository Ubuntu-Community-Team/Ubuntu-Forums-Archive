---
title: "Bose Companion 5 not working on Resume from Suspend"
date: 2011-10-20
forum: Desktop Environments
---

### Post by dwlima on 2011-10-20
After a resume from Suspend, my  Bose sound card is not detected. I have to manually unplug/plug it in  (and unmute it) for it work. Although it replicates the same behavior as  unbinding and binding 5-2, I cannot get the card to be recognized by  binding it after a resume. 

lsmod
Used by number goes from 2 to 0 after resume.

lsusb
Bus 005 Device 002: ID 05a7:1020 Bose Corp. 

port details:
**grep 1020 /sys/bus/usb/devices/*/idProduct**
/sys/bus/usb/devices/5-2/idProduct:1020

Check state of port  (disabled)
**cat /sys/bus/usb/devices/5-2/power/wakeup**
Bose has no wake-up file within "power" directory

dmesg
a whole bunch of "2:1:1: usb_set_interface failed"

Any ideas???

---

### Post by mgmiller on 2011-10-20
I think the trick here is to try to keep the USB port that the sound card is plugged into powered during sleep mode.  There is a package called acpitool that can help you do that.

```
sudo apt-get install acpitool
```Next, post the output of:
```
acpitool -w
```By running:
 ```
sudo acpitool -W # 
```(where #) is the line number of the device you want to keep powered, you can change the status of the USB ports to enabled, meaning they retain power when in sleep mode.

To make the change permanent if it works, add the command to /etc/rc.local

Here are 2 threads that discuss this possible solution for you:

[http://ubuntuforums.org/showthread.php?t=1529855](http://ubuntuforums.org/showthread.php?t=1529855)

[http://ubuntuforums.org/showthread.php?t=1446965](http://ubuntuforums.org/showthread.php?t=1446965)

---

### Post by dwlima on 2011-10-20
I have used "cat /proc/acpi/wakeup" to view the USB device status instead of "acpitool -w". 

I know the Bose is in USB6 since I plugged my bluetooth dongle into USB6 and toggled enabling each USB port until it awoke from suspend. It was USB6. I also made USB6 enabled where the Bose is plugged in by adding "echo USB6>/proc/acpi/wakeup" to /etc/rc.local so it is enabled on boot-up. 

After a re-boot, I can now see USB6 enabled all the time. However, on my second suspend the Bose sound card does not appear on the Sound Hardware.

I am wondering if it is a Bus power issue, maybe there is not enough power to keep the Bose sound card always active while resuming from suspend.

Any last ideas? tia.

---

### Post by mgmiller on 2011-10-20
The proc/acpi/wakeup is a little different.  That is used to keep the port open just to detect signal so you can restart with a USB keyboard or mouse.  I don't think it provides full power to the port.  

Try the acpitool as I suggested.  That should keep the port fully powered during suspend.  Also use the command I gave you to determine which line number to use.  It will be different then the USBport# you found with acpi.

---

### Post by dwlima on 2011-10-20
In the interest of completeness and "obedience", I had tried your suggestion. When I do as root "acpitool -W 9" where line 9 is USB6, I get the following message "Segmentation fault". I downloaded acpitool from apt-get install as well trying the one from the software center.

When I go to /proc/acpi which is what acpitool supposedly modifies, there is a file labeled "wakeup" line 9 is USB6 which shows "enabled".

So, I am not sure that acpitool is different than waking up the port. I need to figure out this Segmentation fault error to see if that makes a difference. A quick search did not reveal anything useful.

---

### Post by dwlima on 2011-10-20
Not sure why, but now I can execute the acpitool -W command and did so:

root@main-MS-7522:/proc/acpi# sudo acpitool -W 9
root@main-MS-7522:/proc/acpi# 
 
On the next suspend, my Bose sound card did not show up. 

Thanks anyway. Anyone else have any ideas?

---

