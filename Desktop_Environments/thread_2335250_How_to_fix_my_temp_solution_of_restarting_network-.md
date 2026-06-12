---
title: "How to fix my temp solution of restarting network-manager on every boot ?"
date: 2016-08-26
forum: Desktop Environments
---

### Post by val-apana on 2016-08-26
I have Lubuntu 14.04 installed and recently swapped my motherboard to the "GIGABYTE Z97X-Gaming 7" with the "Killer E2200 Gaming Networking Platform".

The only way I'm able to use the Ethernet port is by resetting network-manager every time I boot:

```
sudo service network-manager restart
```

I have seen other posts that mention problems with the E2200 and various ways of installing the driver, but if simply restarting network-manager fixes everything, I'm assuming my driver are fine.

I'm looking for a way to have internet without manually restarting network-manager every time I reboot.

Thank You
Val

---

### Post by &amp;KyT$0P# on 2016-08-26
Can you please explain more what kind of state is your NetworkManager / connections in before you restart NetworkManager?

---

### Post by jeremy31 on 2016-08-26
What kernel are you using ```
uname -a
```

---

### Post by val-apana on 2016-08-29
Hello halogen2,

When lubuntu boots up and I hover over the Network-Manager icon it says "Networking disabled" and if I click the icon it says "Networking Manager is not running..."

---

### Post by val-apana on 2016-08-29
jeremy31,

Below is the response after typing in "uname -a":
Linux XXXX-Z97X-UD3H-BK 3.19.0-66-generic #74~14.04.1-Ubuntu SMP Tue Jul 19 19:56:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by &amp;KyT$0P# on 2016-08-29
Any related log messages?
(run these commands, after booting and before restarting network-manager)
```

cat /var/log/syslog | grep -i networkmanager
dmesg | grep -i networkmanager

```

---

### Post by val-apana on 2016-09-01
Results from "cat /var/log/syslog | grep -i networkmanager"

```
Sep  1 11:42:27 valapana-Z97X-UD3H-BK kernel: [   10.638797] audit: type=1400 audit(1472755343.649:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=540 comm="apparmor_parser"Sep  1 11:42:27 valapana-Z97X-UD3H-BK kernel: [   10.638808] audit: type=1400 audit(1472755343.649:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=539 comm="apparmor_parser"
Sep  1 11:42:27 valapana-Z97X-UD3H-BK kernel: [   10.638995] audit: type=1400 audit(1472755343.649:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=540 comm="apparmor_parser"
Sep  1 11:42:27 valapana-Z97X-UD3H-BK kernel: [   10.639004] audit: type=1400 audit(1472755343.649:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=539 comm="apparmor_parser"
Sep  1 11:44:27 valapana-Z97X-UD3H-BK kernel: [  134.591916] audit: type=1400 audit(1472755467.709:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=946 comm="apparmor_parser"
Sep  1 11:44:27 valapana-Z97X-UD3H-BK kernel: [  134.592116] audit: type=1400 audit(1472755467.709:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=946 comm="apparmor_parser"
Sep  1 11:44:28 valapana-Z97X-UD3H-BK whoopsie[1173]: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files

```


"GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown"....looks like a clue.

---

### Post by val-apana on 2016-09-01
dmesg | grep -i networkmanager

```

[   11.271079] audit: type=1400 audit(1472756343.280:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=530 comm="apparmor_parser"
[   11.271090] audit: type=1400 audit(1472756343.280:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=531 comm="apparmor_parser"
[   11.271277] audit: type=1400 audit(1472756343.280:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=530 comm="apparmor_parser"
[   11.271287] audit: type=1400 audit(1472756343.280:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=531 comm="apparmor_parser"
[  134.575030] audit: type=1400 audit(1472756466.692:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=940 comm="apparmor_parser"
[  134.575229] audit: type=1400 audit(1472756466.692:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=940 comm="apparmor_parser"



```

---

### Post by &amp;KyT$0P# on 2016-09-01
Looks like NetworkManager may not ever have been started? :-k

Does reinstalling NetworkManager change anything?
```
sudo apt-get update
sudo apt-get --reinstall install network-manager
```

---

### Post by val-apana on 2016-09-01
I just tried it. No, same symptoms.

Network Manager does pop up on the bottom right when I boot.  However, it says "Networking disabled"

---

### Post by &amp;KyT$0P# on 2016-09-01
> **val-apana said:**
> Network Manager does pop up on the bottom right 
That's not NetworkManager, that's just the applet interface to NetworkManager; it's part of a different package (and presumably where the log message you pointed out earlier had come from).  NetworkManager itself isn't a GUI program.

What do you have in [FONT=Courier New]/etc/NetworkManager/NetworkManager.conf[/FONT]?

EDIT Also can you please post the output of this command
```
cat /etc/init/network-manager.conf
```

---

### Post by val-apana on 2016-09-07
```

cat /etc/init/network-manager.conf
# network-manager - network connection manager
#
# The Network Manager daemon manages the system's network connections,
# automatically switching between the best available.


description    "network connection manager"


start on (local-filesystems
      and started dbus
      and static-network-up)
stop on stopping dbus


expect fork
respawn


script
    # set $LANG so that messages appearing on the GUI will be translated. See LP: 875017
    if [ -r /etc/default/locale ]; then
        . /etc/default/locale
        export LANG LANGUAGE LC_MESSAGES LC_ALL
    fi


    exec NetworkManager
end script


 
```

