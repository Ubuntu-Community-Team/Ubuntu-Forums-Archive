---
title: "j-pilot does work!  I need help!"
date: 2007-04-15
forum: Desktop Environments
---

### Post by Magiczero on 2007-04-15
Hi

I have an old palm IIIXE and I have had J-Pilot installed and I can't figure out how to make my palm conect with J-Pilot 
It is uaing a serial conection to conect to the computer
How do I make J-Pilot work?

Thanks
(I am running Ubuntu 6.10)

---

### Post by Magiczero on 2007-04-15
when I ran a command I got this error:

> tanner@tanner-desktop:~$ jpilot-sync
****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

Error: connecting to serial port
tanner@tanner-desktop:~$ 









What does this mean?

Thanks

---

### Post by dougr on 2007-04-15
Is it a USB device?

If so, try changing the path to the device in jpilot as /dev/ttyUSB1

If you have something else connected via USB, you may need to make it /dev/USB2

There is also a log file that shows the activity of the USB ports.  I haven't used it in a while, so I forget where it is, although im sure someone else can help with that.  If typing USB1 or 2, does not work, all you need to do is check that log file and it will tell you what to put in there.

PS.  In the latest Kpilot, there is a wizard that will detect where the device is when you hit sync, and sets it up.  This was missing from the last version I had, and is a welcome improvement.

---

