---
title: "Ubuntu Mini 9 Internet Connection..."
date: 2008-12-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xCarmen09 on 2008-12-25
Just got an Ubuntu Mini 9 for Christmas. I'm totally new to Ubuntu, but so far I love it...except that I can't do anything with my wireless internet.

I am able to see my wireless network and select it, so I know the wireless is working to some extent. The problem is that once I put the password, it shows that it's connecting and "waiting for the network key," but it never actually connects. I have connected it to the internet and worked great. I downloaded all the updates while I was connected to the internet with the wire, so the updates didn't fix my problem.

Any advice would be greatly appreciated...thanks!

-Katie :)

---

### Post by pytheas22 on 2008-12-25
It may help to connect using wicd instead of Network Manager.  wicd is an alternative connection manager.

To install wicd, plug into the Internet with the wire and run these commands:
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

After those commands finish, launch wicd from your Applications>Internet menu.  You should see a list of networks.  If you need to enter a passphrase, press 'Advanced Settings'; otherwise just click 'Connect' to connect to your network.

If wicd doesn't solve the problem, please try to connect to your network a few times, then open a terminal (Applications>Accessories>Terminal), run the following commands and post the output:
```

lshw -C Network
sudo iwlist scan
dmesg | tail -50
```

---

### Post by xCarmen09 on 2008-12-25
> **pytheas22 said:**
> It may help to connect using wicd instead of Network Manager.  wicd is an alternative connection manager.

To install wicd, plug into the Internet with the wire and run these commands:
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

After those commands finish, launch wicd from your Applications>Internet menu.  You should see a list of networks.  If you need to enter a passphrase, press 'Advanced Settings'; otherwise just click 'Connect' to connect to your network.

If wicd doesn't solve the problem, please try to connect to your network a few times, then open a terminal (Applications>Accessories>Terminal), run the following commands and post the output:
```

lshw -C Network
sudo iwlist scan
dmesg | tail -50
```

To run that first command to install wicd, do I just copy and paste that into the internet, or do I need to do the terminal?

---

### Post by xCarmen09 on 2008-12-25
katie@katie:~$ lshw -C Network
bash: lshw: command not found
katie@katie:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:6E:B2:D6
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-39 dBm  Noise level:-87 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 02 - Address: 00:18:01:88:FA:CD
                    ESSID:"UREC5"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

katie@katie:~$ dmesg | tail -50
[   17.067410] intel_rng: FWH not detected
[   17.133439] iTCO_vendor_support: vendor-support=0
[   17.165780] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   17.165925] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   17.165981] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.187543] ieee80211_crypt: registered algorithm 'NULL'
[   17.218360] r8169 Gigabit Ethernet driver 2.2LK loaded
[   17.218455] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   17.218525] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   17.220002] eth0: RTL8101e at 0xf889a000, 00:21:70:d8:1f:d5, XID 24a00000 IRQ 220
[   17.318367] ieee80211_crypt: registered algorithm 'TKIP'
[   17.389352] EXT3 FS on sda2, internal journal
[   18.047012] Linux agpgart interface v0.102
[   18.055482] agpgart: Detected an Intel 945GME Chipset.
[   18.055717] agpgart: Detected 7932K stolen memory.
[   18.073648] agpgart: AGP aperture is 256M @ 0xd0000000
[   18.149517] [drm] Initialized drm 1.1.0 20060810
[   18.262706] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   18.262754] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   20.970015] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   20.970035] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   20.972896] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   34.753726] Bluetooth: Core ver 2.11
[   34.755559] NET: Registered protocol family 31
[   34.755571] Bluetooth: HCI device and connection manager initialized
[   34.755580] Bluetooth: HCI socket layer initialized
[   34.773147] Bluetooth: HCI USB driver ver 2.9
[   34.773227] usbcore: registered new interface driver hci_usb
[   34.949227] Bluetooth: L2CAP ver 2.9
[   34.949239] Bluetooth: L2CAP socket layer initialized
[   35.003567] Bluetooth: RFCOMM socket layer initialized
[   35.004036] Bluetooth: RFCOMM TTY layer initialized
[   35.004046] Bluetooth: RFCOMM ver 1.8
[   35.370160] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   35.394205] Linux video capture interface: v2.00
[   35.406483] uvcvideo: Found UVC 1.00 device Integrated Webcam (064e:a118)
[   35.422077] usbcore: registered new interface driver uvcvideo
[   35.422095] USB Video Class driver (v0.1.0)
[   35.700563] r8169: eth0: link down
[   35.702428] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.543840] ppdev: user-space parallel port driver
[   36.841165] wl: module license 'unspecified' taints kernel.
[   36.866436] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   36.866463] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   36.889922] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.9
[   49.435468] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   64.174806] eth1: no IPv6 routers present
[   76.029866] r8169: eth0: link up
[   76.033699] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   92.491489] eth0: no IPv6 routers present
katie@katie:~$

