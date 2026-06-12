---
title: "Netgear MA521 : Need personal help"
date: 2009-04-19
forum: General Help
---

### Post by n2stc on 2009-04-19
{SOLVED]
The card is in a compaq laptop. UBUNTU 8.1
 I have looked at all the posts and my head is spinning!  I have installed the windows 200 driver with ndiswrapper.  I actually connected once, with a very slow connection.  I disconnected and retried and now can't get anywhere.  Now it looks like I have no signal sitting right next to the wireless node.  I can connect to the node with another LT running windows.

 ```
 
~$ndiswrapper -l
net8180 : driver installed
	device (10EC:8180) present (alternate driver: rtl8180)
 ndiswrapper -l
net8180 : driver installed
	device (10EC:8180) present (alternate driver: rtl8180)

=======================================
~$iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"N2STC"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

I keeping giving up and coming back, so I don't throw this thing through the window!  Your help would be appreciated!

Stan

---

### Post by prshah on 2009-04-19
> **n2stc said:**
> 
 ```
 
~$ndiswrapper -l
net8180 : driver installed
	device (10EC:8180) present (alternate driver: rtl8180)

```



Are you sure you're using the ndiswrapper driver and not the "alternate" rtl8180 as suggested? Check with ```
lsmod | grep -i -E ndiswrapper\|rtl8180
```

---

### Post by n2stc on 2009-04-19
Thanks for the reply.  I'm not sure of anything at this point:

```
:~$ lsmod | grep -i -E ndiswrapper\|rtl8180
ndiswrapper           196380  0 
rtl8180                36352  0 
mac80211              216820  1 rtl8180
eeprom_93cx6           10240  1 rtl8180
cfg80211               32392  2 rtl8180,mac80211
usbcore               148848  4 ndiswrapper,ehci_hcd,ohci_hcd

```

My next move?

---

### Post by n2stc on 2009-04-19
> **n2stc said:**
> Thanks for the reply.  I'm not sure of anything at this point:

```
:~$ lsmod | grep -i -E ndiswrapper\|rtl8180
ndiswrapper           196380  0 
rtl8180                36352  0 
mac80211              216820  1 rtl8180
eeprom_93cx6           10240  1 rtl8180
cfg80211               32392  2 rtl8180,mac80211
usbcore               148848  4 ndiswrapper,ehci_hcd,ohci_hcd

```

My next move?

Anybody know what each of the columns mean?

---

### Post by n2stc on 2009-04-19
Boldly bumped.;)

---

### Post by n2stc on 2009-04-19
Monday bump.

---

### Post by prshah on 2009-04-21
> **n2stc said:**
> Thanks for the reply.  I'm not sure of anything at this point:

```
:~$ lsmod | grep -i -E ndiswrapper\|rtl8180
ndiswrapper           196380  0 
rtl8180                36352  0 
mac80211              216820  1 rtl8180
eeprom_93cx6           10240  1 rtl8180
cfg80211               32392  2 rtl8180,mac80211
usbcore               148848  4 ndiswrapper,ehci_hcd,ohci_hcd

```

My next move?

OK looks confusing to me too; seems as though both modules are active. However, as a next move you can try this```
sudo modprobe -r ndiswrapper rtl8180
sudo modprobe ndiswrapper
```

Now try connecting, and see if everything works. If it's all OK, post back on how to disable the rtl8180 module from loading.

If it still seems to be giving the same problems, try the rtl8180 module instead of the ndiswrapper module```
sudo modprobe -r ndiswrapper 
sudo modprobe rtl8180
```

If neither of these works post back the last 50 lines from the logs for debugging```
dmesg | tail -50
```

---

### Post by n2stc on 2009-04-26
> **prshah said:**
> OK looks confusing to me too; seems as though both modules are active. However, as a next move you can try this```
sudo modprobe -r ndiswrapper rtl8180
sudo modprobe ndiswrapper
```

Now try connecting, and see if everything works. If it's all OK, post back on how to disable the rtl8180 module from loading.

Works Now.  I did boot without the card installed, then added it.  I saw signal level going up and down.  I assume because two mods were trying to control the card.  After your steps above it seems fine.  I am afraid to power down!

Please tell how to  disable rtl8180.  THANKS!

---

### Post by n2stc on 2009-04-26
> **n2stc said:**
> Works Now.  I did boot without the card installed, then added it.  I saw signal level going up and down.  I assume because two mods were trying to control the card.  After your steps above it seems fine.  I am afraid to power down!

Please tell how to  disable rtl8180.  THANKS!

It turns out that was a fluke.  After reboot it doesn't work again.:cry:

---

### Post by n2stc on 2009-04-26
I removed the rtl8180 module added ndiswrapper and restarted the net manager, ```
sudo /etc/init.d/NetworkManager restart
```  

and working.  did this

 ```
