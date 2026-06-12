---
title: "lm-sensors detects but only shows partial sensor output"
date: 2005-11-04
forum: Desktop Environments
---

### Post by ekarni on 2005-11-04
I Followed the "lm-sensors howto" [here]("http://www.ubuntuforums.org/showthread.php?t=2780&highlight=sensors")
and am getting mixed results.  [FONT="Courier New"]sensors-detect[/FONT] appears to be detecting up my RAM and Winbond W83627THF, however [FONT="Courier New"]sensors[/FONT] only prints the results from the RAM.  It appears from the [FONT="Courier New"]sensors-detect[/FONT] output that the [FONT="Courier New"]w83627hf[/FONT] module isn't loaded, yet the [FONT="Courier New"]lsmod [/FONT]output shows that it is.  Note that according to the sensors page the w83627hf and w83627thf do use the same module.  Attempting to manually load it with [FONT="Courier New"]sudo modprobe w83627hf[/FONT] is unsuccessful.  Output from sensors-detect, sensors, and lsmod are shown below, along with my /etc/modules file.  Any ideas on getting output from the Winbond chip?  It would be great to know how hot my CPU is getting under load.

Thanks!

_System details:_
Ubuntu Breezy 5.10, Gnome
MSI K8T Neo2 Motherboard (VIA K8T800 Northbridge Chipset)
AMD64 3000+ 939, Venice Core

```
[COLOR="Blue"]etan@corsair:~$ sudo sensors-detect[/COLOR]
Password:

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
 Do you want to probe now? (YES/no):
Probing for PCI bus adapters...
Use driver `i2c-viapro' for device 00:11.0: VIA Technologies VT8237 South BridgeProbe succesfully concluded.

We will now try to load each adapter module in turn.
Module `i2c-viapro' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
 i2c-dev is not loaded. Do you want to load it now? (YES/no):
 Module loaded succesfully.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: SMBus Via Pro adapter at 0400
Do you want to scan it? (YES/no/selectively):
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
Client found at address 0x31
Client at address 0x50 can not be probed - unload all client drivers first!
Client at address 0x51 can not be probed - unload all client drivers first!
Client found at address 0x69

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no):
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

Do you want to scan for Super I/O sensors? (YES/no):
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (0x82)
Probing for `Winbond W83627HF Super IO Sensors'
  Failed! (0x82)
[COLOR="Blue"]Probing for `Winbond W83627THF Super IO Sensors'
  Success... found at address 0x0290[/COLOR]
Probing for `Winbond W83637HF Super IO Sensors'
  Failed! (0x82)
Probing for `Winbond W83697HF Super IO Sensors'
  Failed! (0x82)
Probing for `Winbond W83697SF/UF Super IO PWM'
  Failed! (0x82)
Probing for `Winbond W83L517D Super IO'
  Failed! (0x82)
Probing for `Winbond W83627EHF Super IO Sensors'
  Failed! (0x8283)

Do you want to scan for secondary Super I/O sensors? (YES/no):
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

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `Winbond W83627THF Super IO Sensors' (confidence: 9)


 I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)?

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-isa
# I2C chip drivers
w83627hf
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)
[COLOR="Blue"]etan@corsair:~$ sensors[/COLOR]
eeprom-i2c-0-51
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

eeprom-i2c-0-50
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512
[COLOR="Blue"]etan@corsair:~$ lsmod[/COLOR]
Module                  Size  Used by
i2c_dev                 9216  0
nls_utf8                2176  0
nls_cp437               5888  0
vfat                   12288  0
fat                    46492  1 vfat
sd_mod                 17424  0
usb_storage            64704  0
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
powernow_k8            11528  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
usbhid                 30688  0
usblp                  11776  0
snd_cmipci             30368  1
gameport               14472  1 snd_cmipci
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         10120  1 snd_pcm
snd_opl3_lib            9856  1 snd_cmipci
snd_timer              21764  2 snd_pcm,snd_opl3_lib
snd_hwdep               8608  1 snd_opl3_lib
snd_mpu401_uart         6784  1 snd_cmipci
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  2 snd_opl3_lib,snd_rawmidi
snd                    48644  12 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
amd64_agp              11464  1
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
[COLOR="Blue"]i2c_isa                 2176  0
i2c_viapro              7696  0
eeprom                  7184  0
w83627hf               26792  0
i2c_sensor              3456  2 eeprom,w83627hf
i2c_core               19728  7 i2c_dev,i2c_acpi_ec,i2c_isa,i2c_viapro,eeprom,w83627hf,i2c_sensor[/COLOR]
nvidia               3711364  12
agpgart                32328  2 amd64_agp,nvidia
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  3
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 powernow_k8,thermal
fan                     4740  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  6 usb_storage,usbhid,usblp,ehci_hcd,uhci_hcd
sata_via                8836  0
libata                 47876  1 sata_via
scsi_mod              124872  3 sd_mod,usb_storage,libata
r8169                  23180  0
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  6
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  613
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
[COLOR="Blue"]etan@corsair:~$ cat /etc/modules[/COLOR]
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
nvidia

#sensors, EDK
# I2C chip drivers
w83627hf
eeprom

# I2C adapter drivers
i2c-viapro
i2c-isa
#end EDK

```

---

### Post by tHub on 2005-11-04
werd.
all i did here was:
$ sudo apt-get install lm-sensors
$ sudo sensors-detect
and answered smbus to the last config. question and its working ok.
```
th@ubuntu:~$ sensors
it87-isa-0290
Adapter: ISA adapter
VCore 1:   +1.65 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
VCore 2:   +2.50 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
+3.3V:     +3.33 V  (min =  +8.16 V, max =  +8.16 V)   ALARM
+5V:       +4.97 V  (min =  +6.85 V, max =  +6.85 V)   ALARM
+12V:     +12.16 V  (min = +16.32 V, max = +16.32 V)   ALARM
-12V:     -14.84 V  (min =  +3.93 V, max =  +3.93 V)   ALARM
-5V:      -10.04 V  (min =  +4.03 V, max =  +4.03 V)   ALARM
Stdby:     +5.03 V  (min =  +6.85 V, max =  +6.85 V)   ALARM
VBat:      +0.00 V
fan1:     2122 RPM  (min =    0 RPM, div = 4)
fan2:     3110 RPM  (min =    0 RPM, div = 2)
fan3:        0 RPM  (min =    0 RPM, div = 2)
M/B Temp:    +33&#176;C  (low  =    -1&#176;C, high =    -1&#176;C)   sensor = thermistor
CPU Temp:    +47&#176;C  (low  =   +70&#176;C, high =   +80&#176;C)   sensor = thermistor
Temp3:       -55&#176;C  (low  =    -1&#176;C, high =    -1&#176;C)   sensor = thermistor
```

---

### Post by ekarni on 2005-11-16
Fixed it!  The problem is documented at the lm-sensors forum [here.]("http://secure.netroedge.com/~lm78/readticket.cgi?ticket=2094")

The solution is simple (disable pnpacpi), and is documented (indirectly) [here.]("http://www.ubuntuforums.org/showthread.php?t=11501&highlight=pnpacpi")
This seems safe enough, particularly if you're on a desktop and not running any sort of power management that would depend on this (ACPI).

By all means do read the above links, but for the lazy, here's the fix.  
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo gedit /boot/grub/menu.lst
```

Find this section and add the bolded text:
```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro **pnpacpi=off**
```

Save the file and reboot.  Assuming you went through the rest of the tutorial and have the correct modules loading, the planets are correctly aligned, etc, everything should work.

---

