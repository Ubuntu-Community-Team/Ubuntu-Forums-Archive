---
title: "Looking for desklets"
date: 2006-01-21
forum: Desktop Environments
---

### Post by nami on 2006-01-21
Hi

I have seen some screenshots of cool desklets, but have no idea how to install them on my system.

I'm basically interested in desklets which will

1. How the temperature of my cpu, hard drives, etc
2. cpu clock speed and usage
3. amount of ram and usage
4. amount of hard drive space and usage

However to start off with I would like the temperature readers most.

Any suggestions?

Nami

---

### Post by 23meg on 2006-01-21
Start by installing gdesklets / adesklets
```
sudo apt-get install gdesklets
sudo apt-get install adesklets
```
and then go to their websites and grab the desklets you're interested in and install them.

[http://adesklets.sourceforge.net/](http://adesklets.sourceforge.net/)
[http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

---

### Post by nami on 2006-01-29
Thanks

I've done:

sudo apt-get install gdesklets
sudo apt-get install adesklets

and have downloaded

lmsensors-gdesklet-0.8.tar.bz2

How do I install this and get it onto my desktop?

Thanks

---

### Post by angkor on 2006-01-29
Just go to Applications -> Gdesklets and click on install package. Browse to the lmsensors-gdesklet-0.8.tar.bz2 you've downloaded and install it.

Then select the desklet and go to the file menu and click 'run selected desklet'.

Edit: You may need to install lm-sensors for this desklet to work properly.

sudo apt-get install lm-sensors

after installing it run:

sudo sensors-detect

to enable the sensors.

---

### Post by nami on 2006-01-29
Ok some of the desklets are working e.g. the cpu load, the memory status, storage, network etc etc.  But any sensor desklets e.g. cpu temp hdd temp dont work.

I get the following error:

Could not find sensor 'Theme'
/home/administrator/.gdesklets/Displays/lmsensors/lmsensors-Psi-fan.display
A sensor could not be found. This usually means that it has not been installed.

---

### Post by nami on 2006-01-29
I did the sensor scan and this is what the output was:

[terminal output]
administrator@ubuntu:~$ sudo apt-get install lm-sensors
Password:
Reading package lists... Done
Building dependency tree... Done
lm-sensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
administrator@ubuntu:~$ sudo sensors-detect

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
 Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-viapro' for device 00:11.0: VIA Technologies VT8233A South Bridge
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Module `i2c-viapro' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
 i2c-dev is not loaded. Do you want to load it now? (YES/no): y
 Module loaded succesfully.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: SMBus Via Pro adapter at 0400
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x1b
Probing for `Maxim MAX6650/MAX6651'... Failed!
Probing for `Philips Semiconductors PCA9556'... Failed!
Client found at address 0x2f
Probing for `National Semiconductor LM78'... Failed!
Probing for `National Semiconductor LM78-J'... Failed!
Probing for `National Semiconductor LM79'... Failed!
Probing for `National Semiconductor LM80'... Failed!
Probing for `Winbond W83781D'... Failed!
Probing for `Winbond W83782D'... Failed!
Probing for `Winbond W83791D'... Failed!
Probing for `Winbond W83792D'... Failed!
Probing for `Winbond W83791SD'... Failed!
Probing for `Winbond W83627HF'... Failed!
Probing for `Winbond W83627EHF'... Failed!
Probing for `Asus AS99127F (rev.1)'... Failed!
Probing for `Asus AS99127F (rev.2)'... Failed!
Probing for `Asus ASB100 Bach'... Failed!
Probing for `Analog Devices ADM9240'... Failed!
Probing for `Dallas Semiconductor DS1780'... Failed!
Probing for `National Semiconductor LM81'... Failed!
Probing for `Analog Devices ADM1029'... Failed!
Probing for `ITE IT8712F'... Failed!
Probing for `ITE IT8705F / SiS 950'... Failed!
Client at address 0x51 can not be probed - unload all client drivers first!
Client at address 0x52 can not be probed - unload all client drivers first!
Client found at address 0x69

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): y
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
  Trying address 0x0290... Success!
    (confidence 8, driver `w83781d')
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

Do you want to scan for Super I/O sensors? (YES/no): y
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (0x60)
Probing for `Winbond W83627HF Super IO Sensors'
  Failed! (0x60)
Probing for `Winbond W83627THF Super IO Sensors'
  Failed! (0x60)
Probing for `Winbond W83637HF Super IO Sensors'
  Failed! (0x60)
Probing for `Winbond W83697HF Super IO Sensors'
  Success... found at address 0x0290
Probing for `Winbond W83697SF/UF Super IO PWM'
  Failed! (0x60)
Probing for `Winbond W83L517D Super IO'
  Failed! (0x60)
Probing for `Winbond W83627EHF Super IO Sensors'
  Failed! (0x6016)

Do you want to scan for secondary Super I/O sensors? (YES/no): y
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF Super IO Sensors'
  Failed! (skipping family)

 Now follows a summary of the probes I have just done.
 Just press ENTER to continue:

Driver `w83781d' (may not be inserted):
  Misdetects:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `Winbond W83697HF' (confidence: 8)

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `Winbond W83697HF Super IO Sensors' (confidence: 9)


 I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)? ISA

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-isa
# I2C chip drivers
w83627hf
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)y
administrator@ubuntu:~$
[/terminal output]

A few seconds later I got the following error!

[the error]
Could not find sensor 'Theme'
/home/administrator/.gdesklets/Displays/lmsensors/lmsensors-Psi-fan.display
A sensor could not be found. This usually means that it has not been installed.
[/the error]

---

