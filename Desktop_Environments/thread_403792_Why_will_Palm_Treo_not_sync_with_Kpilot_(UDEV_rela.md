---
title: "Why will Palm Treo not sync with Kpilot (UDEV related?)?"
date: 2007-04-07
forum: Desktop Environments
---

### Post by jshute on 2007-04-07
After much reading on the forums and Googling, I can get my Palm Treo 700p to sync but it is a real hack.
I have to make sure Kpilot and the daemon are NOT running and then press the hotsync button. Then Kpilot is started.

I have a feeling it is UDEV related as the USB port numbers seem to shift around in the second case. The dev/pilot link seems to follow to the second connection.
It might be the case of the Kpilot daemon grabbing the ports too early?

Why can I not keep Kpilot and the daemon running and get this to work?

The Facts

Device: Palm Treo 700p
Cable connected directly to computer

Computer:
Kubuntu Edgy (fully up-to-date)
Linux blue 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

60-symlinks.rules
-------------------
#New Palm udev rules from mailing list
BUS=="usb", KERNEL=="ttyUSB[13579]", SYSFS{product}=="Palm Handheld*|Handspring *", NAME="ttyUSB%n", SYMLINK+="pilot", GROUP="dialout", MODE="0666"

The rule produces a symlink to the odd numbered ttyUSB? device with 666 rights. My user is part of the dialout group as well. This has been verified while the Treo is connected.

Kpilot config
---------------
pointed to /dev/pilot
speed 115200
no workarounds


Hotsync Works
1) Kpilot and the deamon are NOT started or running
2) Plug in Treo
3) Press Hotsync button or software button
4) Start kpilot from the menu
5) EVERYTHING WORKS

/dev/pilot is pointing to ttyUSB1 in the end.

