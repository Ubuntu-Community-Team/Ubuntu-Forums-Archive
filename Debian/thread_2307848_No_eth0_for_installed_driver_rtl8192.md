---
title: "No eth0 for installed driver rtl8192"
date: 2015-12-28
forum: Debian
---

### Post by soneen11 on 2015-12-28
Ok, so I installed debian-testing-amd64-xfce-CD-1.iso and I'm having issues with my network driver (I would have asked in thread/debian, but this is network specific). I used the appropriate network binary (rtl8192sefw.bin) during the installation (since this driver is non-free) and it proceeded to work flawlessly downloading the additional packages.


Despite installing network binary, I can't connect under wired or wireless, and eth0 doesn't appear under ifconfig. enp7so appears to be the ethernet connection instead. Reading up on this, it might to be a systemd issue  with networking, but I'm not sure why. Here are the outputs.

cat /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto eth0
allow-hotplug eth0
iface eth0 inet dhcp

```

ifconfig -a
```

enp7s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether c8:0a:a9:90:83:19  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 49  bytes 7343 (7.1 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 49  bytes 7343 (7.1 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp8s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 70:f1:a1:92:ac:b2  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

lspci -v
```

07:00.0 Ethernet controller: Qualcomm Atheros AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at c0800000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 4000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-90-83-19-c8-0a-a9-ff
    Kernel driver in use: atl1c


08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 5000 [size=256]
    Memory at c0d00000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 88-55-22-fe-ff-4c-e0-00
    Kernel driver in use: rtl8192se

```

---

### Post by lisati on 2015-12-28
*Thread moved to **Debian**.*

---

