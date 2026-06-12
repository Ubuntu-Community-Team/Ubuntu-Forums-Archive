---
title: "Ayuda sobre Distribución liviana"
date: 2010-04-01
forum: Comunidad
---

### Post by Mustaine666 on 2010-04-01
Gente de Ubuntu forums.. siempre me ayudaron en todo lo que pudieron.. resulta que luego de la instalación de ubuntu 9.10 .. 
no anduvo bien.. como anduvieron las versiones anteriones..
se tilda.. si si .. ubuntu se tilda.. 
me parece que puede ser por la computadora que ya esta vieja.. 
es una
Intel Celeron 2.4Ghz
1.24 Gb de memoria
64mb de video onboard
...

luego de tanta introduccion vienen mis dudas..
seria mejor instalarle Lubuntu?.. que vi que es una distribucion para ordenadores mas viejos! .. 
que otra distribucion me recomendarian? ..

lo unico que tengo como condicion para la distribucion es que soporte el interprete GHCI de Haskell.. puesto que lo necesito para la facultad...

desde ya muchas gracias.. espero sus respuestas

pd: yo nombre a lubuntu.. por que es la unica distribucion liviana sobre la que lei.. estoy dispuesto a cualquier distribucion liviana

---

### Post by z37a on 2010-04-01
> **Mustaine666 said:**
> Gente de Ubuntu forums.. siempre me ayudaron en todo lo que pudieron.. resulta que luego de la instalación de ubuntu 9.10 .. 
no anduvo bien.. como anduvieron las versiones anteriones..
se tilda.. si si .. ubuntu se tilda.. 
me parece que puede ser por la computadora que ya esta vieja.. 
es una
Intel Celeron 2.4Ghz
1.24 Gb de memoria
64mb de video onboard
...

luego de tanta introduccion vienen mis dudas..
seria mejor instalarle Lubuntu?.. que vi que es una distribucion para ordenadores mas viejos! .. 
que otra distribucion me recomendarian? ..

lo unico que tengo como condicion para la distribucion es que soporte el interprete GHCI de Haskell.. puesto que lo necesito para la facultad...

desde ya muchas gracias.. espero sus respuestas

pd: yo nombre a lubuntu.. por que es la unica distribucion liviana sobre la que leí.. estoy dispuesto a cualquier distribucion liviana

Tenes Xubuntu también que es un tanto mas liviana que Ubuntu y Kubuntu.
Pero la verdad es que ese equipo no es tan malo que digamos como ara correr un Ubuntu, cumple lo mas bien con lo recomendado. Que versión instalaste de Ubuntu? una estable o Lucid(10.04)? Puede ser que el problema ahí venga por otro lado, por si las dudas si podes hace un lshw en una terminal y subí el resultado del mismo, eso ayudaría a saber que hardware tenes específicamente.

---

### Post by Mustaine666 on 2010-04-01
Instale Ubuntu Version 9.10 .. desde el cd.. que te manda shipit de canonical.. 

el resultado de lshw

