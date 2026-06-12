---
title: "CPU temperature applet for XFCE"
date: 2007-12-10
forum: Desktop Environments
---

### Post by tak1150 on 2007-12-10
I know you can install and use the GNOME applet for CPU temperature monitoring, but I'd like to keep things as XFCE as possible.
Does anybody know of a good XFCE-native way to monitor the CPU temperature? I would also like to have the feature where you can set a command to be issued when it reaches certain temp. Thanks!

---

### Post by phidia on 2007-12-10
If youreally don't want to use the gnome app then you may need to look though the [listings]("http://freshmeat.net/search/?q=temperature&section=projects&Go.x=0&Go.y=0") at [freshmeat]("http://freshmeat.net/") and compile your own temp monitor.

---

### Post by PeterJS on 2007-12-10
Gkrellm is always an option, it's got monitors for everything. I just looked and the temperature monitors do support alerts, which you can setup to issue alerts at two different temperatures per sensor.

---

### Post by Skip Da Shu on 2007-12-10
> **PeterJS said:**
> Gkrellm is always an option, it's got monitors for everything. I just looked and the temperature monitors do support alerts, which you can setup to issue alerts at two different temperatures per sensor.

I saw this running on my kid's Gentoo box... is this a package I can install... uh, why don't I go look since I just figured out how to do that...never mind :-)

---

### Post by scxtt on 2007-12-10
gentoo has a "xfce4-sensors" package - that should interface w/ lm_sensors (and probably hddtemp) -- have you tried that?

xfce4-sensors-plugin <-- ubuntu package name

---

### Post by Jouke74 on 2007-12-11
The XFCE-temperature monitor is indeed an option, but it is very basic. Another option is Conky. A lot more configuring, but the end result can be much more satisfying.

You need to have HDDtemp (as daemon) and LM-sensors installed and set-up correctly in both cases.

[http://img248.imageshack.us/my.php?image=screenshot2nw5.jpg](http://img248.imageshack.us/my.php?image=screenshot2nw5.jpg)

---

### Post by tak1150 on 2007-12-11
Thank you all for your tips!

> **scxtt said:**
> gentoo has a "xfce4-sensors" package - that should interface w/ lm_sensors (and probably hddtemp) -- have you tried that?

xfce4-sensors-plugin <-- ubuntu package name

Yes, I've tried this, but I couldn't get it to have the option for CPU temperature. I have lm-sensors and hddtemp installed :confused: And yes, that is the kind of thing that I was looking for because XFCE-native applets seem to be less resource-hungry. --any ideas?

I recently switched from GNOME to XFCE for performance. Until then, I had been using gkrellm and it was great. I was using it to control the fans on my Dell laptop (have a heating issue). But recently I started using a laptop cooling thingy w/ a fan so I can have the CPU operating at the maximum freq. all the time :)

Thanks again.

---

### Post by Jouke74 on 2007-12-12
Did you configure LM-sensors correctly, added the modules etc?
This program is not "just install".

---

### Post by tak1150 on 2007-12-12
> **Jouke74 said:**
> Did you configure LM-sensors correctly, added the modules etc?
This program is not "just install".

Thanks for replying.
How do you configure lm-sensors?

---

### Post by scxtt on 2007-12-12
try **sudo sensors-detect**

then just pay attn. to what it says.

---

### Post by tak1150 on 2007-12-13
> **scxtt said:**
> try **sudo sensors-detect**

then just pay attn. to what it says.

Thanks!

I got this output:
```

# sensors-detect revision 4609 (2007-07-14 09:28:39 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): YES
Probing for PCI bus adapters...
Sorry, no known PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): YES
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): YES
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
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   Yes
Found `Nat. Semi. PC87591 Super IO'                         
    (but no address specified)

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): YES
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

```

What could this mean? Do I need to uninstall other sensor type apps (GNOME ones)?

---

### Post by scxtt on 2007-12-13
looks like your motherboard doesn't play nice w/ lm-sensors :(

not sure how/what was working for you w/ gkrellm+gnome ...

does typing **sensors** into a CLI return anything?

---

### Post by Jouke74 on 2007-12-13
You need to load the I2C module as well as the `National Semiconductor'...  module. Found `Nat. Semi. PC87591 Super IO' (but no address specified). It should then specify an adress. However, I don't know whether the last module is already in existence. Check the shown websites...

---

### Post by gillza on 2008-05-02
I have the same board and running 7.10 (ubuntu, default kernel). After installing and configuring sensors as per HOWTO. My sensors output is a little strange:
```
it8718-isa-0290
Adapter: ISA adapter
VCore:     +1.20 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:      +1.97 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:     +3.39 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +5.00 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +12.29 V  (min =  +0.00 V, max = +16.32 V)   
-12V:     -16.97 V  (min = -16.97 V, max =  +4.01 V)   
-5V:       -4.96 V  (min =  -8.78 V, max =  +4.05 V)   
5VSB:      +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
VBat:      +3.22 V
CPU Fan:  2556 RPM  (min =   10 RPM)                   
Duct Fan: 2812 RPM  (min =    0 RPM)                   
fan3:        0 RPM  (min =    0 RPM)                   
[COLOR="Red"]CPU Temp:    -55°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
M/B Temp:     -4°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor [/COLOR]  
SBr Temp:    +26°C  (low  =  +127°C, high =   +60°C)   sensor = diode   
vid:      +1.088 V

```

I like these temperatures... but don't think they are true :). Anyway I'm suspecting that the problem is with ACPI and might be fixed as in here (not exactly the same way, but something similar)
[http://ubuntuforums.org/showthread.php?t=623633](http://ubuntuforums.org/showthread.php?t=623633)

I was wondering if anyone got the sensors to work any other way. I'll try fixing the issue later, once I gather more information about it.

---

