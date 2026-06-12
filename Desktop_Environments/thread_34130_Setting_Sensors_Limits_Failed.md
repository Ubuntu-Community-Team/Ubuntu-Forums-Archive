---
title: "Setting Sensors Limits Failed"
date: 2005-05-13
forum: Desktop Environments
---

### Post by Peter Alien on 2005-05-13
Can someone tell me what this is and if causes any problems to the System ?

Setting Sensors Limits -> Fail  (when i bootup Ubuntu)


Thanks

---

### Post by mcduck on 2005-05-14
I suppose you have lm-sensors installed, but you havent'n run sensors-detect. So do that (sudo sensors-detect) and answer yes to all questions. The do "sudo sensors -s"

That would fix your problem.

After that running "sensors" in terminal will give you some information about voltages, temperatures and fan speeds of your computer. If these don't seem right, you should edit /etc/sensors.conf to get right values. To do this, run sensors, write down what sensor chip you have and sudo gedit /etc/sensors.conf. Use find to get to your chip's settings and tweak them until running "sensors" gives you sensible values. You'll have to do "sudo sensors -s" every time you have changed something in sensors.conf.

---

### Post by paul cooke on 2005-05-14
what I found annoying about sensors-detect is that it was perfectly happy to run as a normal user, but wouldn't actually see the sensors cos it didn't do the detection over the i2c bus, it just happily told you that it couldn't detect any sensors... and that you should go to the website to see if the latest version had support for your motherboard...

It never told you that it was supposed to be run as root. When I did it as root, suddenly everything was found and magically set up by following the options presented..

---

### Post by Peter Alien on 2005-05-14
Many Thanks :)

---

### Post by Ali_Baba on 2005-05-14
I just updated to breezy files and now sensors are suddenly working.without using root also.must be some patch or support thing.

---

### Post by rama on 2005-09-29
I only get this after running sudo sensors
```
eeprom-i2c-1-51
Adapter: SMBus nForce2 adapter at 5000
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

eeprom-i2c-1-50
Adapter: SMBus nForce2 adapter at 5000
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

```

Why is that?

---

### Post by krcm on 2005-12-20
[QUOTE=mcduck]I suppose you have lm-sensors installed, but you havent'n run sensors-detect. So do that (sudo sensors-detect) and answer yes to all questions. The do "sudo sensors -s"

That would fix your problem.

After that running "sensors" in terminal will give you some information about voltages, temperatures and fan speeds of your computer. If these don't seem right, you should edit /etc/sensors.conf to get right values. To do this, run sensors, write down what sensor chip you have and sudo gedit /etc/sensors.conf. Use find to get to your chip's settings and tweak them until running "sensors" gives you sensible values. You'll have to do "sudo sensors -s" every time you have changed something in sensors.conf.[/QUOTE]






I had the same problem and tried what you suggested.
sensors-detect gave me a lot of failed results: probing for DCC monitor, probing for Maxim MAX 6900, ISAbus scannings (except for one), all IO sensors and secundary IO fan sensors.

sensors -s resulted in 'no sensors found'

We had a new fan installed and new power supply, are all these failed things related to that? 

Is there a way to fix this ?

An

---

### Post by Brian Smith on 2006-07-18
When I do sudo sensors-detect, I only get in reponse:

No i2c device files found. Use prog/mkdev/mkdev.sh to create them.


Maybe my Soyo socket 478 motherboard is not supported, how can I find out?

Thanks for any help!

---

### Post by cborga1985 on 2006-08-02
> **Brian Smith said:**
> When I do sudo sensors-detect, I only get in reponse:

No i2c device files found. Use prog/mkdev/mkdev.sh to create them.


Maybe my Soyo socket 478 motherboard is not supported, how can I find out?

Thanks for any help!

try doing some of what is here [http://www.debian-administration.org/articles/327](http://www.debian-administration.org/articles/327)
worked for me with my AsRock 939 Dual-Sata2 board :)

---

### Post by Guns90 on 2006-09-09
Using the last link provided, I get this...

 Now follows a summary of the probes I have just done.
 Just press ENTER to continue:

Driver `asb100' (should be inserted):
  Detects correctly:
  * Bus `SMBus nForce2 adapter at 5500'
    Busdriver `i2c-nforce2', I2C address 0x2d (and 0x48 0x49)
    Chip `Asus ASB100 Bach' (confidence: 8)

Driver `not-a-sensor' (should be inserted):
  Detects correctly:
  * Bus `SMBus nForce2 adapter at 5500'
    Busdriver `i2c-nforce2', I2C address 0x2f
    Chip `Winbond W83791SD' (confidence: 3)

Driver `smbus-arp' (should be inserted):
  Detects correctly:
  * Bus `SMBus nForce2 adapter at 5500'
    Busdriver `i2c-nforce2', I2C address 0x61
    Chip `SMBus 2.0 ARP-Capable Device' (confidence: 1)

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus nForce2 adapter at 5000'
    Busdriver `i2c-nforce2', I2C address 0x50
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `SMBus nForce2 adapter at 5000'
    Busdriver `i2c-nforce2', I2C address 0x51
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `SMBus nForce2 adapter at 5000'
    Busdriver `i2c-nforce2', I2C address 0x52
    Chip `SPD EEPROM' (confidence: 8)


 I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)?  I2C/SMBus

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-nforce2
# I2C chip drivers
asb100
# Warning: the required module smbus-arp is not currently installed on your system.
# For status of 2.6 kernel ports see [http://secure.netroedge.com/~lm78/supported.html](http://secure.netroedge.com/~lm78/supported.html)
# If driver is built-in to the kernel, or unavailable, comment out the following line.
smbus-arp
eeprom
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)n
gary@Faith:/dev$ sudo modprobe -a asb100 not-a-sensor smbus-arp eeprom
WARNING: Module not_a_sensor not found.
WARNING: Module smbus_arp not found.
gary@Faith:/dev$

A little help please.

---

