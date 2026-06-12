---
title: "unregister device problem: hard reset"
date: 2006-08-26
forum: Desktop Environments
---

### Post by mailmaldi on 2006-08-26
```
root@sprint-haven:/home/milind# uname -r
2.6.15-26-386

```
is the kernel i am using.

i use rp-pppoe to connect to my isp for internet access...

everything was working fine till i got up in the morning & switched on the monitor to see this following message on my already open terminals

```
unregister_netdevice: waiting for ppp0 to become free. Usage count = 1
```

i could not start any more terminals or any other system application & i tried to reboot by switching to console & pressing ctrl + alt + del.

but i got the same message in an infinite loop & finally had to hard reset.

i used to get the same messages when i used to try and reboot without bringing down the active connections

---

### Post by v1ct0r on 2006-08-26
Well...
[http://kerneltrap.org/node/6703](http://kerneltrap.org/node/6703)
[http://www.gatago.com/linux/kernel/15466135.html](http://www.gatago.com/linux/kernel/15466135.html)

---

### Post by mailmaldi on 2006-08-26
thanks but i am a bit of a newbie but till as far as i was able to undestand, neither helps me...

once the message occurs..I CAN DO NOTHING....i cant run any commands nor can i execute another shell...

---

### Post by Samanbaia_eng on 2006-08-30
Hi,

Don't feel alone, I have the same problem :

Myself, I use a hp nx6110 laptop with a wifi connection (centrino).

After "will now halt", a command line show up and says (and repeat):

```
[17180xxx.xxxxxx] unregister_netdevice: waiting for eth1 to become free Usage count: 1

```

This text repeats itself: the only changes are the xxx.xxxxxx : once it was  17180484.000000.

But laptop doesn't stop.

I am using a lan connection on this wifi connection (through a router).

If I stop my laptop before starting a session, this doesn't happen. But if  I put the computer in hibernation (or with the screen saver), I "loose" my wifi connection. Once, I haven't even been able to open a terminal.

This happened 5 days ago after ubuntu update with some new kernel stuff (last Friday).

Every time it's happened, I have to do a hard reset, but I don't think it is a good thing.

Someone can help me (us)?

Thanks.

Nicolas

---

### Post by mailmaldi on 2006-08-30
i have the same problem even with the old 2.6.15-23 kernel...

additionally i have random freeze of the entire system for no reason/cause...

i have a intel 915GAV motherboard with seagate SATA..
i ve tested my hardware components-ram etc & theyre fine

---

### Post by Samanbaia_eng on 2006-08-30
My kernel is 2.6.15-26-386 and here is my configuration:
```
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
```

My configuration worked fine until friday (I did some updates on thursday.)

Once, my system partially freezed (lose my wlan connection, no more terminal) after a screensaver, and I had to hard reset.

I hope in a kernel update, or in the new ubuntu version of october. But this mean to reinstall everything.

Nicolas

---

### Post by chris86wm on 2006-08-31
Same problem here. I have tried using kernel 2.6.15-26-386 and 2.6.15-23-386 without luck.

When I restart/shutdown I get:
unregister_netdevice: waiting for eth1 to become free. Usage count = 1

Someone needs to get this fixed

---

### Post by mailmaldi on 2006-08-31
update:

1. the random freeze is occuring even on my vmware ubuntu...

2. the random freeze is also occuring on a friends intel 845 motherboard

---

### Post by kaffekopp on 2006-09-12
I've got this same problem on my HP laptop DV5000 

Anyone found a fix for this yet?

---

### Post by kaffekopp on 2006-09-16
To be more specific, my laptop started freezing on shutdown after I isntalled vmware server console on it. On the shutdown splash screen, it would stop at the bit about "usplash" something (sorry, can't remember exactly how it goes), before the screen would switch to text mode and I'd get this message: 
```
unregister_netdevice: waiting for vmnet1 to become free. Usage count = 1
```

After a bit of fiddling around, I found out I could disable the vmnet1 device (I'm a bit of a noob, so I don't really know what it's there for... I use eth0 or wlan0 for net connection normally, so I guess it's got to do with vmware) by typing the following in a terminal:
```
sudo ifconfig vmnet1 down
```

It seems this enabled me to shut down without trouble afterwards. Anyway, to avoid trouble shutting down, I've stopped vmware from loading automatically on boot (used the System->Administration->Boot Up Manager menu and untagged "Free Virtual Machine Player from VMware"). 

So, I got rid of the shutdown problem, but can't run VMware. Not an optimal solution, in other words. 

Still interested to hear if anyone knows how to fix this problem!

---

### Post by CoolkcaH on 2006-10-27
I have the same problem when I try to shutdown or hibernate I get the unregister netdevice error and have to hardreset the laptop.
It happens with a Intel ipw2200 on a Fujitsu P7010.

Even after I upgraded to Edgy it's still the same...

---

### Post by Samanbaia_eng on 2006-10-28
I may have found the beginning of a solution:

my ipw2200 (centrino) driver is unstable : version 1.1 (instead of stable version : 1.0 or 1.2)
I should update it with the compilation of a new kernel, or update to edgy.

Another solution is to stop your wireless interface before shuting down :
```
sudo modprobe -r ipw2200

```

The message "unregister..." comes out because ubuntu try to shut down the wireless interface, but is not able to do it.

Anyway, also with a hard reset at this point don't seem to be critical for the hard drive.

Myself I will try to compile a new kernel.

---

### Post by Cactus Sediento on 2006-11-10
Same problem here with pentium M  in Acer Travelmate 4021WLM runging edgy

At shutdown... countless "wating for vmnet1 to become free usage count=1..."

If shutdown is made outside a session, everything OK


Is there a bug reported on this issue?

---

### Post by dannyboy79 on 2006-11-10
all you guys can't even restart X by holding ctrl, alt, backspace a the same time?

---

### Post by Cactus Sediento on 2006-11-10
In my case seems to be resolved...

I had  a "hanged" WMware player runing windows xp. So i started  and shutdown Windows XP in the wmware player.

Now edgy seems to shutdown properly.

---

### Post by Cannaregio on 2006-12-09
```
At shutdown... countless "wating for vmnet1 to become free usage count=1..."
```

Well this does the trick for me:

```
sudo ifconfig vmnet1 down
sudo ifconfig vmnet8 down
```


I -maybe paranoically- wonder if winxp itself, through vmware, opens hidden vmware connections (to microsoft?) _as soon as you have allowed a microsoft check of your winxp copy_, and these are opened by vmware even without powering the virtual winxp on.
I say this because vmware and edgy worked fine with each other and I did never have the
```
"wating for vmnet1 to become free usage count=1..."
```
problem 
_until the day I allowed a microsoft checking_ of my winxp copy inside vmware.

Wonder if somebody else had similar coincidences...

---

### Post by hanzomon4 on 2006-12-19
I have been getting this same problem after installing vmware-server. This is part of the sys.log, I really hope this is fixable.........```
ec 19 00:57:32 localhost NetworkManager: <information>^IGoing to sleep. 
Dec 19 00:57:34 localhost kernel: [17283759.784000] remove_proc_entry: 209/eth0 busy, count=14
Dec 19 00:57:34 localhost kernel: [17283759.784000] bridge-eth0: disabling the bridge
Dec 19 00:57:35 localhost kernel: [17283759.812000] bridge-eth0: down
Dec 19 00:57:36 localhost NetworkManager: <debug info>^I[1166511456.677815] nm_hal_device_removed (): Device removed (hal udi i
s '/org/freedesktop/Hal/devices/net_00_11_11_e2_17_dd'). 
Dec 19 00:57:46 localhost kernel: [17283771.644000] unregister_netdevice: waiting for eth0 to become free. Usage count = 1
Dec 19 00:57:56 localhost gnome-power-manager: (hanzomon4) Resuming computer
Dec 19 00:57:57 localhost NetworkManager: <information>^IWaking up from sleep. 
Dec 19 00:57:57 localhost kernel: [17283781.884000] unregister_netdevice: waiting for eth0 to become free. Usage count = 1
Dec 19 00:58:06 localhost kernel: [17283791.904000] unregister_netdevice: waiting for eth0 to become free. Usage count = 1
Dec 19 00:58:17 localhost kernel: [17283801.988000] unregister_netdevice: waiting for eth0 to become free. Usage count = 1
Dec 19 00:58:27 localhost kernel: [17283812.040000] unregister_netdevice: waiting for eth0 to become free. Usage count = 1
Dec 19 00:58:37 localhost kernel: [17283822.052000] unregister_netdevice: waiting for eth0 to become free. Usage count = 1
Dec 19 00:58:47 localhost kernel: [17283832.308000] unregister_netdevice: waiting for eth0 to become free. Usage count = 1

```

---

### Post by hanzomon4 on 2006-12-21
I fixed my problem:> **hanzomon4 said:**
> I figured it out it wasn't really vmnet that was causing the problem....  Once I got rid of vmnet the problem started happaning with eth0. I checked out the syslog and found that my computer would suspend right before the error message started, I also noticed that after the computer "suspended" It would disable things related to eth0.
[LIST]
[*][COLOR="Red"]**Suspend message**[/COLOR]
[*][COLOR="Green"]**Disabling eth0 message**[/COLOR]
[*][COLOR="Blue"]**Error message**[/COLOR]  
[/LIST]



 ```
[B][COLOR="Red"]Dec 19 00:57:31 localhost gnome-power-manager: (********) Suspending computer b
ecause the system state is idle[/COLOR][/B]
Dec 19 00:57:32 localhost NetworkManager: <information>^IGoing to sleep. 
[B][COLOR="Green"]Dec 19 00:57:34 localhost kernel: [17283759.784000] remove_proc_entry: 209/eth0 
busy, count=14
Dec 19 00:57:34 localhost kernel: [17283759.784000] bridge-eth0: disabling the b
ridge
Dec 19 00:57:35 localhost kernel: [17283759.812000] bridge-eth0: down
Dec 19 00:57:36 localhost NetworkManager: <debug info>^I[1166511456.677815] nm_h
al_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/n
et_00_11_11_e2_17_dd').[/COLOR][/B]
[B][COLOR="Blue"]Dec 19 00:57:46 localhost kernel: [17283771.644000] unregister_netdevice: waitin
g for eth0 to become free. Usage count = 1[/COLOR][/B]
Dec 19 00:57:56 localhost gnome-power-manager: (*******) Resuming computer
Dec 19 00:57:57 localhost NetworkManager: <information>^IWaking up from sleep. 
Dec 19 00:57:57 localhost kernel: [17283781.884000] unregister_netdevice: waitin
g for eth0 to become free. Usage count = 1

```

I changed the power-management settings to stop it from suspending and that fixed the problem.

---

### Post by Repley on 2008-06-26
> **hanzomon4 said:**
> 

[...]

I changed the power-management settings to stop it from suspending and that fixed the problem.

hi, i have the same problem, can you explain what must i do to fix? 
In gnome-power-preferences i don't have anything about network interface, but only settings to turn off the screen or similar
thank you

---

