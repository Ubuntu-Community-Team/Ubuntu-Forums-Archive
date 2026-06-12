---
title: "Nework Diagnosis-Script"
date: 2011-08-28
forum: Desktop Environments
---

### Post by fdrake on 2011-08-28
This is a script to get a diagnosis of your network to help yourself in case of trubleshoting ( Wi-Fi/Lan).  If you are using USB- network adapters is highly suggest that you run a lsusb command next to the scripts. Since i did not include any usb scan for network devices I suggest to use a different script or to change this one to meet your needs.

How-To:

1.download attachment:net.sh

2.sudo chmod +x net.sh

3.sudo ./net.sh

4. After you run the script, a file named ‘results.txt’ will be created.

content of the file 
net.sh
```

#!/bin/bash
clear
# Document to get a diagnosis of network's trubleshoting ( Wi-Fi/Lan)

printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++"> results.
txt
printf "\n+++++++++++++++++++++++++++++++++++++++++++++System-Info+++++++++++++++++++++++++++++++++++++++++++++++\n">> resul
ts.txt
less /etc/lsb-release >> results.txt
uname -a |less >> results.txt

printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">> results
.txt
printf "\n++++++++++++++++++++++++++++++++++++++++++++++ifconfig+++++++++++++++++++++++++++++++++++++++++++++++++\n">> resul
ts.txt
sudo ifconfig |tee >> results.txt

printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">> results
.txt
printf "\n++++++++++++++++++++++++++++++++++++++++++++++iwconfig+++++++++++++++++++++++++++++++++++++++++++++++++\n">>result
s.txt
sudo iwconfig |tee >> results.txt

printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">> results
.txt
printf "\n++++++++++++++++++++++++++++++++++++++++++++++iwlist-scan++++++++++++++++++++++++++++++++++++++++++++++\n">>result
s.txt
sudo iwlist scan | tee >> results.txt
printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">> results.txt
printf "\n+++++++++++++++++++++++++++++++++++++++++/pro/net/wireless+++++++++++++++++++++++++++++++++++++++++++++\n">> results.txt
less  /proc/net/wireless |tee >> results.txt

printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">> results.txt
printf "\n++++++++++++++++++++++++++/var/lib/NetworkManager/NetworkManager.state+++++++++++++++++++++++++++++++++\n">> results.txt

less /var/lib/NetworkManager/NetworkManager.state >> results.txt

printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">> results.txt
printf "\n++++++++++++++++++++++++++/lib/firmware/+++++++++++++++++++++++++++++++++\n">> results.txt

ls -la /lib/firmware/ | grep ucode | tee >> results.txt



printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">> results.txt
printf "\n++++++++++++++++++++++++++++++++++++++++++++++lswh+++++++++++++++++++++++++++++++++++++++++++++++++++++\n">>results.txt
# print only the network class
sudo lshw -c network |tee >> results.txt
#sudo lshw -c network |tee >> log_lshw.txt


printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">>results.txt
printf "\n++++++++++++++++++++++++++++++++++++++++++++++lspci++++++++++++++++++++++++++++++++++++++++++++++++++++\n">> results.txt
# print verbose output that belongs to the "Ethernet Controller"
driver=""
lspci | grep "Ethernet controller:" | cut -d " " -f 1 |tee >> log.txt
cat log.txt | while read line; 
do
sudo lspci -vvvs $line |tee >> results.txt
driver=$(sudo lspci -vvvs $line | grep "Kernel driver in use:" |cut -d " " -f 5)
echo "-e $driver " >> driver.txt
done

printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">>results.txt
printf "\n++++++++++++++++++++++++++++++++++++++++++++++lsusb++++++++++++++++++++++++++++++++++++++++++++++++++++\n">> results.txt

lsusb -v |tee >> results.txt


printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">>results.txt
printf "\n++++++++++++++++++++++++++++++++++++++++++++++dmesg++++++++++++++++++++++++++++++++++++++++++++++++++++\n">> results.txt
# print error msg lines containing the name of the drivers(found in lspci and in lshw) used by the network devices,"lan", "net", and "radio" words.
#sed -e :a -e N -e 's/\n/ /' -e ta driver.txt > log1.txt
#greps=$(cat driver.txt | tr -d "\n" | less) # list of drivers found in lspci
#dmesg | grep $greps -e radio -e net -e wlan -e " eth"   |less >> results.txt

#print full dmesg 
dmesg |less >> results.txt


printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">>results.txt
printf "\n++++++++++++++++++++++++++++++++++++++++++++++/var/log/syslog++++++++++++++++++++++++++++++++++++++++++++++++++++\n">> results.txt
less /var/log/syslog >> results.txt
printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">>results.txt
printf "\n++++++++++++++++++++++++++++++++++++++++++++++/etc/resolv.conf+++++++++++++++++++++++++++++++++++++++++\n">> results.txt
less /etc/resolv.conf >> results.txt

printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">>results.txt
printf "\n+++++++++++++++++++++++++++++++++++++++/etc/modprobe.d/blacklist.conf++++++++++++++++++++++++++++++++++\n">> results.txt
less /etc/modprobe.d/blacklist.conf >> results.txt 


printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">>results.txt
printf "\n++++++++++++++++++++++++++++++++++++++++++++++lsmod++++++++++++++++++++++++++++++++++++++++++++++++++++\n">> results.txt
# uncomment to make lsmod lists only lines containing the names of the network drivers found from lspci($grep list). Not advaiced if you want to check for installation of ndswrapper or other unkown driver confilcts
#lsmod | grep $greps | less >> results.txt  

# list full lsmod with no filters
lsmod | less >> results.txt

printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++">>results.txt
printf "\n+++++++++++++++++++++++++++++++++++++++++++++++++END+++++++++++++++++++++++++++++++++++++++++++++++++++\n">> resul:


```
ps. I will be more than glad to edit/add the script under suggestions to make it more useful.

