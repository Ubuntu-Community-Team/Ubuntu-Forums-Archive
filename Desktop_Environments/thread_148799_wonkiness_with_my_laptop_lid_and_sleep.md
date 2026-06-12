---
title: "wonkiness with my laptop lid and sleep"
date: 2006-03-22
forum: Desktop Environments
---

### Post by groggyboy on 2006-03-22
i have configured my laptop to sleep when i close the lid.  when i open the lid, it does something weird: it automatically resumes from suspend, and i see the desktop, but then it immediately goes back to suspend mode.  from there, i have to press the power button to wake it.  after that, everything is normal.  (if i suspend from the logout menu, it works normally.)

it's not really urgent, but does anyone know why this happens?

---

### Post by groggyboy on 2006-03-23
<bump>

no ideas?

---

### Post by ranf on 2006-03-24
[QUOTE=groggyboy]i have configured my laptop to sleep when i close the lid.  [/QUOTE]
What did you do exactly to configure this?

---

### Post by groggyboy on 2006-03-24
i edited the file /etc/acpi/events/lidbtn from:> # /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/**lid.sh** to:> # /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/**sleep.sh**

I'm pretty sure that's all I did.

---

### Post by ranf on 2006-03-24
Any specs of your machine?

I had a similar problem because I edited a file under /etc/acpi/events. And another file there felt to be responsible for the same event as well.

---

### Post by groggyboy on 2006-03-25
sorry for the wait.  had a crazy friday (school n such).

what kind of specs?

i think i also may have edited my /etc/defaults/acpi-support file.  but all i did (i think) was uncomment the first line:> # Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

what other files might want control?

---

### Post by ranf on 2006-03-25
Before you put your laptop to sleep you can run this:
```
sudo tail -f /var/log/acpid
```

Specs? The model of your laptop would be of interest.

---

### Post by groggyboy on 2006-03-26
aah, specs! :mrgreen: 

dell inspiron 6000.  intel video card.

