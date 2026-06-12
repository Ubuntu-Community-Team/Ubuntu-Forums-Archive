---
title: "Broadcom problems on Dell, KUbuntu 10.04"
date: 2011-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ivan-r on 2011-11-08
Hi everybody, 
I would really like to ask for your help with the following problem, ( I've tried some enlighting posts, like this[ http://ubuntuforums.org/showthread.php?p=9449490]("http://ubuntuforums.org/showthread.php?p=9449490")_ _, however, I suspect that the issue here is different.)

-->> I don't have neither wired, nor wireless connection. The wired connection was lost after I installed
bcmwl-kernel-source. 

my wireless was not working on ubuntu 8.04 and it was one of the reasons  to update to Ubuntu 10.04 (Actually, I have kubuntu). I read a blog somewhere ([http://blog.jorgeivanmeza.com/2010/04/activar-las-tarjetas-wifi-broadcom-despues-de-instalar-linux-ubuntu-10-04/](http://blog.jorgeivanmeza.com/2010/04/activar-las-tarjetas-wifi-broadcom-despues-de-instalar-linux-ubuntu-10-04/)) that suggest to install bcmwl-kernel-source to solve the wireless issue. However, the result was the opposite: the wired connection did brake down.

I have a Dell Inspiron 1300, with kernel 2.6.32-35. Now, I report some outputs that I hope to be helpful, please tell me if you need some more info.
I will really appreciate your advice.
Cheers!


```
 sudo ifconfig -a 
```eth1      Link encap:Ethernet  direcciónHW 00:14:a5:84:47:cd  
          Direc. inet:148.247.183.153  Difus.:148.247.183.255  Másc:255.255.255.0
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 Memoria:dfbfe000-dfc00000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:484 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:484 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:43253 (43.2 KB)  TX bytes:43253 (43.2 KB)


```
lspci
```00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)



```
sudo ifup eth0
```Ignoring unknown interface eth0=eth0.
ivan@ivan-laptop:~$ sudo ifup eth1
ifup: interface eth1 already configured



```
cat /etc/network/interfaces 
```auto lo
iface lo inet loopback


iface eth1 inet static
address 148.247.183.153
netmask 255.255.255.0
gateway 148.247.183.44


```
cat /etc/NetworkManager/nm-system-settings.conf 
```[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


```
dmesg | grep -e eth -e bcm
```[   35.550236] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   35.958263] wlan0: ethernet device 00:14:a5:84:47:cd using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   35.966848] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   35.966883] udev: renamed network interface wlan0 to eth1
[   35.998615] ADDRCONF(NETDEV_UP): eth1: link is not ready


```
sudo lshw -C Network
```  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:dfbfc000-dfbfdfff
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:84:47:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,10/12/2006, 4.100. ip=148.247.183.153 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:dfbfe000-dfbfffff

---

### Post by linuxaddix on 2011-11-11
first off the bcmwl kernel source does not work for a bcm4318 card.uninstall it through synaptic
after uninstalling your ethernet should come back on.now for the driver you need:
while in synaptic type in 
bcm              in the search bar
look for 
firmware-b43-installer
mark for install
fw-cutter approval screen will pop up just click mark
now hit the apply tab 
now your wireless works
all this needs to be done with internet connection

---

