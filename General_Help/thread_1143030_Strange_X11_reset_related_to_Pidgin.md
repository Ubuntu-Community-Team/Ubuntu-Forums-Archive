---
title: "Strange X11 reset related to Pidgin?"
date: 2009-04-29
forum: General Help
---

### Post by awhite on 2009-04-29
I was working on my computer using applications I use every day when suddenly the screen blanked out and then went to a terminal.  This terminal had the boot text (a bunch of lines with [ok]) at the end.  The last line was new and said:
> No path for 0465/c016 at 003/004.

Then I saw the computer seemed to try to recover from the crash and I saw:
> * Reloading Common Unix Printing System: cupsd
* Reloading system log daemon...

After a minute X reset and I had to login again.

If I look at my terminals, tty7 shows the two reloading lines and tty8 shows the bootup messages with the "No path for 0465/c016 at 003/004." line.  X is running on tty9.

If I look at dmesg the last line shows:
> [12207.444049] pidgin[5381]: segfault at 9ecf000 ip b7e73253 sp bfd5b740 error 6 in libX11.so.6.2.0[b7e44000+ea000]

So Pidgin caused the X reset!?

I opened up Ubuntu's log viewer.

In daemon.log
> Apr 29 12:36:13 awhite chipcardd[5099]: devicemanager.c: 3373: Changes in hardware list
Apr 29 12:36:14 awhite chipcardd[5099]: devicemanager.c: 3373: Changes in hardware list
Apr 29 12:36:30 awhite gdm[4691]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Apr 29 12:36:37 awhite acpid: client 4695[0:0] has disconnected 
Apr 29 12:36:37 awhite acpid: client 4695[0:0] has disconnected 
Apr 29 12:36:37 awhite acpid: client connected from 25408[0:0] 
Apr 29 12:36:38 awhite acpid: client connected from 25408[0:0] 
Apr 29 12:36:51 awhite acpid: client 25408[0:0] has disconnected 
Apr 29 12:36:51 awhite acpid: client 25408[0:0] has disconnected 
Apr 29 12:36:51 awhite acpid: client connected from 25427[0:0] 
Apr 29 12:36:52 awhite acpid: client connected from 25427[0:0] 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: Could not parse desktop file /home/awhite/.config/autostart/beryl-manager.desktop: Key file does not have key 'Type' 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: could not read /home/awhite/.config/autostart/beryl-manager.desktop 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: Could not parse desktop file /home/awhite/.config/autostart/evolution-alarm-notify.desktop: Key file does not have key 'Type' 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: could not read /home/awhite/.config/autostart/evolution-alarm-notify.desktop 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: Could not parse desktop file /home/awhite/.config/autostart/beagle-search-autostart.desktop: Key file does not have key 'Type' 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: could not read /home/awhite/.config/autostart/beagle-search-autostart.desktop 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: Could not parse desktop file /home/awhite/.config/autostart/beagled-autostart.desktop: Key file does not have key 'Type' 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: could not read /home/awhite/.config/autostart/beagled-autostart.desktop 
Apr 29 12:37:33 awhite NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Apr 29 12:37:52 awhite last message repeated 3 times
Apr 29 12:39:39 awhite NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Apr 29 12:40:10 awhite acpid: client 25427[0:0] has disconnected 
Apr 29 12:40:10 awhite acpid: client 25427[0:0] has disconnected

In kern.log
> Apr 29 12:36:12 awhite kernel: [12187.138481] hub 3-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Apr 29 12:36:13 awhite kernel: [12187.138488] usb 3-1: USB disconnect, address 2
Apr 29 12:36:13 awhite kernel: [12187.376035] usb 3-1: new low speed USB device using uhci_hcd and address 4
Apr 29 12:36:13 awhite kernel: [12187.549551] usb 3-1: configuration #1 chosen from 1 choice
Apr 29 12:36:13 awhite kernel: [12187.565695] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input7
Apr 29 12:36:13 awhite kernel: [12187.565914] generic-usb 0003:046D:C016.0004: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1/input0
Apr 29 12:36:30 awhite kernel: [12207.444049] pidgin[5381]: segfault at 9ecf000 ip b7e73253 sp bfd5b740 error 6 in libX11.so.6.2.0[b7e44000+ea000]

In messages
> Apr 29 12:36:13 awhite kernel: [12187.138488] usb 3-1: USB disconnect, address 2
Apr 29 12:36:13 awhite kernel: [12187.376035] usb 3-1: new low speed USB device using uhci_hcd and address 4
Apr 29 12:36:13 awhite kernel: [12187.549551] usb 3-1: configuration #1 chosen from 1 choice
Apr 29 12:36:13 awhite kernel: [12187.565695] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input7
Apr 29 12:36:13 awhite kernel: [12187.565914] generic-usb 0003:046D:C016.0004: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1/input0
Apr 29 12:36:30 awhite kernel: [12207.444049] pidgin[5381]: segfault at 9ecf000 ip b7e73253 sp bfd5b740 error 6 in libX11.so.6.2.0[b7e44000+ea000]
Apr 29 12:36:36 awhite bonobo-activation-server (awhite-25342): could not associate with desktop session: Failed to connect to socket /tmp/dbus-h0jhYqREAj: Connection refused
Apr 29 12:37:19 awhite pulseaudio[25627]: pid.c: Stale PID file, overwriting.

