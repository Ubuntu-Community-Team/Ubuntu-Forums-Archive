---
title: "Replacement Palm pilot (Treo 600) won't sync"
date: 2005-07-22
forum: Desktop Environments
---

### Post by suelovell on 2005-07-22
All -

I am new to linux, my son recently got me onto Ubuntu.

 I have been able to sync my old Palm Pilot Treo 600 using j-Pilot. I had a problem with that Palm so I synced for a last time and got a warranty replacement Palm, another Treo 600. I want to put all my old data on to the new Treo.

Within j-Pilot, I go to File ->Restore Handheld and click OK. I press the hotsync button on my palm. The process exits with the following log:

pi_bind error: /dev/ttyUSB1 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished


I saw another post about using Evolution to sync, but I use a different mail client and do not have any data in Evolution.

Thanks in advance -
Sue Lovell

Edit -
I searched further at the Unofficial Ubuntu 5.04 Starter Guide. I did the following:
prompt# sudo gedit /etc/udev/rules.d/10-custom.rules

I entered into the newly created file the following:

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

Then I went to:

 System->Preferences->PalmOSdevices

and I followed instructions there.

Result: I got a new folder in my home directory called MyPilot, but I still cannot get the Treo600 Palm to sync with the computer.

Any help would be appreciated -
Sue Lovell

---

### Post by bergersau on 2006-03-20
I get the exact same error with my Palm Tungsten T.

pi_bind error: /dev/ttyUSB1 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

](*,) 
Anyone got a solution?

---

