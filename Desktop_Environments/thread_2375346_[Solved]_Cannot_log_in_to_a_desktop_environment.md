---
title: "[Solved] Cannot log in to a desktop environment"
date: 2017-10-24
forum: Desktop Environments
---

### Post by i2000s2 on 2017-10-24
Suddenly in one day, I cannot access to my desktop GUI environment. The booting screen stops at a maintenance mode with root logged in to a TTY. I had XFce and Gnome desktop environment installed. XFCE is the default option. There is no internet access as well. 

When I type 

```
service lightdm start
```

it always fails with "lightdm failed to start" error. 

```
journalctl -Xb 
```
 
gives a few errors on loading my NTFS partitions and acpi loading so such. I don't see anything related to internet or other obverse issues. How should I rescue my system? Thanks!

---

### Post by Bashing-om on 2017-10-24
i2000s2; Hello;

From grub's boot menu can you activate a "recovery kernel" selection ?
else also, what results at the login screen with key combo ctl+alt+F1 ?

elseif:

[INDENT][INDENT]we look for other means
[/INDENT][/INDENT]

---

### Post by i2000s2 on 2017-10-24
Hi Bashing-om! Glad to see you here! 

I have only one kernel installed, as my boot partition was too small. I'll try rebooting later to see if the recovery kernel option is available. 

If I press ctl+alt+F1, I'll enter a black screen with a flashing cursor on the top. Nothing I can type in there.

---

### Post by Bashing-om on 2017-10-24
i2000s2; Well ,,, 

What release is this ?
I can accept that blinking cursor in TTY1 as valid IF this is 17.10.
Try to activate other TTYs ( F2,3,4 ............)

I can accept that there are issues in 17.10 IF this system has nvidia hybrid graphics -

What I mean here is that we are still in that process of discovery .

we see what path we take
[INDENT][INDENT][INDENT]where it leads us to
[/INDENT][/INDENT][/INDENT]

---

### Post by i2000s2 on 2017-10-24
I am using 16.04.3 with 6700HQ CPU and the M100M NVidia GPU. Yes, I have enabled the NVidia non-open-source GPU driver. I feel this is also desktop environment related. Last time, when I enabled Gnome, it worked once for a short time. After reboot into XFCE, the next reboot failed.  But this could also happen by chance. Any command line I can try in the maintenance mode? I am rebooting to see the recovery mode.

---

### Post by Bashing-om on 2017-10-24
i2000s2; Sure !

If you can activate the recovery interface -> root console:
Be of interest what shows :
```

lshw -C display

```

maybe the output shows as "unclaimed? ?
Maybe the output shows in the configuration line no driver loaded ?

[INDENT][INDENT]could be this
[INDENT][INDENT][INDENT]might be something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by i2000s2 on 2017-10-24
> **Bashing-om said:**
> i2000s2; Sure !

If you can activate the recovery interface -> root console:
Be of interest what shows :
```

lshw -C display

```

maybe the output shows as "unclaimed? ?
Maybe the output shows in the configuration line no driver loaded ?
[INDENT][INDENT]could be this[INDENT][INDENT][INDENT]might be something else
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

Hi there,

Sorry, I didn't read your message while rebooting into the recovery mode. So far, seems I have found the problem and solved it! 

When I went into the recovery mode, I used the failsafe mode to see if anything worked, then I went into the `/var/log/Xorg.failsafe.log` file and found there are errors on dbus-core and system bus input/output and /var/run/dbus/system_bus_socket. I feel there might be something wrong with my USB ports. So, I noticed I have a tablet connected to my DisplayLink Dock Station. That might be the problem. So, resuming the computer and I entered the normal booting mode. It halted over on the booting screen with TTY1 message asking to enter the maintenance mode. On the `journalctl -xb` log, I found the error includes messages about the usb 1-1.4.2 and /lib/udev/usb-db failures. Again, I feel the culprit is the Dock station and devices connected. Disconnecting the Dock station completely, I rebooted my computer. Hoooray, it worked out without any problem...

So, I will mark this thread as Solved, and thank you for helping around!

---

### Post by lisati on 2017-10-24
> **i2000s2 said:**
> 
So, I will mark this thread as Solved, and thank you for helping around!

Please use the Thread Tools->Mark Thread Solved menu option near the top of the page.

---

