---
title: "Cooling Fan not working on Dell Precision M65 with Gutsy"
date: 2008-02-10
forum: Dell  Ubuntu Support
---

### Post by james957 on 2008-02-10
My cooling fan isn't running on Gutsy.  I've got a Dell Precision M65, with the gkrellm and i8kfan modules installed.  I can see the fan icon in gkrellm, and it claims to be switching on, but I don't hear the fan turn on.  The temperatures rise, and the laptop shuts down occasionally.  

Gkrellm was able to control the fan on this laptop with Dapper installed, however.

Does anyone have any ideas?

Thanks,
James

---

### Post by mrsteveman1 on 2008-02-10
If something changed between 2 different ubuntu versions its likely the kernel. I have a firewall here that sometimes refuses to start the CPU fan, which is problematic because its a P4 which is hot. The fan starts at power on, then as soon as linux loads its fan module it turns the fan off even though it says its on. 

Check in /proc/acpi/fan/ , there should be one or more FAN directories there, and there should be a file in some of them called state, and possibly others.

run 

```
sudo cat state
```

on any of them you find and see what it says.

---

### Post by james957 on 2008-02-12
There's nothing there!

:/proc/acpi/fan$ ls -l
total 0

There's no FAN directory!  I wonder why that is?

Thanks,
James

---

### Post by mrsteveman1 on 2008-02-12
Check and see if the module is even loaded with lsmod | grep fan

also do sudo dmesg | grep fan

---

### Post by james957 on 2008-02-12
Here's my output:

$ lsmod | grep fan
fan                     5764  0 

$ sudo dmesg | grep fan
[sudo] password for user:

I got nothing with the last command.

Thanks so much, Steve!

James

---

### Post by faulkes on 2008-02-12
If you have i8k installed and gkrellm (which it appears you do), go to the configuration section of gkrellm (F1 key).  Go to the plugins section and look at the i8k plugin.

In there will be fan information, make sure you turn on the display fan speed and select the appropriate tempurature scale you are most familiar with (celsius or f.).

Apply the configuration and go back to gkrellm, under the fan animations will be displayed the speed in rpm.  If you click the fan animations, you can increase or decrease this.  Note that the highest setting is starts is 1250 (I know, but it only displays 4 chars).  Additionally, towards the upper left of the tempurature area, right where it displays the tempurature, if you click on this, a little green light comes on - afaik this indicates that the fans are now going to automatically adjust to tempurature changes 
when they occur.  If it is not clicked, my experience has been that one or both of the fans will not adjust (or even completely stop) causing the system temp to rise.

Hope this helps,

Faulkes

---

### Post by mrsteveman1 on 2008-02-12
The module appears to be loaded but might not be working, or perhaps /proc just isnt showing anything (though it should). The sensors/fans in a system are usually controlled by a super I/O chip, so as long as your chip is supported by the kernel you should be able to control the fan speed.

I would use the lm-sensors package to see if the system can find the fans at all, if lm-sensors cant see them something else is wrong.

Install the package lm-sensors, then run sudo sensors-detect and let it find your hardware etc.

Once thats done run the 'sensors' program and see if it shows your fans

---

### Post by james957 on 2008-02-13
Steve,
Here's my output from sensors-detect:
Should I add the "coretemp" driver to /etc/modules like it suggests?

Thanks,
James

$ sudo sensors-detect 

# sensors-detect revision 4609 (2007-07-14 09:28:39 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): 
Module loaded successfully.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): 
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: SMBus I801 adapter at 10c0 (i2c-3)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): 
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
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x2803
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): 
AMD K8 thermal sensors...                                   No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

---

### Post by mrsteveman1 on 2008-02-13
The coretemp module just lets you read the temperature of the processor, you can add it if you like.


It seems lm-sensors found your super i/o chip but can't read it for some reason.

