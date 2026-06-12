---
title: "1 minute boot time. Why?"
date: 2009-06-01
forum: Desktop Environments
---

### Post by MadnessRed on 2009-06-01
I fealt like timing my boot time and it came out at almost exactly 1 minute.

Time - Event
00 - Comp turned on
09 - BIOS finished
11 - GRUB started
15 - (Ubuntu selected)
23 - Ubuntu boot screen appears (8 seconds later!!)
37 - Ubuntu boot screen shows as finished
     Now debug stuff comes up, I get what looks like a startup debug output and also after that I get this on screen
> 113-B34001-X14 RV670 GDDR3_16M x32 256b

64 - Logni screen appears.

So basically, 9 seconds bios, 2 seconds grub, 4 seconds before i get round to choosing, 8 seconds while ubuntu boot screen loads, 14 seconds ubuntu boot screen, 27 seconds of random debug stuff.

I can cope with all of that execpt, the 27 seconds of random debug. Thats pretty much 1/2 my boot time.

The debug started after I install the ATi driver. And RV670 is my graphics card (2 x ATi HD3850 512mb) (1 GeCube, 1 Force3D)
Any one have any ideas how I can remove this debug section.

I am gonna try and film the debug bit and ill upload it. There is too much to write down.

---

### Post by mcduck on 2009-06-01
> **MadnessRed said:**
> 
The debug started after I install the ATi driver.

You pretty much answered your own question yourself.. ;)

Either your driver isn't the correct one, it wasn't installed correctly or it's not configured correctly.

---

### Post by MadnessRed on 2009-06-01
> **mcduck said:**
> You pretty much answered your own question yourself.. ;)

Either your driver isn't the correct one, it wasn't installed correctly or it's not configured correctly.

everything works fine after that part. how can I check weather it is correctly configured?

---

### Post by MadnessRed on 2009-06-12
bump, and here is my log file viewer for that part of startup

```
Jun  7 17:02:41 Anthony-PC kernel: [    9.822311] EXT4 FS on sda1, internal journal on sda1:8
Jun  7 17:02:41 Anthony-PC kernel: [   10.755503] type=1505 audit(1244390560.683:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2075
Jun  7 17:02:41 Anthony-PC kernel: [   10.808252] type=1505 audit(1244390560.739:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2079
Jun  7 17:02:41 Anthony-PC kernel: [   10.808448] type=1505 audit(1244390560.739:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2079
Jun  7 17:02:41 Anthony-PC kernel: [   10.808501] type=1505 audit(1244390560.739:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2079
Jun  7 17:02:41 Anthony-PC kernel: [   10.808547] type=1505 audit(1244390560.739:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2079
Jun  7 17:02:41 Anthony-PC kernel: [   10.958057] type=1505 audit(1244390560.887:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2084
Jun  7 17:02:41 Anthony-PC kernel: [   10.958334] type=1505 audit(1244390560.887:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2084
Jun  7 17:02:41 Anthony-PC kernel: [   10.991029] type=1505 audit(1244390560.919:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2088
Jun  7 17:02:43 Anthony-PC kernel: [   13.074525] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun  7 17:02:44 Anthony-PC kernel: [   14.091297] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun  7 17:02:44 Anthony-PC kernel: [   14.091301] Bluetooth: BNEP filters: protocol multicast
Jun  7 17:02:44 Anthony-PC kernel: [   14.115516] Bridge firewalling registered
Jun  7 17:02:50 Anthony-PC kernel: [   20.069424] eth0: link down
Jun  7 17:02:50 Anthony-PC kernel: [   20.069602] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  7 17:02:50 Anthony-PC kernel: [   20.092670] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  7 17:02:54 Anthony-PC kernel: [   24.922813] [fglrx] Firegl kernel thread PID: 3218
Jun  7 17:02:54 Anthony-PC kernel: [   24.946975] [fglrx] Gart USWC size:942 M.
Jun  7 17:02:54 Anthony-PC kernel: [   24.946979] [fglrx] Gart cacheable size:60 M.
Jun  7 17:02:54 Anthony-PC kernel: [   24.946987] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jun  7 17:02:54 Anthony-PC kernel: [   24.946989] [fglrx] Reserved FB block: Unshared offset:fdff000, size:201000 
Jun  7 17:02:54 Anthony-PC kernel: [   24.946992] [fglrx] Reserved FB block: Unshared offset:1fffc000, size:4000 
Jun  7 17:03:09 Anthony-PC kernel: [   39.555531] [fglrx] Firegl kernel thread PID: 3254
Jun  7 17:03:09 Anthony-PC kernel: [   39.564928] [fglrx] Gart USWC size:942 M.
Jun  7 17:03:09 Anthony-PC kernel: [   39.564932] [fglrx] Gart cacheable size:60 M.
Jun  7 17:03:09 Anthony-PC kernel: [   39.564940] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jun  7 17:03:09 Anthony-PC kernel: [   39.564943] [fglrx] Reserved FB block: Unshared offset:fdff000, size:201000 
Jun  7 17:03:09 Anthony-PC kernel: [   39.564946] [fglrx] Reserved FB block: Unshared offset:1fffc000, size:4000 
```

---

