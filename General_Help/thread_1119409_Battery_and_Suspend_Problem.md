---
title: "Battery and Suspend Problem"
date: 2009-04-07
forum: General Help
---

### Post by tklaus on 2009-04-07
I just recently set up a dual boot with Ubuntu and Vista, and I noticed that the battery life on my laptop differs pretty drastically when going between the two OS. Vista on balanced lasted around 3.5 to 4 hours where it seems Ubuntu is getting around 2. I don't have the brightness all the way up and I am not running any really heavy procesoses. Is there a reason for this?

Also, when I try to use suspend it turns off the computer, but then when I turn it back on nothing shows up on the screen. Will this solution work for me or is it for a mod of Ubuntu? [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

---

### Post by Sam Lars on 2009-04-09
There are many things you could tweak to change power consumption...
I have a script that makes some changes when switching to battery power and back to AC.  I currently don't use it (just reinstalled with Jaunty), but may try some testing with it later.
You could try some of the commands to see if they help... if you have any questions as to what any of them do, search the forums or ask.

As for the solution you linked to, it should work on any version of Ubuntu.


```
#!/bin/bash
 
# Go fast.  More or less Ubuntu defaults
if on_ac_power; then
  hdparm -B 255 -S 240 -M 254 /dev/sda
  mount -o remount,commit=5 /
  mount -o remount,commit=5 /home
  echo 0 > /proc/sys/vm/laptop_mode
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  iwpriv wlan0 power_profile 1
  echo 50 > /proc/sys/vm/swappiness
  echo 3000 > /proc/sys/vm/dirty_expire_centisecs
  hal-disable-polling --device /dev/scd0 --enable-polling
  /etc/init.d/postfix start
  /etc/init.d/anacron start
  /etc/init.d/ntp start
  LINEBACKER=$(/tmp/backlightgot)
  xbacklight -set $LINEBACKER
else # Save power
  hdparm -B 1 -S 4 -M 128 /dev/sda
  mount -o remount,commit=600 /
  mount -o remount,commit=600 /home
  echo 5 > /proc/sys/vm/laptop_mode
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 30000 > /proc/sys/vm/dirty_writeback_centisecs
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  iwpriv wlan0 power_profile 5
  echo 10 > /proc/sys/vm/swappiness
  echo 0 > /proc/sys/vm/dirty_expire_centisecs
  hal-disable-polling --device /dev/scd0
  /etc/init.d/postfix stop
  /etc/init.d/anacron stop
  /etc/init.d/ntp stop
  /etc/init.d/rsync stop
  /etc/init.d/smartmontools stop
  xbacklight > /tmp/xbacklightgot
  xbacklight -set 30
fi
```

---

