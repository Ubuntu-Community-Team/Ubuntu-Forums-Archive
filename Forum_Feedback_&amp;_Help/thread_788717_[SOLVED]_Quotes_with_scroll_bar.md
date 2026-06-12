---
title: "[SOLVED] Quotes with scroll bar"
date: 2008-05-10
forum: Forum Feedback &amp; Help
---

### Post by ktechman on 2008-05-10
I have noticed that when some people post a quote it contains a scroll bar. How is that done? One of my quotes took up about half of a page.

---

### Post by Lord Xeb on 2008-05-10
Use [ CODE][  /CODE] or [ PHP][ /PHP] tags (just remove the spaces)


```
LOL
```


[PHP]ROFL[/PHP]


If they are really big, it will automatically make a scrollbar

```
root@nathan-laptop:/home/nathan# /etc/init.d/module-init-tools
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ] 
root@nathan-laptop:/home/nathan# update-modules
root@nathan-laptop:/home/nathan# update-modules
root@nathan-laptop:/home/nathan# sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
root@nathan-laptop:/home/nathan# sudo modprobe i2c-viapro
root@nathan-laptop:/home/nathan# sudo modprobe i2c-isa
root@nathan-laptop:/home/nathan# sudo modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/it87.ko): No such device
root@nathan-laptop:/home/nathan# sudo depmod -a
root@nathan-laptop:/home/nathan# update-modules
root@nathan-laptop:/home/nathan# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
root@nathan-laptop:/home/nathan# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
root@nathan-laptop:/home/nathan# sensors-detect
# sensors-detect revision 4609 (2007-07-14 09:28:39 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801FB ICH6

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 18e0 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              yNo


Next adapter: ISA main adapter (i2c-9191)
Do you want to scan it? (YES/no/selectively): Can't open /dev/i2c-9191

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xf911
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): y
AMD K8 thermal sensors...                                   No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or http://www.lm-sensors.org/wiki/FAQ
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
root@nathan-laptop:/home/nathan# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```

---

### Post by ktechman on 2008-05-10
I am very new here what is the procedure do I paste the quote between ```
(paste here)
``` or am I missing it? Just answered my own question.

---

### Post by -grubby on 2008-05-10
The disadvangtage with using code tags is that you can't specify the poster of that quote

EDIT: Actually, let me test

[code=nathangrubb]
Does this specify me in it?
[/code]

---

### Post by LaRoza on 2008-05-10
How about this?
[quote="Satan"]
```

root@nathan-laptop:/home/nathan# /etc/init.d/module-init-tools
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ] 
root@nathan-laptop:/home/nathan# update-modules
root@nathan-laptop:/home/nathan# update-modules
root@nathan-laptop:/home/nathan# sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
root@nathan-laptop:/home/nathan# sudo modprobe i2c-viapro
root@nathan-laptop:/home/nathan# sudo modprobe i2c-isa
root@nathan-laptop:/home/nathan# sudo modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/it87.ko): No such device
root@nathan-laptop:/home/nathan# sudo depmod -a
root@nathan-laptop:/home/nathan# update-modules
root@nathan-laptop:/home/nathan# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
root@nathan-laptop:/home/nathan# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
root@nathan-laptop:/home/nathan# sensors-detect
# sensors-detect revision 4609 (2007-07-14 09:28:39 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801FB ICH6

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 18e0 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              yNo


Next adapter: ISA main adapter (i2c-9191)
Do you want to scan it? (YES/no/selectively): Can't open /dev/i2c-9191

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xf911
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): y
AMD K8 thermal sensors...                                   No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or http://www.lm-sensors.org/wiki/FAQ
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
root@nathan-laptop:/home/nathan# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```
[/quote]

---

### Post by -grubby on 2008-05-10
Yes it does, thanks LaRoza

---

### Post by ktechman on 2008-05-10
So how would the syntax be laid out [quote]```
paste
```? That didn't turn out right.

---

### Post by p_quarles on 2008-05-10
> **ktechman said:**
> So how would the syntax be laid out [quote]```
paste
```? That didn't turn out right.
Looks like you just forgot to close the quote tag. You have the right idea.

---

### Post by ktechman on 2008-05-12
Here goes > ```
 paste 
``` Is that it? Thank you for your help

                          Regards

---

### Post by Lord Xeb on 2008-05-12
If you want to quote someone  that has a code in it, do as above or ust copy and past what you want into [ QUOTE][ /QUOTE]  and it will be quoted. If you want code in the quote, press quote, but put the code tags around what you want to be in code then press  Post

---