but more interesting, the results of the sudo tail (i don't understand it all):> [Sun Mar 26 11:05:34 2006] received event "button/lid LID 00000080 00000001"
[Sun Mar 26 11:05:34 2006] notifying client 7480[0:0]
[Sun Mar 26 11:05:34 2006] executing action "/etc/acpi/sleep.sh"
[Sun Mar 26 11:05:34 2006] BEGIN HANDLER MESSAGES
There is already a pid file /var/run/dhclient.eth1.pid with pid 6938
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:13:ce:33:99:24
Sending on   LPF/eth1/00:13:ce:33:99:24
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:13:ce:33:99:24
Sending on   LPF/eth1/00:13:ce:33:99:24
Sending on   Socket/fallback
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver-command: can't open display :0
grep: /proc/acpi/fan/*/state: No such file or directory
[Sun Mar 26 11:05:58 2006] END HANDLER MESSAGES
[Sun Mar 26 11:05:58 2006] action exited with status 0
[Sun Mar 26 11:05:58 2006] executing action "/etc/acpi/actions/lm_lid.sh button/lid LID 00000080 00000001"
[Sun Mar 26 11:05:58 2006] BEGIN HANDLER MESSAGES
Laptop mode already active, not restarting.
[Sun Mar 26 11:05:58 2006] END HANDLER MESSAGES
[Sun Mar 26 11:05:58 2006] action exited with status 0
[Sun Mar 26 11:05:58 2006] completed event "button/lid LID 00000080 00000001"
[Sun Mar 26 11:05:58 2006] received event "ac_adapter AC 00000080 00000000"
[Sun Mar 26 11:05:58 2006] notifying client 7480[0:0]
[Sun Mar 26 11:05:58 2006] executing action "/etc/acpi/power.sh"
[Sun Mar 26 11:05:58 2006] BEGIN HANDLER MESSAGES
[Sun Mar 26 11:05:58 2006] END HANDLER MESSAGES
[Sun Mar 26 11:05:58 2006] action exited with status 0
[Sun Mar 26 11:05:58 2006] executing action "/etc/acpi/actions/lm_ac_adapter.sh ac_adapter AC 00000080 00000000"
[Sun Mar 26 11:05:58 2006] BEGIN HANDLER MESSAGES
Laptop mode already active, not restarting.
[Sun Mar 26 11:05:58 2006] END HANDLER MESSAGES
[Sun Mar 26 11:05:58 2006] action exited with status 0
[Sun Mar 26 11:05:58 2006] completed event "ac_adapter AC 00000080 00000000"
[Sun Mar 26 11:05:58 2006] received event "button/lid LID 00000080 00000002"
[Sun Mar 26 11:05:58 2006] notifying client 7480[0:0]
[Sun Mar 26 11:05:58 2006] executing action "/etc/acpi/sleep.sh"
[Sun Mar 26 11:05:58 2006] BEGIN HANDLER MESSAGES
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.145 -- renewal in 36726 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 10405
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:13:ce:33:99:24
Sending on   LPF/eth1/00:13:ce:33:99:24
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:13:ce:33:99:24
Sending on   LPF/eth1/00:13:ce:33:99:24
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.145 -- renewal in 34479 seconds.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver-command: can't open display :0
grep: /proc/acpi/fan/*/state: No such file or directory
[Sun Mar 26 11:06:23 2006] END HANDLER MESSAGES
[Sun Mar 26 11:06:23 2006] action exited with status 0
[Sun Mar 26 11:06:23 2006] executing action "/etc/acpi/actions/lm_lid.sh button/lid LID 00000080 00000002"
[Sun Mar 26 11:06:23 2006] BEGIN HANDLER MESSAGES
Laptop mode already active, not restarting.
[Sun Mar 26 11:06:23 2006] END HANDLER MESSAGES
[Sun Mar 26 11:06:23 2006] action exited with status 0
[Sun Mar 26 11:06:23 2006] completed event "button/lid LID 00000080 00000002"
[Sun Mar 26 11:06:23 2006] received event "battery BAT0 00000081 00000001"
[Sun Mar 26 11:06:23 2006] notifying client 7480[0:0]
[Sun Mar 26 11:06:23 2006] executing action "/etc/acpi/power.sh"
[Sun Mar 26 11:06:23 2006] BEGIN HANDLER MESSAGES
[Sun Mar 26 11:06:23 2006] END HANDLER MESSAGES
[Sun Mar 26 11:06:23 2006] action exited with status 0
[Sun Mar 26 11:06:23 2006] executing action "/etc/acpi/actions/lm_battery.sh battery BAT0 00000081 00000001"
[Sun Mar 26 11:06:23 2006] BEGIN HANDLER MESSAGES
remaining capacity:      6256 mAh
[Sun Mar 26 11:06:23 2006] END HANDLER MESSAGES
[Sun Mar 26 11:06:23 2006] action exited with status 0
[Sun Mar 26 11:06:23 2006] completed event "battery BAT0 00000081 00000001"
[Sun Mar 26 11:06:23 2006] received event "ac_adapter AC 00000080 00000000"
[Sun Mar 26 11:06:23 2006] notifying client 7480[0:0]
[Sun Mar 26 11:06:23 2006] executing action "/etc/acpi/power.sh"
[Sun Mar 26 11:06:23 2006] BEGIN HANDLER MESSAGES
[Sun Mar 26 11:06:23 2006] END HANDLER MESSAGES
[Sun Mar 26 11:06:23 2006] action exited with status 0
[Sun Mar 26 11:06:23 2006] executing action "/etc/acpi/actions/lm_ac_adapter.sh ac_adapter AC 00000080 00000000"
[Sun Mar 26 11:06:23 2006] BEGIN HANDLER MESSAGES
Laptop mode already active, not restarting.
[Sun Mar 26 11:06:23 2006] END HANDLER MESSAGES
[Sun Mar 26 11:06:23 2006] action exited with status 0
[Sun Mar 26 11:06:23 2006] completed event "ac_adapter AC 00000080 00000000"
[Sun Mar 26 11:06:23 2006] received event "battery BAT0 00000081 00000001"
[Sun Mar 26 11:06:23 2006] notifying client 7480[0:0]
[Sun Mar 26 11:06:23 2006] executing action "/etc/acpi/power.sh"
[Sun Mar 26 11:06:23 2006] BEGIN HANDLER MESSAGES
[Sun Mar 26 11:06:23 2006] END HANDLER MESSAGES
[Sun Mar 26 11:06:23 2006] action exited with status 0
[Sun Mar 26 11:06:23 2006] executing action "/etc/acpi/actions/lm_battery.sh battery BAT0 00000081 00000001"
[Sun Mar 26 11:06:23 2006] BEGIN HANDLER MESSAGES
remaining capacity:      6256 mAh
[Sun Mar 26 11:06:23 2006] END HANDLER MESSAGES
[Sun Mar 26 11:06:23 2006] action exited with status 0
[Sun Mar 26 11:06:23 2006] completed event "battery BAT0 00000081 00000001"
rm: cannot remove `/var/lock/acpisleep': No such file or directory

as i said, i don't really understand it - but at a guess i would say it looks like laptop mode is causing the problem?

thanks for the help, btw.

---

### Post by ranf on 2006-03-26
First it runs this:
```
[Sun Mar 26 11:05:34 2006] executing action "/etc/acpi/sleep.sh"

```

then this:
```
[Sun Mar 26 11:05:58 2006] executing action "/etc/acpi/actions/lm_lid.sh button/lid LID 00000080 00000001"
```

I had to search on "lm_lid.sh" at [http://packages.ubuntu.com](http://packages.ubuntu.com). It is from the package `laptop-mode-tools'.
While the first one is installed by default (in package `acpi-support') you must have installed the laptop-mode-tools later on.

I'd try removing laptop-mode-tools and see what happens.

---

### Post by groggyboy on 2006-03-26
okay, uninstalled laptop-mode-tools.

too bad the lid still is still being wonky.  the results of the sudo tail are different now:> [Sun Mar 26 13:38:43 2006] executing action "/etc/acpi/sleep.sh"
[Sun Mar 26 13:38:43 2006] BEGIN HANDLER MESSAGES
..
[Sun Mar 26 13:39:22 2006] END HANDLER MESSAGES
[Sun Mar 26 13:39:22 2006] action exited with status 0
[Sun Mar 26 13:39:22 2006] completed event "button/lid LID 00000080 00000001"
[Sun Mar 26 13:39:22 2006] received event "ac_adapter AC 00000080 00000000"
[Sun Mar 26 13:39:22 2006] notifying client 7472[0:0]
[B][Sun Mar 26 13:39:22 2006] executing action "/etc/acpi/power.sh"
[Sun Mar 26 13:39:22 2006] BEGIN HANDLER MESSAGES
[Sun Mar 26 13:39:22 2006] END HANDLER MESSAGES
[Sun Mar 26 13:39:22 2006] action exited with status 0
[Sun Mar 26 13:39:22 2006] completed event "ac_adapter AC 00000080 00000000"
[Sun Mar 26 13:39:22 2006] received event "button/lid LID 00000080 00000002"
[Sun Mar 26 13:39:22 2006] notifying client 7472[0:0]
[Sun Mar 26 13:39:22 2006] executing action "/etc/acpi/sleep.sh"[/B]
[Sun Mar 26 13:39:22 2006] BEGIN HANDLER MESSAGES
..
[Sun Mar 26 13:39:51 2006] END HANDLER MESSAGES
[Sun Mar 26 13:39:51 2006] action exited with status 0
[Sun Mar 26 13:39:51 2006] completed event "button/lid LID 00000080 00000002"
[Sun Mar 26 13:39:51 2006] received event "battery BAT0 00000081 00000001"
[Sun Mar 26 13:39:51 2006] notifying client 7472[0:0]
[Sun Mar 26 13:39:51 2006] executing action "/etc/acpi/power.sh"
[Sun Mar 26 13:39:51 2006] BEGIN HANDLER MESSAGES
[Sun Mar 26 13:39:51 2006] END HANDLER MESSAGES
[Sun Mar 26 13:39:51 2006] action exited with status 0
[Sun Mar 26 13:39:51 2006] completed event "battery BAT0 00000081 00000001"
[Sun Mar 26 13:39:51 2006] received event "ac_adapter AC 00000080 00000000"
[Sun Mar 26 13:39:51 2006] notifying client 7472[0:0]
[Sun Mar 26 13:39:51 2006] executing action "/etc/acpi/power.sh"
[Sun Mar 26 13:39:51 2006] BEGIN HANDLER MESSAGES
[Sun Mar 26 13:39:51 2006] END HANDLER MESSAGES
[Sun Mar 26 13:39:51 2006] action exited with status 0
[Sun Mar 26 13:39:51 2006] completed event "ac_adapter AC 00000080 00000000"
[Sun Mar 26 13:39:51 2006] received event "battery BAT0 00000081 00000001"
[Sun Mar 26 13:39:51 2006] notifying client 7472[0:0]
[Sun Mar 26 13:39:51 2006] executing action "/etc/acpi/power.sh"
[Sun Mar 26 13:39:51 2006] BEGIN HANDLER MESSAGES
[Sun Mar 26 13:39:51 2006] END HANDLER MESSAGES
[Sun Mar 26 13:39:51 2006] action exited with status 0
[Sun Mar 26 13:39:51 2006] completed event "battery BAT0 00000081 00000001"
..
rm: cannot remove `/var/lock/acpisleep': No such file or directory

??? it thinks the lid is being closed?

---

### Post by ranf on 2006-03-27
[QUOTE=groggyboy]okay, uninstalled laptop-mode-tools.

too bad the lid still is still being wonky.  the results of the sudo tail are different now:

??? it thinks the lid is being closed?[/QUOTE]
What I doen't like about it is the last line in the log:
```
rm: cannot remove `/var/lock/acpisleep': No such file or directory
```

This file should be created by prepare.sh. From the top of /etc/acpi/prepare.sh
```

#!/bin/bash

#prevent acpid from processing any following events
touch /var/lock/acpisleep

```
Can you verify this is also in yours?

---

### Post by groggyboy on 2006-03-27
hmmm... /etc/acpi/prepare.sh has the lines:> #!/bin/bash

#prevent acpid from processing any following events
touch /var/lock/acpisleep

out of curiosity, i looked in /var/lock/ but it was empty except for a folder named lvm (which was also empty).  am i missing a file?

---

### Post by ranf on 2006-03-29
These lock files usually are created to prevent running a process twice. 
In our case `prepare.sh' creates it (with touch).
And `resume.sh' _should_ remove it after resuming.

---

### Post by groggyboy on 2006-03-30
i checked resume.sh for any appearance of /var/touch/acpisleep.  it shows up at the very end of the file:> #Let acpid process events again
(sleep 5 && rm /var/lock/acpisleep)&

The laptop used to be set to turn the screen off when the lid closed.  I had trouble with the screen not turning back on.  I had to switch to a console and then back to X to get the screen back.  Could that be related to the current problem?

---