```

mustaine@mustaine-desktop:~$ sudo lshw
[sudo] password for mustaine: 
mustaine-desktop          
    description: Mini Tower Computer
    product: DQ035A-AKV S5010LS LA310
    vendor: Compaq Presario 061
    version: 0n31411RE101ECHO 10
    serial: MXK3400ZRV
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=mini-tower uuid=00D7D038-C0F3-D711-8A0B-8AE127278698
  *-core
       description: Motherboard
       product: P4G533LA
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: 3.16 (08/05/2003)
          size: 64KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: PGA 478
          size: 2400MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 8KiB
             capacity: 32KiB
             capabilities: pipeline-burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 128KiB
             capacity: 1MiB
             capabilities: pipeline-burst internal write-back
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 1280MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff(prefetchable)
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff(prefetchable) memory:e7800000-e787ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d400(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d000(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e7000000-e70003ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:b000(size=4096) memory:e6000000-e6ffffff
           *-communication UNCLAIMED
                description: Communication controller
                product: LT WinModem
                vendor: Agere Systems
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=14 mingnt=252
                resources: memory:e6800000-e68000ff ioport:b800(size=8) ioport:b400(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: d
                bus info: pci@0000:01:0d.0
                logical name: eth0
                version: 10
                serial: 00:0c:6e:c5:1d:64
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
                resources: irq:17 ioport:b000(size=256) memory:e6000000-e60000ff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:9400(size=16) memory:e5800000-e58003ff
           *-disk:0
                description: ATA Disk
                product: WDC WD400BB-75DE
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAD1A074759
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0ff40ff4
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 808c6b7d-396e-fc4c-9fe4-9fb333344810
                   size: 8504MiB
                   capacity: 8504MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-01-22 08:36:21 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 28GiB
           *-disk:1
                description: ATA Disk
                product: WDC WD400EB-11CP
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 06.0
                serial: WD-WCAATF498619
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=578d578d
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: 1ce5406b-7093-481e-bcf6-3a51c93fe9a2
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-03-27 18:07:10 filesystem=ext4 lastmountpoint=/&#65533;7&#65533;&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;{&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;I^&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;`&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533; modified=2010-04-01 11:12:02 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-04-01 13:14:39 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 1906MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      logical name: /home
                      capacity: 26GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7190A
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:e800(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e100(size=64) memory:50000000-500001ff memory:50000200-500002ff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:1c:a2:3a:36:75
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=10.0.0.10 link=yes multicast=yes
mustaine@mustaine-desktop:~$ 

```



pd: segun windows tengo 64mb de video.. y segun linux 32mb .. que loco! :lolflag:

---

### Post by harryscode on 2010-04-01
Como te dijo z73a esa maquina deberia funcionar sin problemas con Ubuntu, mi máquina es un Celeron 2,14ghz con 2gh de ram y una onboard de 64 y le sobra cpu para funcionar. El problema debe venir por otro lado. Escuche tambien que (y tambien le pasó a mi cuñado) hubo gente que tuvo problemas con el cd de canonical, a mi cuñado le preste el cd que baje de la web y lo pudo instalar y correr sin problemas.
Por distro liviana, yo probaria con Xubuntu antes de lubuntu, para esa máquina deberia volar xubuntu. 
Exitos

---

### Post by Mustaine666 on 2010-04-01
me resulta rarisimo.. por q la instalacion la verdad que fue rapida sin problemas.. pero cuando prendo la computadora.. abro emesene google chrome.. navego 5 minutos.. y se tilda.. no anda nada.. no se que opinan.. me parece muy raro que se cuelgue ubuntu..

---

### Post by guillermolisi on 2010-04-01
> *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             [COLOR=Blue]width: 32 bits[/COLOR]
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff(prefetchable) memory:e7800000-e787ffff
Que diga width no implica que tenga esa cantidad de memoria asignada. Es el ancho de banda para la transferencia de datos con el bus de la motherboard, por eso habla de bits no de Mbytes.

Por lo que decis que se cuelga cuando la empezas a usar, me suena a algun problema de hardware, RAM quizas.
Que pasa si solo dejas la placa de 1Gb RAM ? Se sigue colgando ? Yo haria la prueba.

---

### Post by Mustaine666 on 2010-04-01
ahora lo pruebo.. y les cuento..

---

### Post by Mustaine666 on 2010-04-01
por ahora no pasa nada.. no se colgo.. 

a su vez me parece raro q ocurra en ubuntu.. y windows no!

pd: se me acaba de colgar.. mientras releia.. el post!..

---

### Post by z37a on 2010-04-01
> **Mustaine666 said:**
> por ahora no pasa nada.. no se colgo.. 

a su vez me parece raro q ocurra en ubuntu.. y windows no!

pd: se me acaba de colgar.. mientras releia.. el post!..

La fuente es muy vieja? Otra cosa, los capacitores(Popr si las dudas aclaro, son unos cilindros con una chapita en la parte de arriba) del mother, hay alguno que se encuentre "hinchado"(Si la chapita se encuentra con forma de huevo, lo normal es que este plana)? Puede sonar raro pero puede pasar, mas si es un mother bastante antiguo!

PD: Es muy posible que halla problemas de hard ahí, capaz que en win todavía no te salto, pero de seguro puede que también te ande algo inestable(o inestabilidad de win + de hard se anulan :D )

---

### Post by Mister X on 2010-04-02
con esa maquina Ubuntu tiene que correr perfectamente, te lo digo porque le instale a mi viejo en una maquina similar (inclusive con menos RAM).

para mi es un problema de hard. podes probar ejecutando el memtest al inicio.

---

### Post by PoNcHo87 on 2010-04-27
> **Mustaine666 said:**
> abro emesene google chrome.. navego 5 minutos.. y se tilda.. no anda nada.. no se que opinan.. me parece muy raro que se cuelgue ubuntu..

A mi me paso que cuando instale el Google Chrome se me hizo muy lento e inclusive se tildaba en el uso y navegacion, yo tengo un equipo mucho mas chiquito que el tuyo y funciona perfecto, EXCEPTO cuando abro el Google Chrome, el resto anda genial.-

---

### Post by alfplayer on 2010-04-27
De Google Chrome para linux la versión más confiable es la llamada "beta", hay otras menos confiables como la "unstable".

---

### Post by PoNcHo87 on 2010-04-28
Claro, yo instale la "beta", pero no sobrevivió ni 2 dias...

---

### Post by leonardomdq on 2010-04-28
Con 9.10 me paso tambien esos cuelgues, ahora con lucid RC mas, ayer 8 (ocho) en el dia, no se que sera....yo esperaria mañana la final de lucid lynx.

PD: Mustaine666 si lo solucionaste lo del cuelgue comentalo asi si alguno le pasa lo mismo puede solucionar el problema.

---