sudo gedit /etc/rc.local
```

Added these lines before 
exit 0

```
 modprobe -r rtl8180
modprobe -r ndiswrapper
modprobe ndiswrapper
/etc/init.d/NetworkManager restart
```


And did this:

```

 sudo co rtl8180.ko rtl8180.bu
 sudo cp rtl8180.ko rtl8180.bu
 sudo rm rtl8180.ko rtl8180.bu

```

OK?

---

### Post by prshah on 2009-04-26
> **n2stc said:**
> 
```
 modprobe -r rtl8180
modprobe -r ndiswrapper
modprobe ndiswrapper
/etc/init.d/NetworkManager restart
```


Instead of all these changes, you should just blacklist the rtl8180 driver; ```
sudo vi /etc/modprobe.d/blacklist
``` and add the line ```
blacklist rtl8180
``` at the end of the file.

I recommend you undo all your documented changes and do this instead.

---

### Post by n2stc on 2009-04-27
> **prshah said:**
> Instead of all these changes, you should just blacklist the rtl8180 driver; ```
sudo vi /etc/modprobe.d/blacklist
``` and add the line ```
blacklist rtl8180
``` at the end of the file.

I recommend you undo all your documented changes and do this instead.

Thanks, but it doesn't work.

```
dmesg | tail -50
[   46.373125] Bluetooth: SCO (Voice Link) ver 0.6
[   46.373139] Bluetooth: SCO socket layer initialized
[   46.440434] Bluetooth: RFCOMM socket layer initialized
[   46.441501] Bluetooth: RFCOMM TTY layer initialized
[   46.441700] Bluetooth: RFCOMM ver 1.10
[   48.936843] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 5
[   48.936876] pci 0000:01:05.0: PCI INT A -> Link[LNK0] -> GSI 5 (level, low) -> IRQ 5
[   49.362862] [drm] Initialized drm 1.1.0 20060810
[   49.395764] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   50.179578] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   50.179639] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   50.179699] pci 0000:01:05.0: putting AGP V2 device into 4x mode
[   50.412462] [drm] Setting GART location based on new memory map
[   50.412489] [drm] Loading R100 Microcode
[   50.412541] [drm] writeback test succeeded in 1 usecs
[   50.661821] eth0: link down
[   51.279147] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   51.419543] ndiswrapper: driver net8180 (Realtek,10/07/2004,5.173.1007.2004) loaded
[   51.423954] ndiswrapper 0000:02:00.0: enabling device (0000 -> 0003)
[   51.423983] ndiswrapper 0000:02:00.0: PCI INT A -> Link[LNK2] -> GSI 10 (level, low) -> IRQ 10
[   51.424854] ndiswrapper 0000:02:00.0: setting latency timer to 64
[   51.552348] ndiswrapper: using IRQ 10
[   51.636464] input: ImPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   51.876506] wlan0: ethernet device 00:09:5b:21:a6:b6 using NDIS driver: net8180, version: 0x500aa, NDIS version: 0x500, vendor: 'Realtek RTL8180 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8180.5.conf
[   51.878015] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   51.878657] usbcore: registered new interface driver ndiswrapper
[   57.265083] eth0: link down
[   57.480773] NET: Registered protocol family 17
[   92.586237] NET: Registered protocol family 10
[   92.592813] lo: Disabled Privacy Extensions
[   92.594897] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   92.596706] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   95.349988] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  105.572079] wlan0: no IPv6 routers present
[  184.031586] type=1503 audit(1240883385.847:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5649/net/" pid=5649 profile="/usr/sbin/cupsd"
[  185.226118] type=1503 audit(1240883387.043:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5653/net/" pid=5653 profile="/usr/sbin/cupsd"
[  185.232512] type=1503 audit(1240883387.050:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5653 profile="/usr/sbin/cupsd"
[  185.237513] type=1503 audit(1240883387.054:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5653 profile="/usr/sbin/cupsd"
[  185.237530] type=1503 audit(1240883387.054:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5653 profile="/usr/sbin/cupsd"
[  185.237540] type=1503 audit(1240883387.054:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5653 profile="/usr/sbin/cupsd"
[  185.237548] type=1503 audit(1240883387.054:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5653 profile="/usr/sbin/cupsd"
[  185.237556] type=1503 audit(1240883387.054:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5653 profile="/usr/sbin/cupsd"
[  185.237564] type=1503 audit(1240883387.054:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5653 profile="/usr/sbin/cupsd"
[  185.237571] type=1503 audit(1240883387.054:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5653 profile="/usr/sbin/cupsd"
[  185.620507] ppdev0: registered pardevice
[  185.672138] ppdev0: unregistered pardevice
[  186.132622] ppdev0: registered pardevice
[  186.269962] ppdev0: unregistered pardevice
[  189.212800] ppdev0: registered pardevice
[  189.261180] ppdev0: unregistered pardevice
stan@sc1-3:~$ 


```

---

