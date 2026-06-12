---
title: "Troubles lm-sensors on PowerEdge 700"
date: 2007-06-06
forum: Dell  Ubuntu Support
---

### Post by bluedeep on 2007-06-06
> 
server:/home/terminet# sensors-detect
# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no):
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH7

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at ece0
Do you want to scan it? (YES/no/selectively):
Client found at address 0x08
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Handled by driver `eeprom' (already loaded), chip type `eeprom'
Client found at address 0x52
Handled by driver `eeprom' (already loaded), chip type `eeprom'
Client found at address 0x69

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no):
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Winbond W83627HF' at 0x290...                  No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `AMD K8 thermal sensors'...                     No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no):
Probing for Super-I/O at 0x2e/0x2f
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0x7901
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x7901
Trying family `VIA/Winbond/Fintek'...                       No
Probing for Super-I/O at 0x4e/0x4f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at ece0'
    Busdriver `i2c-i801', I2C address 0x50
    Chip `eeprom' (confidence: 6)
  * Bus `SMBus I801 adapter at ece0'
    Busdriver `i2c-i801', I2C address 0x52
    Chip `eeprom' (confidence: 6)

  EEPROMs are *NOT* sensors! They are data storage chips commonly
  found on memory modules (SPD), in monitors (EDID), or in some
  laptops, for example.

I will now generate the commands needed to load the required modules.
Just press ENTER to continue:

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# Chip drivers
eeprom
#----cut here----


Do you want to add these lines to /etc/modules automatically? (yes/NO)
server:/home/terminet# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
server:/home/terminet#


Modules are loaded, but still not working, any idea?

---