Probing for Super-I/O at 0x2e/0x2f
Trying family `SMSC'... Yes
Found unknown chip with ID 0x2803

So it found an SMSC (company) chip it can't read. I'll see what model number that is supposed to be and check if its supported by the kernel, though i believe it should work since it worked before.

---

### Post by james957 on 2008-02-14
Steve,

Thanks so much for the help!  I'm interested to see if the fan is supported.

Thanks,
James

---

### Post by mrsteveman1 on 2008-02-17
I haven't been able to find out what chip that is exactly, but perhaps you can post the output of lsmod to see if the module is already loaded but not working correctly.

If fan control worked in an older version of ubuntu, perhaps this is just a bug in the driver for that chip. I've seen similar things happen on a firewall i have here.

---

### Post by james957 on 2008-02-21
Steve,

Here is my output from lsmod.  "fan" is near the bottom, and appears to be used by "0"

Thanks for all the help!
James

Module                  Size  Used by
af_packet              24840  4 
i8k                     7320  0 
isofs                  36412  1 
udf                    87204  0 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
vboxdrv                61104  0 
ipv6                  273892  12 
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_ondemand        9612  2 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
container               5504  0 
button                  8976  0 
battery                11012  0 
video                  18060  14 
sbs                    19592  0 
ac                      6148  0 
bay                     6912  0 
dock                   10656  1 bay
ndiswrapper           185240  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 41388  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               6221648  26 
pcspkr                  4224  0 
serio_raw               8068  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
i2c_core               26112  1 nvidia
psmouse                39952  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              25620  0 
agpgart                35016  2 nvidia,intel_agp
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
ata_generic             8452  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
tg3                   110980  0 
ehci_hcd               36492  0 
ata_piix               17540  3 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 sbp2,sg,sd_mod,sr_mod,libata
uhci_hcd               26640  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by mrsteveman1 on 2008-02-21
Since this is a dell laptop im betting the i8k module is what controls the fans and a lot of other stuff.

Check /proc/i8k/ to see if there are any files listed, since thats where they should be if i8k is in fact in charge of things.


I found some info on the i8kutils [here]("http://people.debian.org/~dz/i8k/00-README")

What do i8kmon/i8kctl tell you?

---

### Post by james957 on 2008-02-23
Steve,

i8kmon opens up a little window with two buttons.. Right now, one says 64 and the other says 2 and is red.

$ i8kctl
1.0 (null) 5XXXXX1 60 -1 0 27660 0 1 -1

$ cat /proc/i8k
1.0 A02 5XXXXX1 60 -22 1 27660 57840 -1 -22

From your link:
The fields read from /proc/18k are:

    1.0 A17 2J59L02 52 2 1 8040 6420 1 2
    |   |   |       |  | | |    |    | |
    |   |   |       |  | | |    |    | +------- 10. buttons status
    |   |   |       |  | | |    |    +--------- 9.  ac status
    |   |   |       |  | | |    +-------------- 8.  right fan rpm
    |   |   |       |  | | +------------------- 7.  left fan rpm
    |   |   |       |  | +--------------------- 6.  right fan status
    |   |   |       |  +----------------------- 5.  left fan status
    |   |   |       +-------------------------- 4.  CPU temperature (Celsius)
    |   |   +---------------------------------- 3.  serial number
    |   +-------------------------------------- 2.  BIOS version
    +------------------------------------------ 1.  /proc/i8k format version

------

This is telling me that it thinks the fans are on (it shows rpm's for both).  But I really don't think they are.. I don't hear them, where I did before this Gutsy installation.  And the temps just keep climbing and the machine starts slowing down, particularly when I'm handling large image files or running Maple computations.  

I also have an Nvidia Quadro FX graphics card.  Perhaps the card is overheating?


Thanks,
James

---

### Post by mrsteveman1 on 2008-02-23
Is this a laptop?

If its a desktop can you physically see if the fan is spinning?

I know on a few dell machines I've worked on the CPU fan is used as the case fan as well, so if that fan isn't running its quite bad for the system, though an intel CPU can technically handle it for a while by cutting its voltage in half etc.

If the system thinks its on, and its not on, its definitely a bug in the module. I've seen something similar on a firewall here, the fan stays on from boot because the bios turned it on, but as soon as the kernel loads everything the fan turns off even though it says the fan is on.

---

### Post by james957 on 2008-02-24
Hmm.  It's a laptop.

Is there another module I can use, or revert to an old module?  I'd hate to burn up my processor.  

Another piece of information:  the laptop had some impact damage and I had to replace the hard drive.  The fan worked in Windows with the old hard drive, but I don't have a Windows partition on this one.  So I don't really have a way to check it in Windows.  It is possible that is physically damaged, but why would I be reading a nonzero fan speed if that is the case?

James

---

### Post by mrsteveman1 on 2008-02-24
If the fan chip is telling you the fan is spinning and giving you an RPM number even though the fan isnt spinning, its either because the fan itself is damaged and the wires are touching (or something equally bad), or because the kernel module is buggy.

It might be worth it to install the newest kernel from kernel.org on the machine rather than going back to an older kernel.

A simple test to see what changes could be done by booting an older version of the ubuntu livecd, IE whatever version worked. You can then see whats different, if i8k spits out different numbers, if the fan actually works etc.

---