---

### Post by val-apana on 2016-09-07
```

cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false



```

---

### Post by &amp;KyT$0P# on 2016-09-07
Those configurations look identical to mine, so you should be good there.

I'm not sure what else to suggest at this point, sorry. :(

---

### Post by val-apana on 2016-09-07
halogen2, 

Thanks for the help!

---

### Post by 1clue on 2016-09-07
Can you run these both before and after the restart?:

```

lspci -k
ip address list
netstat -rn

```

What I'm curious about are:
[LIST=1]
[*]What changes, and how?
[*]Are there any colliding interfaces?
[*]Once you restart the network, does it break after awhile, or does it stay up?
[/LIST]

---

### Post by jeremy31 on 2016-09-07
In addition to 1clue's request, please post ```
modinfo alx
```

---

### Post by val-apana on 2016-09-07
id address list: before reset
```

ip address list
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth8: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 40:8d:5c:be:bc:1d brd ff:ff:ff:ff:ff:ff

```

ip address list: after reset
```

ip address list
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 40:8d:5c:be:bc:1d brd ff:ff:ff:ff:ff:ff
    inet 10.1.2.125/24 brd 10.1.2.255 scope global eth8
       valid_lft forever preferred_lft forever
    inet6 fe80::428d:5cff:febe:bc1d/64 scope link 
       valid_lft forever preferred_lft forever

```

netstat -rn: before reset

```

netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

``` 

netstat -rn: after reset
```

 netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.1.2.1        0.0.0.0         UG        0 0          0 eth8
10.1.2.0        0.0.0.0         255.255.255.0   U         0 0          0 eth8

```



For "lspci -k", I used the diff command in Sublime: Files are identical.
```

lspci -k
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Device 5000
	Kernel driver in use: hsw_uncore
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Device d000
	Kernel driver in use: i915
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
	Subsystem: Intel Corporation Device 2010
	Kernel driver in use: snd_hda_intel
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
	Subsystem: Gigabyte Technology Co., Ltd Device 5007
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
	Subsystem: Gigabyte Technology Co., Ltd Device 1c3a
	Kernel driver in use: mei_me
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
	Subsystem: Gigabyte Technology Co., Ltd Device 5006
	Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
	Subsystem: Gigabyte Technology Co., Ltd Device a0b2
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
	Kernel driver in use: pcieport
00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
	Kernel driver in use: pcieport
00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
	Kernel driver in use: pcieport
00:1c.4 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 5 (rev d0)
	Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
	Subsystem: Gigabyte Technology Co., Ltd Device 5006
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
	Subsystem: Gigabyte Technology Co., Ltd Device 5001
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
	Subsystem: Gigabyte Technology Co., Ltd Device b005
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
	Subsystem: Gigabyte Technology Co., Ltd Device 5001
02:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 10)
	Subsystem: Gigabyte Technology Co., Ltd Device e000
	Kernel driver in use: alx
03:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)
05:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 12)
	Subsystem: Gigabyte Technology Co., Ltd Device b000
	Kernel driver in use: ahci

```


For "modinfo alx", I used the diff command in Sublime: Files are identical.

```
modinfo alx
filename:       /lib/modules/3.19.0-66-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko
license:        GPL
description:    Qualcomm Atheros(R) AR816x/AR817x PCI-E Ethernet Network Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
author:         Johannes Berg <johannes@sipsolutions.net>
srcversion:     1917D292620190CB7319BDE
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v00001969d0000E091sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio
intree:         Y
vermagic:       3.19.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D8:C3:B4:D8:7D:A2:6A:77:55:20:0B:8D:85:4D:5D:41:24:F0:28:69
sig_hashalgo:   sha512

```

---

### Post by pawel-2 on 2017-03-31
Hello,
Did you solve you problem? Could you tell me how? I have the same isue.

---

### Post by wildmanne39 on 2017-03-31
> **pawel-2 said:**
> Hello,
Did you solve you problem? Could you tell me how? I have the same isue.

Hello this is an old thread, please start a new one in networking so you can get the help you need.
Thanks

---

### Post by val-apana on 2017-03-31
I'm on Ubuntu 16.04 LTS now.

---

### Post by jsmcclure on 2017-07-23
I hope that this is still of some use, at least to people that are able to locate this thread in the future. The E2200 Killer Network device, actually, is not the culprit when it comes to the networking issues that people are experiencing on Linux. It is the motherboard itself. Here are the steps that I took to get my Network device to finally start working. *This is achieved on Ubuntu 17.04.*

**Step 1:  **Edit the Grub file.

You will do this by opening up the terminal, going into sudo, and typing

```
nano /etc/default/grub
```

You then need to edit a single line to add "iommu=soft". It should look like

```
GRUB_CMDLINE_LINUX="iommu=soft"
```

Save the file.

**Step 2:  **Change the BIOS

Restart your computer and enter the BIOS.

Navigate to the peripherals section and disable IOMMU.

Save and exit.

**Step 3:  **Enjoy!

*Please note, however, that it needs to be done in the order listed. Disabling IOMMU in the BIOS prior to editing the Grub file will, in fact, enable your networking. It will also disable your USB devices (keyboard, mouse, etc.). That is why the Grub file needs to have that line edited first.*

---

