---
title: "keyboard does not respond + shutdown hangs"
date: 2006-08-24
forum: Desktop Environments
---

### Post by martinz on 2006-08-24
[FONT="Tahoma"]Hello,


Context:
I am running Dapper 6.06, like most of us...
Xgl and compiz are (or were) running correctly.
Still trying to make my wireless working, amongst other thing that are not working yet.

Problem:
1. Startup : the keyboard doesn't respond on the logon screen. Therefore I am not able to login and check what else is not working.

2. Shutdown : immediately switches to a black screen with cursor on top left.
The only way to shutdown is the hard way...

Suspected error sources:
acpi, xorg,...

Any help, someone?
Thanks,

Martin
[/FONT]

---

### Post by martinz on 2006-08-24
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by martinz on 2006-08-24
Note that my xorg.conf didn't change since it was working.:confused:

---

### Post by martinz on 2006-08-25
[SIZE="1"][COLOR="Silver"]I'm so happy that so many experienced users helped me with my problem, I'll format my disk and come back to WINDOWS.
see you.:evil:[/COLOR][/SIZE]

---

### Post by Uluen on 2006-08-25
> **martinz said:**
> I'm so happy that so many experienced users helped me with my problem, I'll format my disk and come back to WINDOWS.

see you.:evil:Have fun :rolleyes: 

Did you try booting with no X and check the usual logs?

---

### Post by martinz on 2006-08-25
Thank you for replying, Uluen.

I am an idiot*. No I didn't check the logs...
I'll do as soon as at home...

*true

I am a IT professional* who do not think about checking the logs. I 'm going to hang myself...

*you guessed, Microsoft environments...

[SIZE="2"][COLOR="Magenta"]**MY APPOLOGISE TO EVERYONE. MEA MAXIMA CULPA**[/COLOR][/SIZE]

Martin

---

### Post by Uluen on 2006-08-25
Not thinking about the system logs is natural if you're been using Windows for a while. I mean, how often does the event viewer give any helpful clues after all? ;)

GL Martin, let us know how it goes?

---

### Post by martinz on 2006-08-25
Thanks. Very much. I mean it.

Windows event log, like linux's, does just tell you where the error is... up to you to dig further. (have you ever had a look to [www.eventid.net](www.eventid.net) ?)

Now, here we are:

/var/log/debug :
this is the last line (before I stress the power button;-))
> [17179611.032000] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !


daemon.log:
> Aug 25 19:51:10 localhost NetworkManager: <WARNING>^I main (): nm_data_new: Setting up dbus filter
Aug 25 19:51:11 localhost hcid[4666]: Bluetooth HCI daemon
Aug 25 19:51:11 localhost hcid[4666]: Can't get system message bus name: Connection ":1.4" is not allowed to own the service "org.bluez" due to security policies in the configuration file


