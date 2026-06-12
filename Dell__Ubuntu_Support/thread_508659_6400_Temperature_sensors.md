---
title: "6400 Temperature sensors"
date: 2007-07-24
forum: Dell  Ubuntu Support
---

### Post by Merritt.kr on 2007-07-24
I've been trying for two days now to get some temperature readings off my Inspiron 6400.

In Vista, i8kfangui got me reading all my temperatures just fine, so I KNOW this little thing has sensors. And obviously the BIOS is okay, if it was reading them in Windows.

I've been trying to get Im-sensors going, but no luck. Here's my setup:

```
kristen@Merritt:~$ sudo sensors-detect
Password:
# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
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

Next adapter: SMBus I801 adapter at 10c0
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x08
Client found at address 0x30
Client found at address 0x32
Client found at address 0x50
Handled by driver `eeprom' (already loaded), chip type `eeprom'
Client found at address 0x52
Handled by driver `eeprom' (already loaded), chip type `eeprom'
Client found at address 0x69

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
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
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `ITE'...                                      Yes
Found unknown chip with ID 0x2803
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x2803
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
  * Bus `SMBus I801 adapter at 10c0'
    Busdriver `i2c-i801', I2C address 0x50
    Chip `eeprom' (confidence: 6)
  * Bus `SMBus I801 adapter at 10c0'
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
```

This is all I get:

```
kristen@Merritt:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

As well as this:

```
kristen@Merritt:~$ acpi -t
     Battery 1: charged, 100%
     Thermal 1: ok, 61.0 degrees C
```

Does anyone know how to get Im-sensors to work, or know of a program that will work with the 6400?

My desktop computer is having major temp problems at the moment, and being the OCD person I am, I'd really like to be able to monitor all of my sensors, now.

Thanks in advance for any advice or input!

---

### Post by myoungf1 on 2007-07-24
Did you type yes to have the sensors found automatically written to /etc/modules ?

---

### Post by Merritt.kr on 2007-07-24
Yes, I did. I also tried entering them manually and in reverse order, as suggested by a Im-sensors guide on these forums. Both gave the no sensors detected message, however. Though in reverse order doesn't do much since it seems to have only detected one sensor!

---

### Post by RangerDanger on 2007-07-24
> **Merritt.kr said:**
> Yes, I did. I also tried entering them manually and in reverse order, as suggested by a Im-sensors guide on these forums. Both gave the no sensors detected message, however. Though in reverse order doesn't do much since it seems to have only detected one sensor!

lm-sensors will NOT work with Dell computers.  It does not matter what you try.

---

### Post by Merritt.kr on 2007-07-24
Okay. I've heard it doesn't like laptops.

Is there ANY program for Linux that will work? Doesn't have to be Im-sensors... That was just the one I heard about.

---

### Post by RangerDanger on 2007-07-24
Fan and temp control
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds in settings - plugins - Dell i8k


This is a program with a I8kfan plugin.  It works just tried it last night.

---

### Post by jb1789 on 2007-07-24
To check the temperature of the processor using the terminal, you can try

watch acpi -V

(or watch acpi -Vf      for Fahrenheit)

---

### Post by Merritt.kr on 2007-07-24
Actually I've tried Gkrellm.. It work as advertised, however I don't just want to control my fans, and I'd like to see the temperature of more than just the CPU. I know I have temp sensors for the CPU, HDD, GPU, motherboard.... I'd like to see them all, get a feel for how my machine is doing inside. Gkrellm, as far as I've been able to get, will only display the CPU temp.

---

### Post by RangerDanger on 2007-07-24
> **Merritt.kr said:**
> Actually I've tried Gkrellm.. It work as advertised, however I don't just want to control my fans, and I'd like to see the temperature of more than just the CPU. I know I have temp sensors for the CPU, HDD, GPU, motherboard.... I'd like to see them all, get a feel for how my machine is doing inside. Gkrellm, as far as I've been able to get, will only display the CPU temp.

I have searched all over and cannot find anything that works with dells at least on Linux.  I personally would like something like Notebook Hardware Control.  It would be nice if someone could get lm-sensors working, but it does not seem possible.

---

### Post by Merritt.kr on 2007-07-24
I find it quite strange that there just seems to be NOTHING that works under Linux, even though there are tools that work under Windows. ESPECIALLY since Dell is now selling their systems with Ubuntu! I checked their Linux tools, but they have nothing for monitoring resources under Linux. :(

---

### Post by RangerDanger on 2007-07-24
Dell for some reason does not use the same sensor system that most other notebook manufacturers do.

---

### Post by Merritt.kr on 2007-07-24
I intend to get into programming, but that won't be for a while, and even then I have to learn more than my knowledge of html. ;) Maybe then I can write something proper for Dells on Linux. lol

---

### Post by tgm4883 on 2007-07-25
you can install hddtemp to watch the temperature on your hard drive.  I use that and the acpi sensor with conky to monitor my e1505

---

