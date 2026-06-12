---
title: "need help with LM-Sensors"
date: 2006-09-20
forum: Desktop Environments
---

### Post by maddbaron on 2006-09-20
I tried get this error after following the instructions on this page:
[http://www.debian-administration.org/articles/327](http://www.debian-administration.org/articles/327)

> sensors-detect
# sensors-detect revision 1.393 (2005/08/30 18:51:1

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
You do not need any special privileges for this.
Do you want to probe now? (YES/no): Yes
Probing for PCI bus adapters...
Use driver `i2c-sis96x' for device 00:02.1: Silicon Integrated Systems SMBus Controller
Probe succesfully concluded.

As you are not root, we can't load adapter modules. We will only scan
already loaded adapters.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
If it is built-in into your kernel, you can safely skip this.
i2c-dev is already loaded.

We are now going to do the adapter probings. Some adapters may hang halfway
through; we can't really help that. Also, some chips will be double detected;
we choose the one with the highest confidence value in that case.
If you found that the adapter hung after probing a certain address, you can
specify that address to remain unprobed. That often
includes address 0x69 (clock chip).

Next adapter: SiS96x SMBus adapter at 0x8100
Do you want to scan it? (YES/no/selectively): YES
Can't open /dev/i2c-0

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

As you are not root, we shall skip this step.

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

As you are not root, we shall skip this step.

Sorry, no chips were detected.
Either your sensors are not supported, or they are
connected to an I2C bus adapter that we do not support.
See doc/FAQ, doc/lm_sensors-FAQ.html, or
[http://www2.lm-sensors.nu/~lm78/cvs/...nsors-FAQ.html](http://www2.lm-sensors.nu/~lm78/cvs/...nsors-FAQ.html)
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, see
[http://secure.netroedge.com/~lm78/newdrivers.html](http://secure.netroedge.com/~lm78/newdrivers.html) for driver status.

> sensors-detect
No i2c device files found. Use prog/mkdev/mkdev.sh to create them.


This is like another language for me. Can someone tell me in Layman's terms what to do to get sensors working? Please?

---

### Post by Zed on 2006-09-20
See [here.](http://ubuntuforums.org/showthread.php?t=2780) The language isn't especially for the layperson, I fear, but I don't know an easier solution.

---

### Post by Zed on 2006-09-20
Ah, I see now you've posted to that thread. Did you follow the instructions in the original article in that thread, and saved and ran mkdev.sh?

---

### Post by maddbaron on 2006-09-20
i have no idea how to even get to mkdev.sh it said create so i tried make then mkdev.sh  i assume that was wrong b/c it didn't work lol...how do i do that?

---

### Post by Zed on 2006-09-20
I'll assume you have a regular Ubuntu installation with the Gnome desktop. I don't have a Dapper installation on me, but I do have an Edgy installation, so I hope the details of menu selections, below, haven't changed.

From the main desktop menu, select Applications->Accessories->Text Editor. This will laurch gedit, the default text editor for Gnome.

In Firefox, follow my link, above, to the first page of the sensors howto thread. With your mouse, select the text under item 2. there, from ```
#!/bin/bash
``` through ```
# end of file
```, inclusively (i.e. including both those lines), and copy it (either with Edit->Copy from Firefox's menu, or by hitting Ctrl-C.) 

Then click on your gedit window again, and click its paste icon. You should see the text you selected from the web page. Click the save button, and a "Save as..." dialogue will pop up. Enter the name 'mkdev.sh' and in the "save in folder" pulldown menu, select Desktop.

(All of that takes longer to say than to do...)

Open a terminal window. issue:

```

cd ~/Desktop
chmod +x mkdev.sh
sudo ./mkdev.sh

```

Continue to follow the directions in the HOWTO. Note that, like it says, when you run sensors-detect, you have to use ```
sudo
``` to use superuser permissions. If you're logged in with the account you created during the Ubuntu installation, issuing a command with sudo will prompt you for a password -- just use your account's login password.

Good luck!

---

### Post by maddbaron on 2006-09-20
Thank you so much, I am using Kubuntu but the instructions can't be that different so I did them using KATE but i think I did the last parts wrong here is what I have as result:

> 
maddbaron@baronnet:~/Desktop$ chmod +x mkdev.sh
maddbaron@baronnet:~/Desktop$ sudo ./mkdev.sh
Password:
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31
maddbaron@baronnet:~/Desktop$ sudo sensors-detect
# sensors-detect revision 1.393 (2005/08/30 18:51:18)

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): YES
Probing for PCI bus adapters...
Use driver `i2c-sis96x' for device 00:02.1: Silicon Integrated Systems SMBus Controller
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Module `i2c-sis96x' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
 i2c-dev is not loaded. Do you want to load it now? (YES/no): YES
 Module loaded succesfully.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: SiS96x SMBus adapter at 0x8100
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x08
Client found at address 0x10
Client found at address 0x50
Probing for `SPD EEPROM'... Success!
    (confidence 8, driver `eeprom')
Probing for `DDC monitor'... Failed!
Probing for `Maxim MAX6900'... Failed!
Client found at address 0x51
Probing for `SPD EEPROM'... Success!
    (confidence 8, driver `eeprom')
Client found at address 0x69

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): YES
Probing for `National Semiconductor LM78'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
  Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627EHF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83697HF'
  Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
  Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
  Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
  Trying general detect... Failed!
Probing for `ITE IT8712F'
  Trying address 0x0290... Failed!
Probing for `ITE IT8705F / SiS 950'
  Trying address 0x0290... Failed!
Probing for `IPMI BMC KCS'
  Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
  Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for `ITE 8702F Super IO Sensors'
  Failed! (0xec11)
Probing for `ITE 8705F Super IO Sensors'
  Failed! (0xec11)
Probing for `ITE 8712F Super IO Sensors'
  Failed! (0xec11)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87360 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87363 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87364 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Voltage Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Thermal Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Voltage Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Thermal Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87372 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87373 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87591 Super IO'
  Success... but not activated
Probing for `Nat. Semi. PC87371 Super IO'
  Failed! (0xec)
Probing for `Nat. Semi. PC97371 Super IO'
  Failed! (0xec)
Probing for `Nat. Semi. PC8739x Super IO'
  Failed! (0xec)
Probing for `Nat. Semi. PC8741x Super IO'
  Failed! (0xec)
Probing for `Nat. Semi. PCPC87427 Super IO'
  Failed! (0xec)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M10x/13x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M14x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M15x/192 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47S42x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47S45x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M172 Super IO'
  Failed! (0xec)
Probing for `SMSC LPC47B397-NC Super IO'
  Failed! (0xec)
Probing for `VT1211 Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83627HF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83627THF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83637HF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83687THF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83697HF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83697SF/UF Super IO PWM'
  Failed! (0xec)
Probing for `Winbond W83L517D Super IO'
  Failed! (0xec)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (0xec11)

Do you want to scan for secondary Super I/O sensors? (YES/no): YES
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

 Now follows a summary of the probes I have just done.
 Just press ENTER to continue:

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SiS96x SMBus adapter at 0x8100'
    Busdriver `i2c-sis96x', I2C address 0x50
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `SiS96x SMBus adapter at 0x8100'
    Busdriver `i2c-sis96x', I2C address 0x51
    Chip `SPD EEPROM' (confidence: 8)


 I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)? 12C/SMBus

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-sis96x
# I2C chip drivers
eeprom
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)yes
maddbaron@baronnet:~/Desktop$ sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
maddbaron@baronnet:~/Desktop$ sudo modprobe i2c-viapro
maddbaron@baronnet:~/Desktop$ sudo modprobe i2c-isa
maddbaron@baronnet:~/Desktop$ sudo modprobe it87
maddbaron@baronnet:~/Desktop$ sudo depmod -a
Password:
maddbaron@baronnet:~/Desktop$ sudo update-modules
maddbaron@baronnet:~/Desktop$ sensors
No sensors found!


How do I set the sensors(find them?) and test them so I can reboot?

---

### Post by Zed on 2006-09-20
In step 5 of the original HOWTO, the intent isn't that you modprobe the exact modules used in the example, but, rather, the ones output by sensors-detect.

Remove the ones you loaded, and load the one output by sensors-detect.

```

sudo modprobe -r i2c-viapro
sudo modprobe -r i2c-isa
sudo modprobe -r it87
sudo modprobe i2c-sis96x
sudo depmod -a
sudo update-modules
sensors

```

With any luck, this will actually produce results.

---

### Post by maddbaron on 2006-09-20
I think i messed up somehow, i keep getting no sensors found.

> maddbaron@baronnet:~/Desktop$ sudo modprobe -r i2c-viapro
Password:
maddbaron@baronnet:~/Desktop$ sudo modprobe -r i2c-isa
FATAL: Module i2c_isa is in use.
maddbaron@baronnet:~/Desktop$ sudo modprobe -r it87
maddbaron@baronnet:~/Desktop$ sudo modprobe i2c-sis96x
maddbaron@baronnet:~/Desktop$ sudo depmod -a
maddbaron@baronnet:~/Desktop$ sudo update-modules
maddbaron@baronnet:~/Desktop$ sensors
No sensors found!


---

