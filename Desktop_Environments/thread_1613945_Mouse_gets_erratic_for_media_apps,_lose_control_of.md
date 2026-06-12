---
title: "Mouse gets erratic for media apps, lose control of desktop env."
date: 2010-11-05
forum: Desktop Environments
---

### Post by m.dr on 2010-11-05
My Ub 10.10 has been running fine, all updates installed but recently after installing Picasa (I think) getting erratic results when I launch media related apps: Picasa, Brasero, Acrobat.

When I launch these apps the mouse goes totally erratic, even clicking in places and wrecking havoc - I don't mean it lightly.

I can sometimes control the mouse by switching desktops and getting to the console and killing Picasa or such. Sometimes I have to logoff and log back in as the mouse and screen totally locks up.

So I had Picasa and such in 10.04 as well, no such problem. In fact I had been using Picasa in 10.10 but I think this erraticism started once I made an update.

But am not sure when it really started. Just wondering if anyone is facing the same. From external apps I also have Matlab installed, dev tools such as build-essential, jdk installed among the major things. No games and such.

Please let me know if there is any rectification of this, or if there is a way to mention it to the Ub developers.

Look forward to hearing from you.

Thanks for your help.

---

### Post by P4man on 2010-11-05
Check your log files. Particularly /var/log/dmesg and /var/log/syslog. You can do so easily through system > administration > log file viewer.

To report bug have a look here:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

But it would be in your and their interest to gather a bit more information first.

---

### Post by m.dr on 2010-11-06
Here's my logs. Like it shows the mouse is losing synchronization. Happens when I open media apps like Picasa, Brasero etc. I have a USB cable connected but no hub or anything connected to it. Wondering if that can be a problem?

I have an older box so have a cable connected to the back as sometimes its difficult to get to it in the back.

Thanks again for your advice and suggestions.

--------

Nov  6 14:01:35 orange kernel: [21041.729193] hub 1-1:1.0: hub_port_status failed (err = -110)
Nov  6 14:01:37 orange kernel: [21043.336009] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Nov  6 14:01:37 orange kernel: [21043.452692] psmouse.c: resync failed, issuing reconnect request
Nov  6 14:01:40 orange kernel: [21046.733362] hub 1-1:1.0: hub_port_status failed (err = -110)
Nov  6 14:01:42 orange kernel: [21048.474102] psmouse serio1: ID: 11 00 3c
Nov  6 14:01:46 orange kernel: [21051.817572] hub 1-1:1.0: hub_port_status failed (err = -110)

---

### Post by P4man on 2010-11-06
Okay. See the link in my signature for possible workarounds. 
the acpi_osi= switch might help, or acpi_osi=Linux.  noapic might help too (see the link if you have no idea what Im saying).

There is a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194)

You may want to subscribe to it, and there are some other possible workaround in there too.

---

### Post by m.dr on 2010-11-12
Ok great. Thanks for the help.
I can see there are no solutions.

I solved it by hitting the ESC key a couple of times.
Then mouse seems to be back fine.

Thanks again and sorry for the delayed response.

---

