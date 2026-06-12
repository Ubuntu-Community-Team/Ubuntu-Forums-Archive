---
title: "Asus L3H modem problem"
date: 2006-05-21
forum: Desktop Environments
---

### Post by penguinfan on 2006-05-21
I need instructions on how to make my modem work. 

this is what scanModem says

~$ sudo ./scanModem
Password:

UPDATE=2005_April_19
ONLY use scanModem downloaded as: [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

 ./scanModem should ONLY be run within a Linux/UNIX partition.
   If within a MicroSoft/DOS partition, abort with Ctrl-C now !!!
   Copy scanModem.gz to your Linux partition and restart.

PCIBUS=0000:00:02.6

Providing detail for device at PCI_bus 0000:00:02.6
  with vendor-ID:device-ID
            ----:----
Class 0703: 1039:7013   Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
  SubSystem 1043:1696   Asustek Computer, Inc.: Unknown device 1696
0000:00:02.6 0703: 1039:7013 (rev a0)
        Flags: medium devsel, IRQ 11
        I/O ports at b400 [size=256]
        I/O ports at b000 [size=128]

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 1039:7013 1043:1696 debian 2.6.12-10-386 3.4.5 4.0.2    i686

 The soft modem Subsystem operates under a controller
   1039:7013  SIS 630
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:
        Pctel
        AgereSystems
        Conexant
        Intel
        Smartlink
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

---

