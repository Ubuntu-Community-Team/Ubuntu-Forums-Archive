---
title: "udev on 9.04 - USB backup"
date: 2009-04-30
forum: General Help
---

### Post by bonjour on 2009-04-30
I've just upgraded to 9.04 and found that a little USB backup system that I've been using on all previous versions has ceased to work.

The system basically involved placing a file called 55-usb-backup.rules in the /etc/udev/rules.d folder, which called a shell script in /usr/local/bin/

The contents of /etc/udev/rules.d/55-usb-backup.rules is as below:

[I]#KERNEL=="sd*", SUBSYSTEMS="scsi", ATTRS{model}=="USB 2.0 Storage Device", RUN+="/usr/local/bin/usb-backup.sh"
KERNEL=="sd*", SUBSYSTEMS=="usb", SUBSYSTEMS=="scsi", ACTION=="add", RUN+="/usr/local/bin/usb-backup %k"

[/I]I've discovered that the rules.d folder has been moved to /lib/udev/rules.d, but even moving 55-usb-backup.rules across to this folder does not activate my usb-backup script when a usb drive is inserted.

Has anything else changed regarding the udev rules?

Ta.

---

