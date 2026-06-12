---
title: "gdm crashes when click on desktop"
date: 2008-05-04
forum: Desktop Environments
---

### Post by cet' on 2008-05-04
If I click on the desktop gdm crashes.
I have a dual screen ati big desktop setup and it doesn't happen every time the desktop is clicked. I have 8.04 with the latest ati driver 8.47.3 for a X1300/X1550 Series card.

it also is more noticeable when clicking on the display number 1 desktop. 

it goes to a black then i have to start gdm again sometimes i have to first restart it or just reboot.

Has anyone seen this problem before or what log files should i be looking at to understand whats going on?


xorg.conf
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "screen0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "monitor0"
EndSection

Section "Monitor"
	Identifier   "monitor1"
EndSection

Section "Device"
	Identifier  "device0"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1280x1024+1280x1024,0x0+0x0"
EndSection

Section "Device"
	Identifier  "device1"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "screen0"
	Device     "device0"
	Monitor    "monitor0"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
EndSection

---

### Post by Sa1nt_Linux_n00b on 2008-08-26
I am also having the same problem and I too have dual monitors but disabled the second to try to trouble shoot the issue. I have found out that the crash will typically occur when I click the right side of the desktop.

I have attached where I think the problem is... as you can tell with my name I am completely new so I have no idea what this means.  Any help is appreciated.

Aug 26 00:13:10 supernatural -- MARK --
Aug 26 00:17:01 supernatural /USR/SBIN/CRON[7475]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
**Aug 26 00:29:25 supernatural kernel: [ 2237.486507] compiz.real[6790]: segfault at 2a466 rip 40fee0 rsp 7fff580f8fb0 error 4**
**Aug 26 00:29:25 supernatural gdm[6563]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0**
Aug 26 00:29:30 supernatural kernel: [ 2241.803772] [fglrx] PCIe has already been initialized. Reinitializing ...
Aug 26 00:29:30 supernatural kernel: [ 2241.810131] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
Aug 26 00:29:30 supernatural kernel: [ 2241.810138] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Aug 26 00:29:30 supernatural kernel: [ 2241.810141] [fglrx] Reserve Block - 2 offset =  0X1ffff000 length = 0X1000
Aug 26 00:29:30 supernatural kernel: [ 2241.810143] [fglrx] Reserve Block - 3 offset =  0Xffc0000 length = 0X40000
Aug 26 00:29:30 supernatural kernel: [ 2241.849744] [fglrx] interrupt source 20008000 successfully enabled
Aug 26 00:29:30 supernatural kernel: [ 2241.849751] [fglrx] enable ID = 0x00000008
Aug 26 00:29:30 supernatural kernel: [ 2241.849758] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Aug 26 00:29:30 supernatural kernel: [ 2241.849803] [fglrx] interrupt source 10000000 successfully enabled
Aug 26 00:29:30 supernatural kernel: [ 2241.849805] [fglrx] enable ID = 0x00000009
Aug 26 00:29:30 supernatural kernel: [ 2241.849809] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Aug 26 00:29:37 supernatural pulseaudio[7759]: pid.c: Stale PID file, overwriting.
Aug 26 00:29:37 supernatural pulseaudio[7759]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 26 00:29:37 supernatural pulseaudio[7759]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 26 00:29:37 supernatural hcid[5883]: Default passkey agent (:1.66, /org/bluez/passkey) registered
Aug 26 00:29:37 supernatural hcid[5883]: Default authorization agent (:1.66, /org/bluez/auth) registered
Aug 26 00:29:38 supernatural NetworkManager: <info>  Updating allowed wireless network lists.
Aug 26 00:29:38 supernatural NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

---

### Post by treyphan on 2008-09-11
I am having the same problem when I click more then 2 or 3 times.

---

### Post by Predator106 on 2008-09-11
Well it appears that Compiz is segfaulting and thus crashing GDM. I never had Compiz crash before, so this is about as much as I can help you with. Do you have any engines attached to compiz? That COULD be the problem, I don't know.