---

### Post by Potsoil on 2011-08-28
Hi fdrake, thanks for taking the time to do this.

I'm still very new at using the terminal in Ubuntu (I'm currently doing a course using Python). 
After downloading the attachment, I type "sudo chmod +x net.sh" into the terminal right?
I just get a return message saying 'cannot access net.sh no directory found'

---

### Post by fdrake on 2011-08-28
> **Potsoil said:**
> Hi fdrake, thanks for taking the time to do this.

I'm still very new at using the terminal in Ubuntu (I'm currently doing a course using Python). 
After downloading the attachment, I type "sudo chmod +x net.sh" into the terminal right?
I just get a return message saying 'cannot access net.sh no directory found'

you have to assign the right path of the file. usually ur downloads are all place in ~/Downloads. first "cd ~/Downloads" then "sudo chmod +x net.sh"

---

### Post by Potsoil on 2011-08-28
Thanks for bearing with me!
```

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++++++Sysyem-Info+++++++++++++++++++++++++++++++++++++++++++++++
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux David 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++ifconfig+++++++++++++++++++++++++++++++++++++++++++++++++
eth0      Link encap:Ethernet  HWaddr 00:1b:63:33:19:21  
          inet addr:192.168.1.74  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:63ff:fe33:1921/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:553444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:525727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:460689473 (460.6 MB)  TX bytes:42788500 (42.7 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:313732 (313.7 KB)  TX bytes:313732 (313.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:b3:bf:05:2b  
          inet6 addr: fe80::21c:b3ff:febf:52b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10298 (10.2 KB)  TX bytes:13415 (13.4 KB)


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++iwconfig+++++++++++++++++++++++++++++++++++++++++++++++++
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++/pro/net/wireless+++++++++++++++++++++++++++++++++++++++++++++
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++/var/lib/NetworkManager/NetworkManager.state+++++++++++++++++++++++++++++++++

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++lswh+++++++++++++++++++++++++++++++++++++++++++++++++++++
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 22
       serial: 00:1b:63:33:19:21
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.74 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:90200000-90203fff ioport:1000(size=256) memory:90500000-9051ffff
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:b3:bf:05:2b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:90100000-9010ffff

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++lspci++++++++++++++++++++++++++++++++++++++++++++++++++++
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
    Subsystem: Marvell Technology Group Ltd. Marvell RDK-8053
    Physical Slot: 0
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Interrupt: pin A routed to IRQ 42
    Region 0: Memory at 90200000 (64-bit, non-prefetchable) [size=16K]
    Region 2: I/O ports at 1000 [size=256]
    Expansion ROM at 90500000 [disabled] [size=128K]
    Capabilities: [48] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
    Capabilities: [50] Vital Product Data
        Product Name: Marvell Yukon 88E8053 Gigabit Ethernet Controller
        Read-only fields:
            [PN] Part number: Yukon 88E8053
            [EC] Engineering changes: Rev. 2.2
            [MN] Manufacture ID: 4d 61 72 76 65 6c 6c
            [SN] Serial number: AbCdEfG334455
            [CP] Extended capability: 01 10 cc 03
            [RV] Reserved: checksum good, 9 byte(s) reserved
        Read/write fields:
            [VE] Vendor specific: 00
            [RW] Read-write area: 116 byte(s) free
        End
    Capabilities: [5c] MSI: Enable+ Count=1/2 Maskable- 64bit+
        Address: 00000000fee0100c  Data: 4171
    Capabilities: [e0] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 2048 bytes
        DevSta:    CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 <256ns, L1 unlimited
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr+ BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        AERCap:    First Error Pointer: 1f, GenCap- CGenEn- ChkCap- ChkEn-
    Kernel driver in use: sky2
    Kernel modules: sky2


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++dmesg++++++++++++++++++++++++++++++++++++++++++++++++++++
[    0.016313] Initializing cgroup subsys net_cls
[    0.407388] audit: initializing netlink socket (disabled)
[    1.383493] sky2: driver version 1.28
[    1.383538] sky2 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.383553] sky2 0000:01:00.0: setting latency timer to 64
[    1.383587] sky2 0000:01:00.0: Yukon-2 EC chip revision 2
[    1.383718] sky2 0000:01:00.0: irq 42 for MSI/MSI-X
[    1.392624] sky2 0000:01:00.0: eth0: addr 00:1b:63:33:19:21
[   17.253305] sky2 0000:01:00.0: eth0: enabling interface
[   17.253649] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.273714] Registered led device: ath9k-phy0::radio
[   17.317643] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.519741] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.010671] sky2 0000:01:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[   19.024934] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.336086] wlan0: authenticate with 00:8b:5d:97:ab:8a (try 1)
[   23.338302] wlan0: authenticated
[   23.338325] wlan0: associate with 00:8b:5d:97:ab:8a (try 1)
[   23.341855] wlan0: RX AssocResp from 00:8b:5d:97:ab:8a (capab=0x431 status=0 aid=1)
[   23.341859] wlan0: associated
[   23.344163] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.600056] eth0: no IPv6 routers present
[   34.172036] wlan0: no IPv6 routers present
[   44.206015] wlan0: deauthenticating from 00:8b:5d:97:ab:8a by local choice (reason=3)
[ 9871.636125] sky2 0000:01:00.0: eth0: disabling interface
[ 9876.232025] PM: late suspend of drv:sky2 dev:0000:01:00.0 complete after 155.987 msecs
[ 9876.744997] sky2 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 9876.745008] sky2 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfffe0000)
[ 9876.745025] sky2 0000:01:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x1001)
[ 9876.745033] sky2 0000:01:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x90200004)
[ 9876.745040] sky2 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x40)
[ 9876.745049] sky2 0000:01:00.0: restoring config space at offset 0x1 (was 0x40100000, writing 0x100407)
[ 9878.795358] sky2 0000:01:00.0: eth0: enabling interface
[ 9878.795622] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9878.828933] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9880.607776] sky2 0000:01:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[ 9880.608161] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 9884.915134] wlan0: authenticate with 00:8b:5d:97:ab:8a (try 1)
[ 9884.918327] wlan0: authenticated
[ 9884.918349] wlan0: associate with 00:8b:5d:97:ab:8a (try 1)
[ 9884.921906] wlan0: RX AssocResp from 00:8b:5d:97:ab:8a (capab=0x431 status=0 aid=1)
[ 9884.921910] wlan0: associated
[ 9884.924224] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9890.688033] eth0: no IPv6 routers present
[ 9895.720073] wlan0: no IPv6 routers present
[ 9905.207891] wlan0: deauthenticating from 00:8b:5d:97:ab:8a by local choice (reason=3)
[22620.412691] sky2 0000:01:00.0: eth0: Link is down
[23422.658272] sky2 0000:01:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++lsmod++++++++++++++++++++++++++++++++++++++++++++++++++++
sky2                   49172  0 

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++++++++++END+++++++++++++++++++++++++++++++++++++++++++++++++++
```

