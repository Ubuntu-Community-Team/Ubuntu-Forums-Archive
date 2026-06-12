---
title: "Que webcam me recomiendan para usar con 9.10 ?"
date: 2010-02-14
forum: Comunidad
---

### Post by rojojuan on 2010-02-14
Tengo que instalar una webcam en Ubuntu 9.10. Alguien compró alguna que ande bien en Capital Federal?
La pregunta es para tener la certeza que funcione bien y sin problemas.
Gracias desde ya por la ayuda

---

### Post by atari130xe on 2010-02-24
Hola como estás? te cuento que en mi caso uso una webcam Genius LooK 316 desde Ubuntu 7.04 en mi PC es totalmente compatible, buena definición, colores brillantes y la detecta con solo conectarla. Espero te sirva, saludos!

---

### Post by rojojuan on 2010-02-24
Muchas gracias, voy a ver si la consigo.


> **atari130xe said:**
> Hola como estás? te cuento que en mi caso uso una webcam Genius LooK 316 desde Ubuntu 7.04 en mi PC es totalmente compatible, buena definición, colores brillantes y la detecta con solo conectarla. Espero te sirva, saludos!

---

### Post by guillermolisi on 2010-02-24
Seria muy interesante y abriria las posibilidades entre los distintos fabricantes disponibles, saber que chip utiliza esa camara. De esa forma no importa ni el modelo ni la marca para saber si funcionara o no.

Con la camara conectada, si se pide un "lshw" en consola/terminal deberia indicar que chip usa.

---

### Post by atari130xe on 2010-02-24
> **guillermolisi said:**
> Seria muy interesante y abriria las posibilidades entre los distintos fabricantes disponibles, saber que chip utiliza esa camara. De esa forma no importa ni el modelo ni la marca para saber si funcionara o no.

Con la camara conectada, si se pide un "lshw" en consola/terminal deberia indicar que chip usa.

Bueno corrí lshw pero al menos yo no la encuentro:

```
josh-desktop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 2012MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.11.2
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: irq:11 ioport:fc00(size=32) ioport:4c00(size=64) ioport:4c40(size=64)
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:feb00000-feb000ff
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e800(size=16)
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d400(size=16) memory:fe02c000-fe02cfff
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH20NS10
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: EL00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c000(size=16) memory:fe02b000-fe02bfff
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master
          resources: ioport:a000(size=4096) memory:fdf00000-fdffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:01:01.0
             version: c0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32
             resources: irq:17 memory:fdfff000-fdfff7ff ioport:ac00(size=128)
        *-multimedia
             description: Multimedia controller
             product: SAA7130 Video Broadcast Decoder
             vendor: Philips Semiconductors
             physical id: 6
             bus info: pci@0000:01:06.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=saa7134 latency=32 maxlatency=38 mingnt=15
             resources: irq:16 memory:fdffe000-fdffe3ff
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: f3
          serial: 00:1e:8c:a0:21:63
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: irq:23 memory:fe02a000-fe02afff ioport:bc00(size=8)
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:24
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:25
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:26
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:27 ioport:9000(size=4096) memory:f8000000-fbffffff ioport:d0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G86 [GeForce 8400 GS]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:f8000000-f9ffffff ioport:9c00(size=128) memory:fbfe0000-fbffffff(prefetchable)
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

```

en cambio con un lsusb:

```
josh@josh-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0fce:d025 Sony Ericsson Mobile Communications AB 520 WMC Data Modem
Bus 002 Device 003: ID 0d8c:0201 C-Media Electronics, Inc. CM6501
[COLOR="Red"][FONT="Arial Black"][SIZE="4"]Bus 002 Device 002: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 Webcam[/SIZE][/FONT][/COLOR]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
josh@josh-desktop:~$ 

```


Espero les sea util :D[IMG]http://www.clickbox.com.ar/imagen/productos/2660a.jpg[/IMG]

> ESPECIFICACIONES TÉCNICAS

    *      Sensor imagen VGA (640 x 480) CMOS
    *      Tipo lentes foco manual
    *      Ratio de fotogramas: (1). 320 x 240 / hasta 30 fotogramas por segundo (con sistema recomendado) (2). 640 x 480 / hasta 15fps
    *      Interface USB1.1 USB 2.0
    *      Formato BMP/AVI
    *      Resolución captura: 1,280 x 960(DirectX9.0 posterior y software interpolación); 1,024 x 768 (DirectX9.0 posterior y software interpolación); 800 x 600 (DirectX9.0 posterior y software interpolación); 640 x 480 / 352 x 288 / 320 x 240 / 176 x 144 / 160 x 120
    *      Resolución AVI 640 x 480 (Máximo)
    *      Otros Compatible TWAIN
    *      Requerimientos de Sistema o PC o Pentium 4 1Ghz CPU o superior
          o 256MB RAM mínimo o Tarjeta Video 16bit con 16MB RAM mínimo
          o Pantalla (High Color) o superior o 10 MB de espcio libre en  disco o Windows 98SE, ME, 2000, XP o Mac OS 10.4 o [SIZE="2"][COLOR="Blue"]Linux 2.6.5[/COLOR][/SIZE] o Puerto USB disponible 

---

### Post by juancarlospaco on 2010-02-25
Hasta la fecha me andaron todas las Webcam con que me tope excepto la:
Genius iSlim 310

---