---

### Post by treyphan on 2008-09-11
Yes I narrowed it down to a compiz/ATI problem. I just can't figure out what it is that is causing the issue. I will continue to look into it.

---

### Post by mr51m0n on 2008-10-09
Hello

Any News here?

I also have a dual screen setup with ATI/Compiz.

cheers

---

### Post by treyphan on 2008-10-09
I'm still trying to correct the issue. Ironically, the same thing happens in fedora when you turn on desktop effects. Here is an interesting side bar to that "in Fedora only" if you log in as root and turn on desktop effects, you can click until the cows come home and no crash. I tested this in ubuntu and sadly even logged on as root, it crashes. ATI has got to do a better job with driver support!

---

### Post by mr51m0n on 2008-10-09
Okay. Please tell me if/how i can help you.

---

### Post by treyphan on 2008-10-09
what video card do you have in your box?

---

### Post by mr51m0n on 2008-10-10
Hey

Have a:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400 (prog-if 00 [VGA controller])
	Subsystem: Lenovo Thinkpad T60 model 2007
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at ee100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at ee120000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Legacy Endpoint IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-


It's a T60 2007 CTO, using Ubuntu 8.04 and all Software up to date.

[Update]

fund this in my syslog now:


Oct  9 16:48:27 STI-L07009 gdm[3603]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Oct  9 16:48:30 STI-L07009 kernel: [178879.651367] [fglrx] PCIe has already been initialized. Reinitializing ...
Oct  9 16:48:30 STI-L07009 kernel: [178879.672650] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
Oct  9 16:48:30 STI-L07009 kernel: [178879.672655] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Oct  9 16:48:30 STI-L07009 kernel: [178879.672659] [fglrx] Reserve Block - 2 offset =  0X7fbb000 length = 0X40000
Oct  9 16:48:30 STI-L07009 kernel: [178879.797700] [fglrx] interrupt source 10000000 successfully enabled
Oct  9 16:48:30 STI-L07009 kernel: [178879.797705] [fglrx] enable ID = 0x00000008
Oct  9 16:48:30 STI-L07009 kernel: [178879.797711] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000

[Update 2]

and sometimes, it looks like that:

