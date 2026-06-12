---
title: "Dell Vostro 3400 - Problem Broadcom Wireless device"
date: 2010-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by delcarloj on 2010-12-07
I dont know why, but after download new actualizations, my wireless device didnt work anymore.
Now only can work by cable adaptor...
If run:


julio@julio-laptop:/$ sudo lshw -C network
[sudo] password for julio: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbb00000-fbb03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 03
       serial: a4:ba:db:d1:a3:d6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.100.102 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:44 ioport:e000(size=256) memory:d0b04000-d0b04fff memory:d0b00000-d0b03fff memory:fba00000-fba1ffff

show me the device, but if a Run:

julio@julio-laptop:/$ ifconfig
eth0      Link encap:Ethernet  direcciónHW a4:ba:db:d1:a3:d6  
          Direc. inet:192.168.100.102  Difus.:192.168.100.255  Másc:255.255.255.0
          Dirección inet6: fe80::a6ba:dbff:fed1:a3d6/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:45892 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:25007 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:21589906 (21.5 MB)  TX bytes:4005470 (4.0 MB)
          Interrupción:44 Dirección base: 0xa000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:317 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:317 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:17322 (17.3 KB)  TX bytes:17322 (17.3 KB)

tun0      Link encap:UNSPEC  direcciónHW 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          Direc. inet:10.99.99.6  P-t-P:10.99.99.5  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:7326 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:9615 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:100 
          Bytes RX:3769339 (3.7 MB)  TX bytes:1286337 (1.2 MB)

vmnet1    Link encap:Ethernet  direcciónHW 00:50:56:c0:00:01  
          Direc. inet:192.168.137.1  Difus.:192.168.137.255  Másc:255.255.255.0
          Dirección inet6: fe80::250:56ff:fec0:1/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:46 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  direcciónHW 00:50:56:c0:00:08  
          Direc. inet:192.168.254.1  Difus.:192.168.254.255  Másc:255.255.255.0
          Dirección inet6: fe80::250:56ff:fec0:8/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:46 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

I cant see wlan adapter...
Anyone can help me?
Regards.

---