---

### Post by pytheas22 on 2008-12-25
> To run that first command to install wicd, do I just copy and paste that into the internet, or do I need to do the terminal?

Sorry for not being more specific.  Yes, you should run those commands (one per line) in the terminal by copying and pasting them.  You can paste text into the terminal by pressing control-shift-V, or by right-clicking and selecting copy.

Please give wicd a try and let me know if it works.

---

### Post by xCarmen09 on 2008-12-25
I've been trying all evening to do those commands you gave me. I have no idea how to use the terminal, and it just isn't working. Nothing is happening even when the commands "seem" to be working. I just restarted and got this error..

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'xCarmen09' is not known on line 16 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

I am really worried about this. I can't even manage to connect to the internet with ubuntu...as much as I want to keep this laptop/OS, it really terrifies me because I can't even do the simplest things. Help!!! :(

---

### Post by albinootje on 2008-12-25
> **xCarmen09 said:**
> 
'E:Type 'xCarmen09' is not known on line 16 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

I am really worried about this. I can't even manage to connect to the internet with ubuntu...as much as I want to keep this laptop/OS, it really terrifies me because I can't even do the simplest things. Help!!! :(

You should fix that error by editing /etc/apt/sources.list.
```

sudo gedit /etc/apt/sources.list

```
Check around line 16 for typos or syntax errors.

---

### Post by pytheas22 on 2008-12-25
> I've been trying all evening to do those commands you gave me. I have no idea how to use the terminal, and it just isn't working. Nothing is happening even when the commands "seem" to be working. I just restarted and got this error..

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'xCarmen09' is not known on line 16 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

I am really worried about this. I can't even manage to connect to the internet with ubuntu...as much as I want to keep this laptop/OS, it really terrifies me because I can't even do the simplest things. Help!!!

I'm sorry things are not going so smoothly, but don't worry; they can be fixed.  I know the terminal is intimidating if you're new to Linux--I was in your shoes myself--but we won't leave you on your own with any of this until the problems are fixed.

Please post the output of these commands:
```

cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get install wicd
```

---

### Post by xCarmen09 on 2008-12-26
Hey pytheas22,

Thanks so much for all your help. I am actually shipping my mini back to Dell today, not because I doubt that you could help me fix my problems, but because it worries me so much that the system as a whole didn't work out of the box. I had a lot of experience with Dell's tech support yesterday, and I decided I am going to return the Dell and go for another netbook I can buy at a real electronics store, that way if I have problems I can just take it there for help. My experiences with the Ubuntu community was great, but this Dell Mini with Ubuntu...for whatever reason, just didn't work well. So I'm trading it in.

Once again, thanks so much for your help.

-Katie

---

### Post by pytheas22 on 2008-12-26
Sorry to hear that, but I understand.  Dell really should make sure that these work out-of-the-box.  I hope you find a new netbook that works better.

---