I can connect via an ethernet cable, and my mac picks up the signal of my wireless network, but whenever I try to connect it fails. This happened when I had Tiger installed, and I solved it by downloading a driver update, however I'm not sure how to compile packages on Ubuntu yet, or if there's an easier way, of if I've even got the right file!

---

### Post by fdrake on 2011-08-28
ehhh.. something is strange. your wirelss show in the error logs and in the hardware list but not in the pci list or in the kernel's modules list, and not even in the wireless connection log.

can you try 
```
lspci | grep Ethernet
less /var/log/daemon.log
```

it seems like it's a driver issue.

---

### Post by Potsoil on 2011-08-28
lspci | grep Ethernet
```
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)

```
less /var/log/daemon.log
```
/var/log/daemon.log: No such file or directory
```

---

### Post by Potsoil on 2011-08-28
I've downloaded what I think is the correct driver, however it's in what I think is called a tarball? In other words I just get a lot of files that I think I need to compile manually, and I'm not sure how to do that..

---

### Post by fdrake on 2011-08-28
yes it looks like your wifi card is not recognized in pci list but it is present in iwconfig and in lshw.

---

### Post by Potsoil on 2011-08-28
```
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
    Subsystem: Marvell Technology Group Ltd. Marvell RDK-8053
    Physical Slot: 0
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Interrupt: pin A routed to IRQ 42
    Region 0: Memory at 90200000 (64-bit, non-prefetchable) [size=16K]
    Region 2: I/O ports at 1000 [size=256]
    Expansion ROM at 90500000 [disabled] [size=128K]
    Capabilities: [48] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
    Capabilities: [50] Vital Product Data
        Product Name: Marvell Yukon 88E8053 Gigabit Ethernet Controller
        Read-only fields:
            [PN] Part number: Yukon 88E8053
            [EC] Engineering changes: Rev. 2.2
            [MN] Manufacture ID: 4d 61 72 76 65 6c 6c
            [SN] Serial number: AbCdEfG334455
            [CP] Extended capability: 01 10 cc 03
            [RV] Reserved: checksum good, 9 byte(s) reserved
        Read/write fields:
            [VE] Vendor specific: 00
            [RW] Read-write area: 116 byte(s) free
        End
    Capabilities: [5c] MSI: Enable+ Count=1/2 Maskable- 64bit+
        Address: 00000000fee0100c  Data: 4171
    Capabilities: [e0] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 2048 bytes
        DevSta:    CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 <256ns, L1 unlimited
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr+ BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        AERCap:    First Error Pointer: 1f, GenCap- CGenEn- ChkCap- ChkEn-
    Kernel driver in use: sky2
    Kernel modules: sky2


```

