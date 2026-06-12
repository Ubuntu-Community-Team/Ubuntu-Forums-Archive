---
title: "Synce Help"
date: 2008-12-29
forum: General Help
---

### Post by igknighted on 2008-12-29
Following the intrepid directions here: [http://ubuntuforums.org/showpost.php?p=6258719&postcount=6/](http://ubuntuforums.org/showpost.php?p=6258719&postcount=6/), when I get to the part where it asks me to plug in the device and run 'synce-pls', i get the following message:

```
fitzgid@lappy:~$ synce-pls 
** Message: Hal reports no devices connected

** (process:8954): WARNING **: synce_info_from_odccm: Failed to get devices: The name org.synce.odccm was not provided by any .service files
synce-pls: Could not find configuration at path '(Default)'
```

The ODCCM one is be expected I guess, as Synce now uses HAL, but it claims there is nothing on HAL?  The device is a Motorola q9c, FWIW.

---

### Post by climberjc on 2009-01-04
> **igknighted said:**
> Following the intrepid directions here: [http://ubuntuforums.org/showpost.php?p=6258719&postcount=6/](http://ubuntuforums.org/showpost.php?p=6258719&postcount=6/), when I get to the part where it asks me to plug in the device and run 'synce-pls', i get the following message:

```
fitzgid@lappy:~$ synce-pls 
** Message: Hal reports no devices connected

** (process:8954): WARNING **: synce_info_from_odccm: Failed to get devices: The name org.synce.odccm was not provided by any .service files
synce-pls: Could not find configuration at path '(Default)'
```

The ODCCM one is be expected I guess, as Synce now uses HAL, but it claims there is nothing on HAL?  The device is a Motorola q9c, FWIW.

I have the same error, and have been trying trying to fix it for a few days now. If it helps at all, I am trying to sync with a Motorola Q9C, and the device shows up on lsusb:
Bus 004 Device 016: ID 22b8:7008 Motorola PCS

I replied to another thread from a few months ago that had the same problem:
[http://ubuntuforums.org/showthread.php?p=6494658#post6494658]("http://ubuntuforums.org/showthread.php?p=6494658#post6494658")
with more detailed information, like the result from lsusb -v and xterm -e 'tail -f /var/log/messages'

---

