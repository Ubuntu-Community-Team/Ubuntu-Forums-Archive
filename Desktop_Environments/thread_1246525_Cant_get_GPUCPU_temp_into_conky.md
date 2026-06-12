---
title: "Cant get GPU/CPU temp into conky"
date: 2009-08-21
forum: Desktop Environments
---

### Post by Ice799 on 2009-08-21
i've searched these forums for a few days and haven't found the answer to my problem even googled it for hours on end.

I have Sensors installed

```
ice@ice-desktop:~$ sensors
w83627ehf-isa-0290
Adapter: ISA adapter
VCore:       +1.30 V  (min =  +0.00 V, max =  +1.85 V)   
in1:        +12.14 V  (min =  +0.00 V, max =  +1.69 V)   ALARM
AVCC:        +3.28 V  (min =  +1.02 V, max =  +0.00 V)   ALARM
3VCC:        +3.26 V  (min =  +0.51 V, max =  +0.26 V)   ALARM
in4:         +2.04 V  (min =  +0.26 V, max =  +0.00 V)   ALARM
in5:         +1.60 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
in6:         +6.30 V  (min =  +1.64 V, max =  +0.00 V)   ALARM
VSB:         +3.26 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
VBAT:        +3.25 V  (min =  +0.00 V, max =  +0.02 V)   ALARM
in9:         +2.04 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
Case Fan:      0 RPM  (min =    0 RPM, div = 128)  ALARM
CPU Fan:    4623 RPM  (min =    0 RPM, div = 4)  ALARM
Aux Fan:    2033 RPM  (min =    0 RPM, div = 4)  ALARM
fan5:          0 RPM  (min =    0 RPM, div = 64)
Sys Temp:    +48.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPU Temp:    +63.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:    +44.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor

```

```
ice@ice-desktop:~$ sudo sensors-detect
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801FB ICH6

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): y
Module loaded successfully.
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

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6650/MAX6651'...                      No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): y

Next adapter: SMBus I801 adapter at 0400 (i2c-3)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x4f
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

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
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627EHF/EF/EHG/EG Super IO Sensors'        Success!
    (address 0x290, driver `w83627ehf')
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

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627EHF/EF/EHG/EG Super IO Sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627ehf
#----cut here----


```

Can someone please help me?
Ive tried various commands in conky but nothing.

---

### Post by anthw27 on 2009-08-21
Hey Ice799,

The thread you need to see is here

[http://ubuntuforums.org/showthread.php?p=6365702](http://ubuntuforums.org/showthread.php?p=6365702)

But remember Jaunty is still in development....

Also check here for support contact in regards to conky.

[http://sourceforge.net/projects/conky/support](http://sourceforge.net/projects/conky/support)

---

### Post by Ice799 on 2009-08-22
That really didn't even remotely help.... Sorry to say.
I just need the commands to add it to conky.
I need to know if there's any extra files I need to add or programs I need to get?

---

### Post by |Porsche on 2009-08-22
Can you get the output in a terminal? If so you can execute the command from conky and display it using the execi conky variable. 
See [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html) for all other variables.

Also checkout the conky setups on this thread [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865) and if you find what you are looking for you can look at their .conkyrc.

---

### Post by Ice799 on 2009-08-22
Conky runs fine... Just need to know what to do in order to get the GPU/CPU temp.

Ive tried:
```
Apcitemp
```
but just get 0

---

### Post by |Porsche on 2009-08-22
This are my lines of code:
Case: ${hwmon 1 temp 1}C ${hwmon 0 fan 4}rpm
CPU:  ${hwmon 1 temp 2}C ${hwmon 1 fan 2}rpm

HINT: You might have different sensors,but you can use hwmon on conky to display them. The GPU is a different story.

---

### Post by Ice799 on 2009-08-23
```
CPU: ${hwmon 1 temp 2}C ${hwmon 1 fan 2}rpm
```

Not working for me. Thanks thou.

Anythings else guys?

---

### Post by Aubergines on 2009-08-23
Change the number 5 to how many seconds between each time you want the script to run.

```
CPU: ${execi 5 sensors | grep "CPU Temp" | cut -c15-21
```

---

### Post by Ice799 on 2009-08-23
sweetness it works expects i have a wierd A in the middle of it....
Edit:
Changed:
```
CPU: ${execi 5 sensors | grep "CPU Temp" | cut -c15-21}
```
to
```
CPU: ${execi 5 sensors | grep "CPU Temp" | cut -c15-18|
```


Anyone know how to get GPU temp and %?

---

### Post by frigginacky on 2009-08-23
If you have an nvidia GPU and nvidia-settings installed, try this:

In a terminal, type
```
nvidia-settings -query GPUCoreTemp
```

You should get something like this:
```
Attribute 'GPUCoreTemp' (FrigMachine:0.0): 50.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.
```

On the first line, figure out which characters are displaying the temperature.  In my example, the temperature (50) is characters 46-47.

In your .conkyrc, add this:

```
${execi 2 nvidia-settings -query GPUCoreTemp | grep Attribute | cut -c46-47}
```

Replace 2 with your desired update frequency in seconds, and 46-47 with the range of characters you want to display, and BOOM!  You should have your GPU temp.

If you don't have an nvidia card, I'm clueless.  Sorry.

---

### Post by Ice799 on 2009-08-24
> **frigginacky said:**
> 
In your .conkyrc, add this:

```
${execi 2 nvidia-settings -query GPUCoreTemp | grep Attribute | cut -c46-47}
```
I do have nvidia card, worked like a charm thanks.

---

### Post by ImbaDaimon on 2009-09-10
> **frigginacky said:**
> If you have an nvidia GPU and nvidia-settings installed, try this:

In a terminal, type
```
nvidia-settings -query GPUCoreTemp
```

You should get something like this:
```
Attribute 'GPUCoreTemp' (FrigMachine:0.0): 50.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.
```

On the first line, figure out which characters are displaying the temperature.  In my example, the temperature (50) is characters 46-47.

In your .conkyrc, add this:

```
${execi 2 nvidia-settings -query GPUCoreTemp | grep Attribute | cut -c46-47}
```

Replace 2 with your desired update frequency in seconds, and 46-47 with the range of characters you want to display, and BOOM!  You should have your GPU temp.

If you don't have an nvidia card, I'm clueless.  Sorry.

In my Laptop i have nVidia 9600M GT Card and this is working :D

for me
```
GPU Temp: ${execi 1 nvidia-settings -query GPUCoreTemp | grep Attribute | cut -c45-46}°C
```

ty a lot

---

### Post by Nikos.Alexandris on 2009-11-05
> **frigginacky said:**
> If you have an nvidia GPU and nvidia-settings installed, try this:

In a terminal, type
```
nvidia-settings -query GPUCoreTemp
```

You should get something like this:
```
Attribute 'GPUCoreTemp' (FrigMachine:0.0): 50.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.
```

On the first line, figure out which characters are displaying the temperature.  In my example, the temperature (50) is characters 46-47.

In your .conkyrc, add this:

```
${execi 2 nvidia-settings -query GPUCoreTemp | grep Attribute | cut -c46-47}
```

Replace 2 with your desired update frequency in seconds, and 46-47 with the range of characters you want to display, and BOOM!  You should have your GPU temp.

If you don't have an nvidia card, I'm clueless.  Sorry.

Perfect, thanks! For me characters 43-44 were the ones.

Regards

p.s. Looking at the "variables" [1] it also works using "${nvidia temp}" and there are also more options (e.g. gpufreq).

[1] [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