---

### Post by fdrake on 2011-08-28
```

sudo ifconfig wlan0 up
sudo iwconfig wlan0 power on

```
ca you post the link of the driver you are trying to install

---

### Post by Potsoil on 2011-08-28
[http://fedoramobile.org/fc-wireless/bcm43xx-yum-extras](http://fedoramobile.org/fc-wireless/bcm43xx-yum-extras)

I think that's the one I need.

---

### Post by Potsoil on 2011-08-28
[oops double post]("http://fedoramobile.org/fc-wireless/bcm43xx-yum-extras")

---

### Post by fdrake on 2011-08-29
the driver you are trying to in stall is meant for Broadcom devices, instead you are using a  device from Atheros Communications Inc. the right driver is:  [http://wiki.debian.org/ath9k#Supported_Devices](http://wiki.debian.org/ath9k#Supported_Devices)

```

sudo aptitude update && sudo aptitude install wireless-tools
sudo modprobe ath9k
<reboot>
iwconfig wlan0 power on
ifconfig wlan0 up

```
if you have still problems run again the script and repost again please. you just need to install the correct driver.

---

### Post by Potsoil on 2011-08-29
Ha, thanks!
After running sudo aptitude update && aptitude install wireless-tools
I get:
```
sudo: aptitude: command not found

```

Do I need to download something from the wireless tools package link first?

---

### Post by Neko16 on 2011-08-29
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++ifconfig+++++++++++++++++++++++++++++++++++++++++++++++++
eth0      Link encap:Ethernet  HWaddr 00:24:81:55:6f:41  
          inet addr:192.168.0.114  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe55:6f41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8871908 (8.8 MB)  TX bytes:1096513 (1.0 MB)
          Interrupt:22 Memory:e4600000-e4620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++iwconfig+++++++++++++++++++++++++++++++++++++++++++++++++
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++/pro/net/wireless+++++++++++++++++++++++++++++++++++++++++++++
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++/var/lib/NetworkManager/NetworkManager.state+++++++++++++++++++++++++++++++++

[main]
:

---

### Post by fdrake on 2011-08-30
> **Potsoil said:**
> Ha, thanks!
After running sudo aptitude update && aptitude install wireless-tools
I get:
```
sudo: aptitude: command not found

```

Do I need to download something from the wireless tools package link first?

ehh.. ?? that's odd. are you sure you re typing the command correctly?
try this instead:
```

sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install aptitude
sudo aptitude update

```

Edit:
> ```
network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:b3:bf:05:2b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=ath9k driverversion=2.6.38-11-generic[/COLOR] firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:90100000-9010ffff
```


also I just double checked more carefully your script and i found out that the right driver is actually already installed (in lshw, even if lspci did not show it). My bad, i missed that! :P

so the driver is not the problem in this case! which is better....
can you post the results for this commands:
```

sudo iwlist scan | less

```
and which one is your ESSID name
are you able to connect normally to .an open(no pass/encryption) wifi hotspot?
if so change your router setting to WAP or WAP2 only , do not use WAP/WAP2

---

### Post by fdrake on 2011-08-30
> **Neko16 said:**
> DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++ifconfig+++++++++++++++++++++++++++++++++++++++++++++++++
eth0      Link encap:Ethernet  HWaddr 00:24:81:55:6f:41  
          inet addr:192.168.0.114  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe55:6f41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8871908 (8.8 MB)  TX bytes:1096513 (1.0 MB)
          Interrupt:22 Memory:e4600000-e4620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++iwconfig+++++++++++++++++++++++++++++++++++++++++++++++++
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++/pro/net/wireless+++++++++++++++++++++++++++++++++++++++++++++
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++/var/lib/NetworkManager/NetworkManager.state+++++++++++++++++++++++++++++++++

[main]
:

i am sorry to sound rude but this was suppose to be a thread about my script in the first place (on how to improve it and elaborate the informations collected by the system), not a place where everyone post their results and ask for help, please . It's going to get very confusing for the ppl that are trying to help to understand the situation for each one of you. I am just doing a favor to Potsoil by letting him posting here his/her own issues... for this time only! 
If you have troubles with your wifi open a new thread (under "networking and wireless") and post here a link to it. I will be happy to assist you there and I am sure you will find a lot more help too.  ;)

---

### Post by Potsoil on 2011-08-30
Sorry Fdrake I didn't realise this wasn't the purpose of the thread, I can message you rather than continue to clog up your thread if you like? :tongue:

results of the scan:
```
wlan0     Scan completed :
          Cell 01 - Address: 06:8B:5D:97:AB:8A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fbcfac180
                    Extra: Last beacon: 2620ms ago
                    IE: Unknown: 000A42544F70656E7A6F6E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:8B:5D:97:AB:8A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-22T7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fbd00a7f9
                    Extra: Last beacon: 2184ms ago
                    IE: Unknown: 000F4254486F6D65487562322D32325437
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF3F000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 0A:8B:5D:97:AB:8A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fbd010284
                    Extra: Last beacon: 2236ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000

(END) 
```

Do you mean change the actual settings on the router itself? Or on my settings on here? I haven't got an option to change to just WAP or WAP2 only on my network settings.
I can connect to BT openzone and whatnot, which is what made me think it was just the driver for that particular router.

---

### Post by fdrake on 2011-08-30
from the scan i have 3 results: BTOpenzone, BTFON which are open and i think you should not have any problem to connect to them. And we have BTHomeHub2-22T7 which uses a mixed mode ecryption mode wap/wap2
```
                   IE: IEEE 802.11i/[COLOR="Red"]**_WPA2_**[/COLOR] Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: [COLOR="Red"]_**WPA**_[/COLOR] Version 1
                        Group Cipher : TKIP
```

mixed mode setting is know isssue in a lot of drivers in linux/ubuntu. you can change your routers' setting by connecting through the ethernet and go to the "wireless-security" tab and select either "wap" or "wap2" only.

if you have problems post here please.

---

### Post by Potsoil on 2011-08-30
My only other security option is WEP...I'm actually moving house in 2 weeks so for fear of having everyone else in the house having to reconfigure their wireless settings I might just wait and see if I can connect to my new router

But thanks so much for all your help fdrake! I'll probably spend the rest of the two weeks trying to figure out how to get my speakers and macbook camera to work :-P

---

### Post by fdrake on 2011-08-30
you are welcome. actually you made me realize I am missing few commands and logs to improve the script.

---

### Post by lkjoel on 2011-08-31
There is a much more complete version of the script at: j.mp/Netinfo

Could we team up on the scripts? Strength relies in Unity ;-)

