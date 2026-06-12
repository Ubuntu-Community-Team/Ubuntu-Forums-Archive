---
title: "Automatic control of laptop mode not activated?"
date: 2009-08-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mjwalfredo on 2009-08-16
There are two things that are keeping me from being perfectly happy with the way Ubuntu 9.04 runs on my Inspiron 1420n laptop.  One is the fact that my webcam still doesn't work and two, power management does not seem to work like it is supposed to. I seem to get horrible battery life and the system does not hibernate when battery is critcally low even though gnome-power-manager reports that it is set to do so.  Instead of hibernating, the power just dies completely like if you pulled the plug on a desktop computer.

This morning I have been trying to work on problem number two. I learned about laptop mode and I checked "/proc/sys/vm/laptop_mode".  It seems to always be set at "0" regardless of the machine running on AC or battery.

I have managed to manually set it by issuing the command:  "sudo laptop_mode start" but I would really like to get it working automatically.

Synaptic reports that I have laptop-mode-tools version  1.47-1ubuntu1 installed.

How can I get laptop mode to automatically start/stop?

---

### Post by mjwalfredo on 2009-08-16
So I have noticed that laptop mode does work but only if the computer is on battery power when it boots up or resumes from suspend.  If I boot it up or resume while it is plugged in, it fails to switch to laptop mode.

---

### Post by mikewhatever on 2009-08-17
You can try using this guide [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773). Just make sure you have the same hardware, and if different, comment out these lines or delete completely. Laptop mode and disk settings should apply regardless of hardware.

---

### Post by mjwalfredo on 2009-08-25
I found out about Powertop today on Slashdot and have started implementing some of the suggestions it made.

I read that I could add some statements to rc.local so that the settings are applied during system initialization.

```

echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo 5 > /proc/sys/vm/laptop_mode
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
hal-disable-polling --device /dev/cdrom
echo 5 > /sys/bus/pci/drivers/iwl3945/0000\:0c\:00.0/power_level

```

I have put the wireless device power setting on the last line because I don't think it is working correctly.  For one, when I had it first, none of the following statements would be applied.  Also, when I check the value after startup, it is set to 6 (AC) (whatever that means).

I had originally tried the wireless device path without the escaping slashes for the colongs and when that didn't work, I added the escape slashes but it still doesn't seem to work.

Also, can I add these to the resume scripts so they are applied after resuming from suspend?

---

### Post by mjwalfredo on 2009-08-26
I the following post that deals with setting up power saving features on Dell Laptops.  It is an excellent read and seems to cover exactly what I was trying to do.

I am going to try to implement these scripts later tonight.

[http://ubuntuforums.org/showthread.php?t=847773]("http://ubuntuforums.org/showthread.php?t=847773")

---

