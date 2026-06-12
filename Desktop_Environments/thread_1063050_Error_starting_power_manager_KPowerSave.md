---
title: "Error starting power manager KPowerSave"
date: 2009-02-07
forum: Desktop Environments
---

### Post by rkent on 2009-02-07
From time to time I get an error that causes my power manager to think the battery has been removed, and/or causes the wireless applet to stop detecting networks.  In fact the power thing always happens, and the wireless network problem usually accompanies it.

I was previously advised in this thread ([http://ubuntuforums.org/showthread.php?t=1033033](http://ubuntuforums.org/showthread.php?t=1033033)) to switch to Kpowersave from the power manager applet I had been using.  However, this does not fix the problem.  Today it happened and when I tried to start kpowersave, I got the following error messages:

user@host:~$ kpowersave --force-acpi-check
kpowersave: ERROR: Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
kpowersave: ERROR: Can't connect to D-Bus
kpowersave: ERROR: Can't connect to HAL
kpowersave: ERROR: Could not connect to D-Bus & HAL
kpowersave: ERROR: This machine does not support ACPI, APM, PMU, CPUFreq, Suspend2Disk nor Suspend2RAM. Close KPowersave now.
ERROR: Communication problem with kpowersave, it probably crashed.

This is the exact command I've used to start it before - successfully - so I know that D-Bus and HAL are usually there.  I restarted hald manually, and it didn't help.  

Hardware is a Lenovo T-60, running 8.04.1.

Any suggestions?  This seems to happen at random, without any connection to what I'm doing at the time, and it's getting frustrating.  Thanks.

---