----------------------------------------------------------------------------------------------------------------------------------
syslog
----------------------------------------------------------------------------------------------------------------------------------
-= Plug in cable to Treo =-
Apr  7 13:14:24 blue kernel: [17547614.264000] usb 1-6: new full speed USB device using ohci_hcd and address 79
Apr  7 13:14:24 blue kernel: [17547614.480000] usb 1-6: configuration #1 chosen from 1 choice
Apr  7 13:14:24 blue kernel: [17547614.484000] visor 1-6:1.0: Handspring Visor / Palm OS converter detected
Apr  7 13:14:24 blue kernel: [17547614.484000] usb 1-6: Handspring Visor / Palm OS converter now attached to ttyUSB0
Apr  7 13:14:24 blue kernel: [17547614.484000] usb 1-6: Handspring Visor / Palm OS converter now attached to ttyUSB1
-= Press hotsync =-
Apr  7 13:14:46 blue kernel: [17547636.892000] usb 1-6: USB disconnect, address 79
Apr  7 13:14:46 blue kernel: [17547636.892000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Apr  7 13:14:46 blue kernel: [17547636.892000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Apr  7 13:14:46 blue kernel: [17547636.892000] visor 1-6:1.0: device disconnected
Apr  7 13:14:47 blue kernel: [17547637.700000] usb 1-6: new full speed USB device using ohci_hcd and address 80
Apr  7 13:14:47 blue kernel: [17547637.908000] usb 1-6: configuration #1 chosen from 1 choice
Apr  7 13:14:47 blue kernel: [17547637.916000] visor 1-6:1.0: Handspring Visor / Palm OS converter detected
Apr  7 13:14:47 blue kernel: [17547637.916000] usb 1-6: Handspring Visor / Palm OS converter now attached to ttyUSB0
Apr  7 13:14:47 blue kernel: [17547637.916000] usb 1-6: Handspring Visor / Palm OS converter now attached to ttyUSB1
Apr  7 13:16:55 blue kernel: [17547765.916000] usb 1-6: USB disconnect, address 80
Apr  7 13:16:55 blue kernel: [17547765.916000] visor 1-6:1.0: device disconnected

---------------------------------------------------------------------------------------------------------------------------------
kpilot log
---------------------------------------------------------------------------------------------------------------------------------
Version: KPilot 4.6.0 (blivit)
Version: pilot-link 0.12.1
Version: KDE 3.5.4
Version: Qt 3.3.6

HotSync Log
13:14:51 Starting the KPilot daemon ...
13:14:51 Daemon status is `not running'
13:14:51 Next HotSync will be: Copy Handheld to PC. Please press the HotSync button.
13:14:52 Trying to open device /dev/pilot...
13:14:52 Device link ready.
13:14:57 Checking last PC...
13:14:57 KPilot 4.6.0 (blivit) HotSync starting...
13:14:57 Using encoding ISO 8859-15 on the handheld.
13:14:57 [Conduit knotes-conduit]
13:15:01 Modified one note in KNotes.
13:15:02 [Conduit vcal-conduit]
13:15:02 Using non-local time zone: America/Chicago
13:15:04 Syncing with file "/home/jshute/.kde/share/apps/korganizer/std.ics"
13:15:05 Copying records to PC ...
13:16:14 Cleaning up ...
13:16:20 [Conduit abbrowser_conduit]
13:16:34 [Conduit todo-conduit]
13:16:34 Using non-local time zone: America/Chicago
13:16:35 Syncing with file "/home/jshute/.kde/share/apps/korganizer/std.ics"
13:16:36 Copying records to PC ...
13:16:38 Cleaning up ...
13:16:40 [Conduit sysinfo_conduit]
13:16:46 Handheld system information written to the file /home/jshute/kpilot-syslog.html
13:16:46 End of HotSync
13:16:46 HotSync Completed.


Hotsync Does NOT Work
1) Kpilot and the deamon are started
2) Plug in Treo
3) Press Hotsync button or software button
4) Sync FAILS

/dev/pilot is pointing to ttyUSB3 in the end.

----------------------------------------------------------------------------------------------------------------------------------
syslog
----------------------------------------------------------------------------------------------------------------------------------
-= kpilot started =-
Apr  7 13:32:15 blue kernel: [17548685.296000] usb 1-6: new full speed USB device using ohci_hcd and address 82
Apr  7 13:32:15 blue kernel: [17548685.504000] usb 1-6: configuration #1 chosen from 1 choice
Apr  7 13:32:15 blue kernel: [17548685.512000] visor 1-6:1.0: Handspring Visor / Palm OS converter detected
Apr  7 13:32:15 blue kernel: [17548685.512000] usb 1-6: Handspring Visor / Palm OS converter now attached to ttyUSB0
Apr  7 13:32:15 blue kernel: [17548685.512000] usb 1-6: Handspring Visor / Palm OS converter now attached to ttyUSB1
-= Press hotsync button =-
Apr  7 13:32:24 blue kernel: [17548694.832000] usb 1-6: USB disconnect, address 82
Apr  7 13:32:24 blue kernel: [17548694.832000] visor 1-6:1.0: device disconnected
Apr  7 13:32:25 blue kernel: [17548695.648000] usb 1-6: new full speed USB device using ohci_hcd and address 83
Apr  7 13:32:25 blue kernel: [17548695.868000] usb 1-6: configuration #1 chosen from 1 choice
Apr  7 13:32:25 blue kernel: [17548695.876000] visor 1-6:1.0: Handspring Visor / Palm OS converter detected
Apr  7 13:32:25 blue kernel: [17548695.876000] usb 1-6: Handspring Visor / Palm OS converter now attached to ttyUSB2
Apr  7 13:32:25 blue kernel: [17548695.876000] usb 1-6: Handspring Visor / Palm OS converter now attached to ttyUSB3

---------------------------------------------------------------------------------------------------------------------------------
kpilot log
---------------------------------------------------------------------------------------------------------------------------------
Version: KPilot 4.6.0 (blivit)
Version: pilot-link 0.12.1
Version: KDE 3.5.4
Version: Qt 3.3.6

HotSync Log
13:32:08 Starting the KPilot daemon ...
13:32:08 Daemon status is `not running'
13:32:09 Next HotSync will be: Copy Handheld to PC. Please press the HotSync button.
13:32:09 Pilot device /dev/pilot does not exist. Probably it is a USB device and will appear during a HotSync.
13:32:16 Device link ready.
13:32:24 Unable to read system information from Pilot

---

### Post by mykrob on 2007-04-07
dont know if this is your problem or not, but I was unable to sync my Palm until i loaded the "visor" module

sudo modprobe visor



If this works, add a new line containing the word 

visor

to the file /etc/modules

This will load the module at boot time.

---

### Post by martalli on 2008-04-04
Once again, I was having trouble syncing my Treo 680 with kubuntu, but the simple "sudo modprobe visor" worked instantly.  Thanks for the advice!  I wonder if installation of kpilot should have instantly add this module, or at least offer to do so?

---

