---
title: "sensors not working on older hardware - asus a7m266"
date: 2010-05-16
forum: Desktop Environments
---

### Post by graysky on 2010-05-16
Recently had to reinstall Arch i686 after an HD crash.  I can't for the life of me get sensors to work with this board and I know it worked before!  It's an old Asus A7M266 (via chipset).

Thoughts?

```
# sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# Board: ASUSTeK Computer INC. <A7M266>

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no):
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          Success!
    (driver `via686a')
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no):
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no):
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no):
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no):
Using driver `i2c-viapro' for device 0000:00:04.4: VIA Technologies VT82C686 Apollo ACPI

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively):

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively):

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively):

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `via686a':
  * Chip `VIA VT82C686 Integrated Sensors' (confidence: 9)

Do you want to overwrite /etc/conf.d/lm_sensors? (YES/no):
Copy prog/init/lm_sensors.init to /etc/rc.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.

[root@reborn squ]# modprobe via686a
[root@reborn squ]# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

---

### Post by graysky on 2010-05-16
Interesting find on my part:
```
$ dmesg | grep [S,s]ensor
via686a 0000:00:04.4: Sensors disabled, enable with force_addr=0xe300
```
So I added the force_addr as a token to my modprobe which was accepted by the shell.
```
# modprobe via686a force_addr=0xe300
```
And for some reason I remember needing both the via686a module as well as the w83781d module.  So I modprobed the w83781d module too and sensors works again!

```
$ sensors
as99127f-i2c-0-2d
Adapter: SMBus Via Pro adapter at e800
in0:         +1.81 V  (min =  +1.65 V, max =  +2.05 V)   
in1:         +2.46 V  (min =  +1.65 V, max =  +2.05 V)   
in2:         +3.23 V  (min =  +2.96 V, max =  +3.63 V)   
in3:         +2.98 V  (min =  +2.67 V, max =  +3.28 V)   
in4:         +3.23 V  (min =  +2.51 V, max =  +3.79 V)   
in5:         +0.53 V  (min =  +0.08 V, max =  +1.02 V)   
in6:         +0.88 V  (min =  +0.54 V, max =  +1.17 V)   
temp1:       +35.0°C  (high =  +0.0°C, hyst = -128.0°C)  
temp2:       +59.0°C  (high = +100.0°C, hyst = +75.0°C)  
cpu0_vid:   +1.750 V
beep_enable:enabled
```
I haven't tested this on a reboot yet but I think I can add the following to /etc/modprobe.d/modprobe.conf:

```
via686a force_addr=0xe300
```
From there it should be a trivial matter to load both modules in my MODULES array in /etc/rc.conf:

```
MODULES=(!snd_pcsp !pcspkr !lirc_streamzap !lirc_dev !rtl8187 !floppy w83781d via686a)
```
We'll see if it survives a reboot when the backup finishes in 10 h :p

---