In syslog
> Apr 29 12:36:12 awhite kernel: [12187.138481] hub 3-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Apr 29 12:36:13 awhite kernel: [12187.138488] usb 3-1: USB disconnect, address 2
Apr 29 12:36:13 awhite kernel: [12187.376035] usb 3-1: new low speed USB device using uhci_hcd and address 4
Apr 29 12:36:13 awhite kernel: [12187.549551] usb 3-1: configuration #1 chosen from 1 choice
Apr 29 12:36:13 awhite kernel: [12187.565695] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input7
Apr 29 12:36:13 awhite kernel: [12187.565914] generic-usb 0003:046D:C016.0004: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1/input0
Apr 29 12:36:13 awhite chipcardd[5099]: devicemanager.c: 3373: Changes in hardware list
Apr 29 12:36:14 awhite chipcardd[5099]: devicemanager.c: 3373: Changes in hardware list
Apr 29 12:36:30 awhite gdm[4691]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Apr 29 12:36:30 awhite kernel: [12207.444049] pidgin[5381]: segfault at 9ecf000 ip b7e73253 sp bfd5b740 error 6 in libX11.so.6.2.0[b7e44000+ea000]
Apr 29 12:36:36 awhite bonobo-activation-server (awhite-25342): could not associate with desktop session: Failed to connect to socket /tmp/dbus-h0jhYqREAj: Connection refused
Apr 29 12:36:37 awhite acpid: client 4695[0:0] has disconnected 
Apr 29 12:36:37 awhite acpid: client 4695[0:0] has disconnected 
Apr 29 12:36:37 awhite acpid: client connected from 25408[0:0] 
Apr 29 12:36:38 awhite acpid: client connected from 25408[0:0] 
Apr 29 12:36:51 awhite acpid: client 25408[0:0] has disconnected 
Apr 29 12:36:51 awhite acpid: client 25408[0:0] has disconnected 
Apr 29 12:36:51 awhite acpid: client connected from 25427[0:0] 
Apr 29 12:36:52 awhite acpid: client connected from 25427[0:0] 
Apr 29 12:37:19 awhite pulseaudio[25627]: pid.c: Stale PID file, overwriting.
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: Could not parse desktop file /home/awhite/.config/autostart/beryl-manager.desktop: Key file does not have key 'Type' 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: could not read /home/awhite/.config/autostart/beryl-manager.desktop 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: Could not parse desktop file /home/awhite/.config/autostart/evolution-alarm-notify.desktop: Key file does not have key 'Type' 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: could not read /home/awhite/.config/autostart/evolution-alarm-notify.desktop 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: Could not parse desktop file /home/awhite/.config/autostart/beagle-search-autostart.desktop: Key file does not have key 'Type' 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: could not read /home/awhite/.config/autostart/beagle-search-autostart.desktop 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: Could not parse desktop file /home/awhite/.config/autostart/beagled-autostart.desktop: Key file does not have key 'Type' 
Apr 29 12:37:23 awhite x-session-manager[25463]: WARNING: could not read /home/awhite/.config/autostart/beagled-autostart.desktop 
Apr 29 12:37:32 awhite pulseaudio[25627]: module-x11-xsmp.c: X11 session manager not running.
Apr 29 12:37:32 awhite pulseaudio[25627]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Apr 29 12:37:33 awhite NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Apr 29 12:37:52 awhite last message repeated 3 times
Apr 29 12:39:02 awhite /USR/SBIN/CRON[26097]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Apr 29 12:39:02 awhite postfix/pickup[25133]: E34C5555CA: uid=0 from=<root>
Apr 29 12:39:02 awhite postfix/cleanup[26013]: E34C5555CA: message-id=<20090429193901.E34C5555CA@awhite.its.calpoly.edu>
Apr 29 12:39:02 awhite postfix/qmgr[4444]: E34C5555CA: from=<root@awhite.its.calpoly.edu>, size=709, nrcpt=1 (queue active)
Apr 29 12:39:02 awhite postfix/local[26177]: E34C5555CA: to=<awhite@awhite.its.calpoly.edu>, orig_to=<root>, relay=local, delay=539, delays=539/0.1/0/0.04, dsn=2.0.0, status=sent (delivered to mailbox)
Apr 29 12:39:02 awhite postfix/qmgr[4444]: E34C5555CA: removed
Apr 29 12:39:39 awhite NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Apr 29 12:40:01 awhite /USR/SBIN/CRON[26382]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Apr 29 12:40:10 awhite acpid: client 25427[0:0] has disconnected 
Apr 29 12:40:10 awhite acpid: client 25427[0:0] has disconnected

In user.log
> Apr 29 12:36:36 awhite bonobo-activation-server (awhite-25342): could not associate with desktop session: Failed to connect to socket /tmp/dbus-h0jhYqREAj: Connection refused
Apr 29 12:37:19 awhite pulseaudio[25627]: pid.c: Stale PID file, overwriting.
Apr 29 12:37:32 awhite pulseaudio[25627]: module-x11-xsmp.c: X11 session manager not running.
Apr 29 12:37:32 awhite pulseaudio[25627]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

I've never had anything like this happen with Ubuntu.  I've been running Jaunty since the day it was released.  This is the first time I've seen this issue.

Should I report this to the Pidgin team or make a bug report?  Has anyone seen something like this?

-Arlo

---

### Post by maphilli14 on 2009-05-01
Me too?!

[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/362789](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/362789) Is the only thing I've found.  I suspect something has been going wrong w/ my pidgin since the early beta days.

Mike

---