Oct  9 16:49:14 STI-L07009 kernel: [178923.299249] compiz.real[4718]: segfault at 00000018 eip 08055a6d esp bfd98210 error 4
Oct  9 16:49:14 STI-L07009 gdm[4500]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Oct  9 16:49:17 STI-L07009 kernel: [178926.069484] [fglrx] PCIe has already been initialized. Reinitializing ...
Oct  9 16:49:17 STI-L07009 kernel: [178926.090451] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
Oct  9 16:49:17 STI-L07009 kernel: [178926.090456] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Oct  9 16:49:17 STI-L07009 kernel: [178926.090458] [fglrx] Reserve Block - 2 offset =  0X7fbb000 length = 0X40000
Oct  9 16:49:17 STI-L07009 kernel: [178926.214098] [fglrx] interrupt source 10000000 successfully enabled
Oct  9 16:49:17 STI-L07009 kernel: [178926.214104] [fglrx] enable ID = 0x00000008
Oct  9 16:49:17 STI-L07009 kernel: [178926.214112] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Oct  9 16:49:26 STI-L07009 kernel: [178934.985286] [fglrx] interrupt source 10000000 successfully disabled!
Oct  9 16:49:26 STI-L07009 kernel: [178934.985291] [fglrx] enable ID = 0x00000000
Oct  9 16:49:26 STI-L07009 kernel: [178934.985293] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000008
Oct  9 16:49:26 STI-L07009 init: tty4 main process (5007) killed by TERM signal
Oct  9 16:49:26 STI-L07009 init: tty5 main process (5008) killed by TERM signal
Oct  9 16:49:26 STI-L07009 init: tty2 main process (5010) killed by TERM signal
Oct  9 16:49:26 STI-L07009 init: tty3 main process (5011) killed by TERM signal
Oct  9 16:49:26 STI-L07009 init: tty6 main process (5012) killed by TERM signal
Oct  9 16:49:26 STI-L07009 init: tty1 main process (27656) killed by TERM signal
Oct  9 16:49:27 STI-L07009 gdm[5105]: CRITICAL: gdm_connection_close: assertion `conn != NULL' failed
Oct  9 16:49:27 STI-L07009 last message repeated 2 times
Oct  9 16:49:27 STI-L07009 gdm[5105]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed
Oct  9 16:49:27 STI-L07009 gdm[5105]: WARNING: Request for invalid configuration key xdmcp/PingIntervalSeconds=15
Oct  9 16:49:27 STI-L07009 gdm[5105]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed
Oct  9 16:49:27 STI-L07009 gdm[5105]: WARNING: Request for invalid configuration key xdmcp/PingIntervalSeconds=15
Oct  9 16:49:28 STI-L07009 gdm[5105]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed
Oct  9 16:49:28 STI-L07009 gdm[5105]: WARNING: Request for invalid configuration key daemon/ServAuthDir=/var/lib/gdm
Oct  9 16:49:28 STI-L07009 gdm[5105]: WARNING: gdm_slave_send: Can't open fifo!
Oct  9 16:49:28 STI-L07009 gdm[5105]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed
Oct  9 16:49:28 STI-L07009 gdm[5105]: WARNING: Request for invalid configuration key daemon/ServAuthDir=/var/lib/gdm
Oct  9 16:49:28 STI-L07009 gdm[5105]: WARNING: gdm_auth_secure_display: Cannot safely open
Oct  9 16:49:28 STI-L07009 gdm[5105]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed
Oct  9 16:49:28 STI-L07009 gdm[5105]: WARNING: Request for invalid configuration key daemon/ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh
Oct  9 16:49:28 STI-L07009 gdm[5105]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed
Oct  9 16:49:28 STI-L07009 gdm[5105]: WARNING: Request for invalid configuration key daemon/ConsoleNotify=true

---

### Post by bernd.juchems on 2009-03-03
Hi there ...

I have the same problem:
- ATI Radeon X1300/X1550 Series
- Dual Monitor Setup
- proprietary ATI Catalyst Driver, Version 8.54.3

From Syslog:

Mar  3 11:52:39 ju-brutus nullmailer[5612]: Starting delivery: protocol: smtp host: mail. file: 1234497601.23691
Mar  3 11:52:39 ju-brutus nullmailer[5529]: smtp: Failed: Connect failed
Mar  3 11:52:39 ju-brutus nullmailer[5612]: Sending failed:  Host not found
Mar  3 11:52:39 ju-brutus nullmailer[5612]: Delivery complete, 25 message(s) remain.
Mar  3 11:52:40 ju-brutus gdm[2482]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  (eth0): device state change: 8 -> 3 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  (eth0): deactivating device (reason: 38). 
Mar  3 11:52:40 ju-brutus NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Mar  3 11:52:40 ju-brutus avahi-daemon[4961]: Withdrawing address record for 192.168.0.86 on eth0.
Mar  3 11:52:40 ju-brutus avahi-daemon[4961]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.86.
Mar  3 11:52:40 ju-brutus avahi-daemon[4961]: Interface eth0.IPv4 no longer relevant for mDNS.
Mar  3 11:52:40 ju-brutus NetworkManager: <info>  dhclient started with pid 5578 


I formerly had Desktop Effects turned on, grudgingly I have them now turned of. Hopefully, that problem will not return.

I will monitor this thread, hoping for someone coming out for a solution ...


P.S.: I've searched other forums for this; seemingly this is not an ATI problem and comes on Intel and nVidia cards, too.

---

