---
title: "Palm /dev/pilot Permissions?"
date: 2005-03-23
forum: Desktop Environments
---

### Post by sgbeamer on 2005-03-23
My palm synced the first time I tried it after I made the symlink to /dev/pilot   BUT

Now the only way I can get it to sync is to open a root window and chmod  to 0666 after I push the sync button. I must do this each and every time I sync.  I've tried setting the permissions in the udev rules and I still can't get it to work.

What am I missing?

Palm is /dev/usb/ttyUSB1

---

### Post by Blackneto on 2005-03-23
check /var/log/messages when you hit the hotsync buttton on the cradle.
I had a similar problem and it wasn't the permissions on the device (I just entered /dev/usb/ttyUSB1 in my configuration) 
What was happening is gpilotd wasn't releasing the device after the sync was done. so on subsequent syncs, if i hadn't rebooted, the device number just kept increasing /dev/usb/ttyUSB2 /dev/usb/ttyUSB3 /dev/usb/ttyUSB*, etc. 
so the program was looking for the palm in the wrong place. i believe this is a known bug with gpilotd.
just HUP it or kill it and restart it and see if that fixes anything.

---

### Post by sgbeamer on 2005-03-25
Thanks, I checked the log file and this does not appear to be the problem.  Each time I plug in I get the following:

[INDENT]Mar 23 05:46:57 localhost kernel: visor 2-2.2:1.0: Handspring Visor / Palm OS converter detected
Mar 23 05:46:57 localhost kernel: usb 2-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Mar 23 05:46:57 localhost kernel: usb 2-2.2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Mar 23 05:48:44 localhost kernel: usb 2-2.2: USB disconnect, address 10
Mar 23 05:48:44 localhost kernel: visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Mar 23 05:48:44 localhost kernel: visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Mar 23 05:48:44 localhost kernel: visor 2-2.2:1.0: device disconnected
[/INDENT]

---

### Post by Blackneto on 2005-03-25
well i haven't had to chmod /dev/pilot  so i'm not sure whats going on.

Check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=21466](http://www.ubuntuforums.org/showthread.php?t=21466)

I used information from all the links i posted there to figure out what was wrong with my setup.

---

