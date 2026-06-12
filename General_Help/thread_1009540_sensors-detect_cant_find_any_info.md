---
title: "sensors-detect cant find any info?"
date: 2008-12-12
forum: General Help
---

### Post by sdowney717 on 2008-12-12
this is a compaq intel board 2.4ghz

```
scott@scott-desktop:~$ sudo sensors-detect 
[sudo] password for scott: 
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Sorry, no supported PCI bus adapters found.

If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: ivtv i2c driver #0 (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found `SMSC LPC47B367-NC Super IO'                          
    (no hardware monitoring capabilities)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
http://www.lm-sensors.org/wiki/FAQ/Chapter3 for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
scott@scott-desktop:~$ 

```

---

### Post by Arup on 2008-12-12
Have you installed lm-sensors? Do a sudo apt-get install lm-sensors and then do sudo sensors-detect and see what it finds.

---

### Post by SmokinJuan on 2008-12-13
you might try this:

see /usr/share/doc/lm-sensors/examples/hotplug/README.p4b

```
sudo /usr/share/doc/lm-sensors/examples/hotplug/unhide_ICH_SMBus
sudo modprobe thmc50
sudo modprobe i2c-i801
```

worked for this compaq, but i dont have it installed now so the details are fuzzy.  your modprobe statements will proly be different.

---

### Post by sdowney717 on 2008-12-13
yes. lm-sensors is installed

```
scott@scott-desktop:~$ sudo /usr/share/doc/lm-sensors/examples/hotplug/unhide_ICH_SMBus
[sudo] password for scott: 
Enabling SMBus PCI device ...
Rescanning the bus ...
/usr/share/doc/lm-sensors/examples/hotplug/unhide_ICH_SMBus: line 56: /sys/bus/pci/slots/0000:00:1f.0/power: No such file or directory
Failed to enable the SMBUS

scott@scott-desktop:~$ sudo modprobe thmc50
scott@scott-desktop:~$ sudo modprobe i2c-i801

scott@scott-desktop:~$ sudo /usr/share/doc/lm-sensors/examples/hotplug/unhide_ICH_SMBus
Enabling SMBus PCI device ...
Rescanning the bus ...
/usr/share/doc/lm-sensors/examples/hotplug/unhide_ICH_SMBus: line 56: /sys/bus/pci/slots/0000:00:1f.0/power: No such file or directory
Failed to enable the SMBUS
scott@scott-desktop:~$ 

```

---

### Post by SmokinJuan on 2008-12-13
Did you try to run sensors-detect after that? If I'm remembering right, I'd get the "Failed to enable the SMBUS" occasionally but sensors would work anyway.

---

### Post by sdowney717 on 2008-12-14
> Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
[http://www.lm-sensors.org/wiki/FAQ/Chapter3](http://www.lm-sensors.org/wiki/FAQ/Chapter3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.


just tried it again and perhaps not supported yet.
Reason I wanted to do this was a conky file showing some system temps.

---

### Post by SmokinJuan on 2008-12-14
Sorry, that's all I got.  When I searched the subject for my machine I became convinced that sensors just flat-out wouldn't work thanks to the closed nature of the name brand.  I just stumbled across the unhide_ICH_SMBus solution by accident one day and all it gave was motherboard and processor temperatures - not the fan speeds like I needed.  Good luck.

---