Kernel.log
> ...
Aug 25 19:50:58 localhost kernel: No module symbols loaded - kernel modules not enabled.
...
Aug 25 19:50:58 localhost kernel: [17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
...
Aug 25 19:50:58 localhost kernel: [17179570.004000] ACPI: Looking for DSDT ... not found!
...
Aug 25 19:50:58 localhost kernel: [17179571.092000] input: AT Translated Set 2 keyboard as /class/input/input0 [COLOR="Red"]Just to show there is something about the keyboard[/COLOR]
...
Aug 25 19:50:58 localhost kernel: [17179586.192000] ZD1211 802.11b/g USB WLAN driver v20050315 loaded
Aug 25 19:50:58 localhost kernel: [17179586.192000] (c) Willig, Yang, Zviskov et al.
Aug 25 19:50:58 localhost kernel: [17179586.192000] [http://zd1211.sourceforge.net/](http://zd1211.sourceforge.net/)
Aug 25 19:50:58 localhost kernel: [17179586.192000] zd1211 device (0x0b05,0x170c) found.
Aug 25 19:50:58 localhost kernel: [17179586.192000] zd1211 device on USB 2.0 Host
Aug 25 19:50:58 localhost kernel: [17179586.192000] Firmware Version = 4802
Aug 25 19:50:58 localhost kernel: [17179586.192000] bulk out: wMaxPacketSize = 200
Aug 25 19:50:58 localhost kernel: [17179586.192000] bulk in: wMaxPacketSize = 200
Aug 25 19:50:58 localhost kernel: [17179586.192000] interrupt in: wMaxPacketSize = 40
Aug 25 19:50:58 localhost kernel: [17179586.192000] interrupt in: int_interval = 1
Aug 25 19:50:58 localhost kernel: [17179586.192000] interrupt out: wMaxPacketSize = 40
Aug 25 19:50:58 localhost kernel: [17179586.192000] EEPROM Version = 4330
Aug 25 19:50:58 localhost kernel: [17179586.204000] USB Download Boot code success
Aug 25 19:50:58 localhost kernel: [17179586.204000] Downloaded firmware.
Aug 25 19:50:58 localhost kernel: [17179586.232000] hw_random: RNG not detected
...
Aug 25 19:50:58 localhost kernel: [17179602.540000] Asus Laptop ACPI Extras version 0.29
Aug 25 19:50:58 localhost kernel: [17179602.540000]   Error calling BSTS
Aug 25 19:50:58 localhost kernel: [17179602.540000]   A4S model detected, unsupported, trying default values, supply the developers with your DSDT
...
Aug 25 19:51:04 localhost kernel: [17179610.372000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 25 19:51:05 localhost kernel: [17179610.372000] apm: overridden by ACPI.
Aug 25 19:51:05 localhost kernel: [17179611.032000] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
...
Aug 25 19:51:11 localhost kernel: [17179616.760000] Bluetooth: Core ver 2.8
Aug 25 19:51:11 localhost kernel: [17179616.760000] NET: Registered protocol family 31
Aug 25 19:51:11 localhost kernel: [17179616.760000] Bluetooth: HCI device and connection manager initialized
Aug 25 19:51:11 localhost kernel: [17179616.760000] Bluetooth: HCI socket layer initialized
Aug 25 19:51:11 localhost kernel: [17179616.860000] Bluetooth: L2CAP ver 2.8
Aug 25 19:51:11 localhost kernel: [17179616.860000] Bluetooth: L2CAP socket layer initialized
Aug 25 19:51:11 localhost kernel: [17179616.908000] Bluetooth: RFCOMM socket layer initialized
Aug 25 19:51:11 localhost kernel: [17179616.908000] Bluetooth: RFCOMM TTY layer initialized
Aug 25 19:51:11 localhost kernel: [17179616.908000] Bluetooth: RFCOMM ver 1.7
Aug 25 19:51:11 localhost kernel: [17179617.360000] Unable to handle kernel NULL pointer dereference at virtual address 00000008
...
Aug 25 19:51:12 localhost kernel: [17179617.800000]  [kthread+147/160] kthread+0x93/0xa0
Aug 25 19:51:12 localhost kernel: [17179617.800000]  [kthread+0/160] kthread+0x0/0xa0
Aug 25 19:51:12 localhost kernel: [17179617.800000]  [kernel_thread_helper+5/16] kernel_thread_helper+0x5/0x10
Aug 25 19:51:12 localhost kernel: [17179617.800000] Code: 33 69 ff ff 8d 76 00 56 53 8a 4c 24 0c a1 7c 07 a8 f8 8b 80 30 01 00 00 9c 5b fa ba 00 e0 ff ff 21 e2 ff 42 14 8b 80 64 0e 00 00 <8b> 40 08 25 ff ff 00 00 81 e1 ff 00 00 00 41 39 c8 0f 9d c0 89 
Aug 25 19:51:12 localhost kernel: [17179617.800000]  <6>note: events/0[4] exited with preempt_count 1
Aug 25 19:51:57 localhost kernel: [17179663.140000] NET: Registered protocol family 17

Acpid
> [Fri Aug 25 19:50:57 2006] starting up
[Fri Aug 25 19:50:57 2006] 54 rules loaded
[Fri Aug 25 19:51:05 2006] client connected from 4450[108:108]
[Fri Aug 25 19:51:05 2006] 1 client rule loaded
[Fri Aug 25 19:55:07 2006] received event "button/power PWRF 00000080 00000001"
[Fri Aug 25 19:55:07 2006] notifying client 4450[108:108]
[Fri Aug 25 19:55:07 2006] executing action "/etc/acpi/powerbtn.sh"
[Fri Aug 25 19:55:07 2006] BEGIN HANDLER MESSAGES

Messages
> ...
Aug 25 19:51:12 localhost kernel: [17179617.800000]  [kernel_thread_helper+5/16] kernel_thread_helper+0x5/0x10
Aug 25 19:51:12 localhost kernel: [17179617.800000] Code: 33 69 ff ff 8d 76 00 56 53 8a 4c 24 0c a1 7c 07 a8 f8 8b 80 30 01 00 00 9c 5b fa ba 00 e0 ff ff 21 e2 ff 42 14 8b 80 64 0e 00 00 <8b> 40 08 25 ff ff 00 00 81 e1 ff 00 00 00 41 39 c8 0f 9d c0 89 
Aug 25 19:51:12 localhost kernel: [17179617.800000]  <6>note: events/0[4] exited with preempt_count 1
Aug 25 19:51:57 localhost kernel: [17179663.140000] NET: Registered protocol family 17


Syslog
> ...
Aug 25 19:51:11 localhost kernel: [17179617.360000]  [wireless_process_ioctl+1562/1936] wireless_process_ioctl+0x61a/0x790
Aug 25 19:51:11 localhost kernel: [17179617.360000]  [pg0+946019424/1069368320] zd1205wext_siwscan+0x0/0x70 [zd1211]
Aug 25 19:51:11 localhost kernel: [17179617.360000]  [dev_ioctl+603/688] dev_ioctl+0x25b/0x2b0
Aug 25 19:51:11 localhost kernel: [17179617.360000]  [do_ioctl+34/128] do_ioctl+0x22/0x80
Aug 25 19:51:11 localhost kernel: [17179617.360000]  [vfs_ioctl+81/496] vfs_ioctl+0x51/0x1f0
Aug 25 19:51:11 localhost kernel: [17179617.360000]  [sys_ioctl+93/144] sys_ioctl+0x5d/0x90
Aug 25 19:51:11 localhost kernel: [17179617.360000]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
Aug 25 19:51:11 localhost kernel: [17179617.360000] Code: 33 69 ff ff 8d 76 00 56 53 8a 4c 24 0c a1 7c 07 a8 f8 8b 80 30 01 00 00 9c 5b fa ba 00 e0 ff ff 21 e2 ff 42 14 8b 80 64 0e 00 00 <8b> 40 08 25 ff ff 00 00 81 e1 ff 00 00 00 41 39 c8 0f 9d c0 89 
Aug 25 19:51:11 localhost kernel: [17179617.360000]  <6>note: iwlist[4736] exited with preempt_count 1
Aug 25 19:51:12 localhost kernel: [17179617.800000] Unable to handle kernel NULL pointer dereference at virtual address 00000008
...
Aug 25 19:51:12 localhost kernel: [17179617.800000]  <6>note: events/0[4] exited with preempt_count 1
Aug 25 19:51:56 localhost NetworkManager: <information>^IDevice 'eth0' DHCP transaction took too long (>45s), stopping it. 
Aug 25 19:51:57 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Aug 25 19:51:57 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Aug 25 19:51:57 localhost NetworkManager: <information>^INo DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Aug 25 19:51:57 localhost kernel: [17179663.140000] NET: Registered protocol family 17
Aug 25 19:55:07 localhost shutdown[4849]: shutting down for system halt
Aug 25 19:55:07 localhost shutdown[4849]: shutting down for system halt


User.log
A> ug 25 19:51:10 localhost dhcdbd: Started up.
Aug 25 19:51:10 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug 25 19:51:10 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug 25 19:55:07 localhost shutdown[4849]: shutting down for system halt


Part of the errors seems coming from the network conf...

Any idea?

Thanks

---

### Post by martinz on 2006-08-27
I just went for a fresh instal...:(

---

### Post by lucho64 on 2006-08-29
I have problems with bluetooth hanging at shutdown as well. I think that it's interfering with my USB devices when more than one  user is logged in different screens. Is your keyboard a USB one? I've decided to disable bluetooth for now (since I don't have bluetooth devices anyway) by:
[FONT="Courier New"]**chmod -x /etc/init.d/bluez-utils**[/FONT]
and adding the lines:
[FONT="Courier New"][B]alias bluetooth off
alias rfcomm off
alias l2cap[/B][/FONT]
to my /etc/modules.d/bad_list. I don't know if it's going to work, the problem is unfortunately not easy to reproduce :confused:

---