---

### Post by fdrake on 2011-09-01
> **lkjoel said:**
> There is a much more complete version of the script at: j.mp/Netinfo

Could we team up on the scripts? Strength relies in Unity ;-)

sure that would be great! It's been a while that I was wondering with so many wireless / network issues around how come there isn't a script yet to automate these commands?

I never noticed the your sign had the links to it, and I have seen you around a lot in the forum! I must be blind or something!

I checked your script and I like the fact that you check for the commands first and created user-friendly interface when loading.

What I'd like to do in my script like you did in your is to add the usb scan and extract from lspci,lshw,lsusb, the driver-names, firmware-names and the devices-names and use those variables (next to "net" "wlan" "eth" "radio") to filter the long log files present in dmesg and in /var/log/syslog. To make the research of the problem faster. Also filter with these variable the blacklisting of drivers and the list of modules in general. 

What i did on mine is to extract the driver names from lspci for example and save those info in a temp log file, and then use those name to filter dmesg and lsmod. Unfortunately if your device is not listed in lspci that is useless, like it happened with the poster in this thread. 

I know this is not a big deal in the end we can do ourself when we have the .txt file downloaded in the hdd. Sometimes filtering is good other times not, especially when you do not know what you are looking for (like for example a conflict with ndiswrapper). So here I am stuck to answer this question : to filter or not to filter the endless-logs? or maybe give an option in the script?

