---
title: "Add a script to end of boot sequence"
date: 2009-04-15
forum: General Help
---

### Post by hjtrost on 2009-04-15
I have installed Ubuntu on a 10 year old machine (AMD K6-2, 256 MB RAM, 8.4 GB IDE, 4.2 GB SCSI), and have it working reasonably well.  The only problem is that I need to manually run a script to get the SCSI drive started.  The script is

#!/bin/sh
modprobe aha152x
wait
sleep 3
wait
rmmod aha152x
wait
sleep 3
wait
modprobe aha152x
wait
sleep 5
wait
mount /dev/sdb1 /work

emulating my handiwork in a terminal window.  The "wait"s guarantee zero overlap in time of the successive command execution.  I now run this from a terminal once after boot up (and login) with a command "sudo sh workdisk".

I want this script to run automatically at the end of the boot sequence just before the login screen is displayed.  It does need root/superuser privileges to succeed.

Where do I put/call this script?

Cheers,            Jochen

P.S.: Is there a better suited forum where I should have put this post in?

---

### Post by eldragon on 2009-04-15
add the command to /etc/rc.local

no need to sudo it since its run as root already

---

### Post by hjtrost on 2009-04-16
> **eldragon said:**
> add the command to /etc/rc.local

no need to sudo it since its run as root already

Thanks, that looks exactly like what I need.  The sudo comes about only for me to run the script by hand from my regular account.  Thanks for confirming on that one what I had hoped for.

Cheers,      Jochen

---

### Post by hjtrost on 2009-04-17
SOLVED.

Works as desired!  I added a test around the core part of the script to prevent it from being executed twice, e.g., when I should change run levels without rebooting (should I ever do that).

Cheers,           Jochen

---

### Post by kpkeerthi on 2009-04-17
Both the **modprobe **and **mount **commands you have used in your script requires root privileges. It worked since commands from rc.local are executed with root privileges.

---

