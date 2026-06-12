---
title: "Help increasing battery life Dell inspiron 1525"
date: 2008-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by henry_d on 2008-10-07
I have a Dell inspiron 1525 and ubuntu 8.04 which i installed over vista but it seems to have less battery life.
Could someone give me some tips to increase the battery life and how long do you think i could get the battery to last as it is currently at 2 hours after a full charge.

Any help would be much appreciated

---

### Post by joshuajtl on 2008-10-14
I also have had the same problem since I first put ubuntu on this machine, 6 months ago.

---

### Post by loneowais on 2008-12-09
Same here...I also tried various methods & switched between various power management packages but still I get a max of 2 hours in Ubuntu in balanced mode, while as I get 3.5 hours in vista in balanced mode.

I hate MS & their products and I don't want to go back. Someone help...
I don't remember how Hardy was with power management...Should I downgrade?

---

### Post by iggykoopa on 2008-12-09
you could try the gui I'm working on, the thread is here [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309) . It might help a little.

---

### Post by dwarness on 2008-12-09
I've been doing some research lately on exactly this topic and have gathered some suggestions from different sources.  Some comes from powertop suggestions, others I got from the guide: [Installing Ubuntu on a Dell XPS m1530]("https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530")

I haven't actually tested how much of a gain on battery time I've gotten, but it is noticeable.  Most of this should be generic enough and not specific to my make/model of laptop.  Let me know how it fairs for you.  Just one caveat, though.  After making these settings when running on battery, I did notice a slight pause each time a new file is opened.  This has to do with the hard drive spinning down to conserve power.

Put the following code in a script and place that script in both: /etc/acpi/ac.d/ and /etc/acpi/battery.d/

```

#!/bin/sh

POWERSTATEFILE="/var/lib/acpi-support/powerstate"
POWERSTATE=`cat $POWERSTATEFILE`

if [ x"$POWERSTATE" = x"AC" ] ; then
	echo 60		> /proc/sys/vm/swappiness
	echo 3000	> /proc/sys/vm/dirty_expire_centisecs
	echo 500	> /proc/sys/vm/dirty_writeback_centisecs
	echo 10		> /proc/sys/vm/dirty_background_ratio
	echo 40		> /proc/sys/vm/dirty_ratio
	echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy

	# Enable CDROM Polling
	/usr/bin/hal-disable-polling --enable-polling --device /dev/cdrom

	# Enable the Firewire Module
	/sbin/modprobe ohci1394
else
	echo 10		> /proc/sys/vm/swappiness
	echo 0		> /proc/sys/vm/dirty_expire_centisecs
	echo 1500	> /proc/sys/vm/dirty_writeback_centisecs
	echo 60		> /proc/sys/vm/dirty_background_ratio
	echo 95		> /proc/sys/vm/dirty_ratio
	echo min_power	> /sys/class/scsi_host/host0/link_power_management_policy

	# Disable CDROM Polling (Warning, if you insert a CD, it won't automount)
	/usr/bin/hal-disable-polling --device /dev/cdrom

	# Remove the Firewire Module
	/sbin/modprobe -r ohci1394
fi


```

---

### Post by jakerella on 2009-04-30
In case anyway is looking for some generic tips, try out:
[http://pherricoxide.wordpress.com/2009/02/07/increase-battery-life-on-ubuntu-810/](http://pherricoxide.wordpress.com/2009/02/07/increase-battery-life-on-ubuntu-810/)

In fact, from there I found the tool to disable your ethernet port (when my laptop is on battery power, I am usually using wireless). You will first need to install the ethtool:

```
sudo apt-get install ethtool
```

Then add this line to the script file Dave has (near the bottom, right after removal of the Firewire module):
```
# Disable ethernet (presumed using wireless)
/usr/sbin/ethtool -s eth0 wol d
```

Good luck.
--Jordan

---

### Post by sdennie on 2009-04-30
Not the same model but, you may find this thread useful for getting ideas: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

---

### Post by abn91c on 2009-04-30
check your BIOS my inspiron 1000 has a battery conditioning utility there. they suggest you run it at night since it can take several hrs to complete.

---