ps. I updated my script with no filters and more logs.

edit: i got an idea how about we highlight those names (or the lines containing them)with a bold font and a different color? this way we have the whole log and at the same time we know where to look for?

---

### Post by lkjoel on 2011-09-01
> **fdrake said:**
> sure that would be great! It's been a while that I was wondering with so many wireless / network issues around how come there isn't a script yet to automate these commands?

I never noticed the your sign had the links to it, and I have seen you around a lot in the forum! I must be blind or something!

I checked your script and I like the fact that you check for the commands first and created user-friendly interface when loading.

What I'd like to do in my script like you did in your is to add the usb scan and extract from lspci,lshw,lsusb, the driver-names, firmware-names and the devices-names and use those variables (next to "net" "wlan" "eth" "radio") to filter the long log files present in dmesg and in /var/log/syslog. To make the research of the problem faster. Also filter with these variable the blacklisting of drivers and the list of modules in general. 

What i did on mine is to extract the driver names from lspci for example and save those info in a temp log file, and then use those name to filter dmesg and lsmod. Unfortunately if your device is not listed in lspci that is useless, like it happened with the poster in this thread. 

I know this is not a big deal in the end we can do ourself when we have the .txt file downloaded in the hdd. Sometimes filtering is good other times not, especially when you do not know what you are looking for (like for example a conflict with ndiswrapper). So here I am stuck to answer this question : to filter or not to filter the endless-logs? or maybe give an option in the script?

ps. I updated my script with no filters and more logs.

edit: i got an idea how about we highlight those names (or the lines containing them)with a bold font and a different color? this way we have the whole log and at the same time we know where to look for?
Should I add you as a developer of the Network Info script? That way you could help out easily.

Maybe we should add an upload option like the option in the Alsa-Info script? Then it could upload an HTML file, with the correct highlighting.

---

### Post by fdrake on 2011-09-02
> **lkjoel said:**
> Should I add you as a developer of the Network Info script? That way you could help out easily.

Maybe we should add an upload option like the option in the Alsa-Info script? Then it could upload an HTML file, with the correct highlighting.

I will be very happy to help out in the project! Probably an on-line view is the easiest thing to do in this case for everyone. Actually is even better than I thought since we can collect all the data very easly and fast for each driver/device in a database(preferably a mySQL) and relate those to the errors present in the log files or in the commands...  just a thought, but there is time for that.

I will take a look at the alsa-info script right now. PM me or contact me anytime if you have any news/ideas or whatever thing that you want to do in the project.

---

### Post by lkjoel on 2011-09-02
OK. Did you register for sourceforge.net?

I've just updated the script a bit, fixing a few bugs and adding all of the checks included in your script (and fixed a few bugs on your checks ;-)).

---

