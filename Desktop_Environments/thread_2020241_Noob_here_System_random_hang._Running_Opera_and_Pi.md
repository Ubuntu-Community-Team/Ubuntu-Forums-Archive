---
title: "Noob here: System random hang. Running Opera and Pidgin"
date: 2012-07-07
forum: Desktop Environments
---

### Post by moviezzz on 2012-07-07
Hi all,

Noob here. I installed Ubuntu 12.04 but noticed it hung randomly a few times. A few apps would be opened, namely Opera and Pidgin. Appreciate help on solving this.

Hardware using is Dell E6320 with its default hardware specs.

Thanks in advance!

JJ

---

### Post by lrcaballero on 2012-07-07
Can you provide us with more specs of your system please.

---

### Post by moviezzz on 2012-07-07
hi..

Is there any command I can use to get these info?

JJ

> **lrcaballero said:**
> Can you provide us with more specs of your system please.

---

### Post by moviezzz on 2012-07-07
will this do? ->

jj@noobie:/var/log$ sudo lshw -short
H/W path           Device      Class          Description
=========================================================
                               system         Latitude E6320 ()
/0                             bus            087HK7
/0/0                           memory         64KiB BIOS
/0/4                           processor      Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
/0/4/5                         memory         32KiB L1 cache
/0/4/6                         memory         256KiB L2 cache
/0/4/7                         memory         4MiB L3 cache
/0/4/0.1                       processor      Logical CPU
/0/4/0.2                       processor      Logical CPU
/0/4/0.3                       processor      Logical CPU
/0/4/0.4                       processor      Logical CPU
/0/4/0.5                       processor      Logical CPU
/0/4/0.6                       processor      Logical CPU
/0/4/0.7                       processor      Logical CPU
/0/4/0.8                       processor      Logical CPU
/0/4/0.9                       processor      Logical CPU
/0/4/0.a                       processor      Logical CPU
/0/4/0.b                       processor      Logical CPU
/0/4/0.c                       processor      Logical CPU
/0/4/0.d                       processor      Logical CPU
/0/4/0.e                       processor      Logical CPU
/0/4/0.f                       processor      Logical CPU
/0/4/0.10                      processor      Logical CPU
/0/41                          memory         4GiB System Memory
/0/41/0                        memory         2GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/41/1                        memory         2GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/1                           processor      
/0/1/0.1                       processor      Logical CPU
/0/1/0.2                       processor      Logical CPU
/0/1/0.3                       processor      Logical CPU
/0/1/0.4                       processor      Logical CPU
/0/1/0.5                       processor      Logical CPU
/0/1/0.6                       processor      Logical CPU
/0/1/0.7                       processor      Logical CPU
/0/1/0.8                       processor      Logical CPU
/0/1/0.9                       processor      Logical CPU
/0/1/0.a                       processor      Logical CPU
/0/1/0.b                       processor      Logical CPU
/0/1/0.c                       processor      Logical CPU
/0/1/0.d                       processor      Logical CPU
/0/1/0.e                       processor      Logical CPU
/0/1/0.f                       processor      Logical CPU
/0/1/0.10                      processor      Logical CPU
/0/100                         bridge         2nd Generation Core Processor Family DRAM Controller
/0/100/2                       display        2nd Generation Core Processor Family Integrated Graphics Controller
/0/100/16                      communication  6 Series/C200 Series Chipset Family MEI Controller #1
/0/100/19          eth0        network        82579LM Gigabit Network Connection
/0/100/1a                      bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
/0/100/1b                      multimedia     6 Series/C200 Series Chipset Family High Definition Audio Controller
/0/100/1c                      bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 1
/0/100/1c.1                    bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 2
/0/100/1c.1/0      wlan0       network        Centrino Advanced-N 6205
/0/100/1c.2                    bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 3
/0/100/1c.3                    bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 4
/0/100/1c.5                    bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 6
/0/100/1c.5/0                  generic        O2 Micro, Inc.
/0/100/1d                      bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
/0/100/1f                      bridge         QM67 Express Chipset Family LPC Controller
/0/100/1f.2        scsi0       storage        82801 Mobile SATA Controller [RAID mode]
/0/100/1f.2/0      /dev/sda    disk           250GB ST9250410AS
/0/100/1f.2/0/1    /dev/sda1   volume         100MiB Windows NTFS volume
/0/100/1f.2/0/2    /dev/sda2   volume         160GiB Windows NTFS volume
/0/100/1f.2/0/3    /dev/sda3   volume         72GiB Extended partition
/0/100/1f.2/0/3/5  /dev/sda5   volume         68GiB Linux filesystem partition
/0/100/1f.2/0/3/6  /dev/sda6   volume         3976MiB Linux swap / Solaris partition
/0/100/1f.2/1      /dev/cdrom  disk           DVD+-RW TS-U633J
/0/100/1f.3                    bus            6 Series/C200 Series Chipset Family SMBus Controller

---

### Post by carl4926 on 2012-07-07
If you open a terminal and leave 'top' running
Then open opera and pidgin
Bring your terminal back in to focus and watch to see the processes.

You can install something call hwinfo
It can fet a detailed list of all your hardware. But it's usually sufficient to just post the output of

```
lspci -nnk
```That will tell us about most of the hardware and loaded drivers

---

### Post by carl4926 on 2012-07-07
Nothing unusual in that output if you ask me
unning top may help you identify the issue
or check .xsession-errors

---

### Post by moviezzz on 2012-07-08
hi,

how do i check .xsession-errors?


> **carl4926 said:**
> Nothing unusual in that output if you ask me
unning top may help you identify the issue
or check .xsession-errors

---

### Post by carl4926 on 2012-07-08
It's a hidden file in your user dir

---

### Post by carl4926 on 2012-07-08
> **carl4926 said:**
> It's a hidden file in your user dir
Just to be clear - by that I mean /home/yourusername*
Just open the file manager and press Ctrl+H

---

### Post by moviezzz on 2012-07-08
Thanks a lot. here are the outputs:

jj@noobie:~$ cat .xsession-errors
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
I/O warning : failed to load external entity "/home/jj/.compiz/session/10e2ee044e6c72e78b134171660940952300000018710033"
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
** Message: applet now removed from the notification area
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done
** Message: using fallback from indicator to GtkStatusIcon

(compiz:1937): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Setting Update "main_menu_key"
Setting Update "run_key"
** Message: moving back from GtkStatusIcon to indicator

** (zeitgeist-datahub:2227): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

** (nautilus:1953): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist


** (nautilus:1953): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

(Pidgin:2411): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(Pidgin:2411): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(Pidgin:2411): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(Pidgin:2411): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(Pidgin:2411): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(Pidgin:2411): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(Pidgin:2411): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(Pidgin:2411): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(Pidgin:2411): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(Pidgin:2411): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


> **carl4926 said:**
> Just to be clear - by that I mean /home/yourusername*
Just open the file manager and press Ctrl+H

---

### Post by carl4926 on 2012-07-08
I can't really pretend to understand all that, but perhaps someone will.

Pidgin is obviously having some kind of bad hair day.

But you mention Opera specifically. Does that mean that pidgin is OK with no opera and or with other browsers?

If you use fallback mode, do things work differently?

---

### Post by idoitprone on 2012-07-08
[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/976481](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/976481)

do you have swap?

cuz it sound like you are swapping without swap
```
free -m
```

---

### Post by carl4926 on 2012-07-08
> **idoitprone said:**
> [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/976481](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/976481)

do you have swap?

cuz it sound like you are swapping without swap
```
free -m
```


This posted suggests he does

```
/0/100/1f.2/0/3/6  /dev/sda6   volume         3976MiB Linux swap / Solaris partition
```

---

### Post by moviezzz on 2012-07-08
i have dual boot. windows 7 and ubuntu. is the problem here?

---

### Post by moviezzz on 2012-07-08
i dont know if one will function good without the other. sometimes the system doesnt hang the whole day, sometimes it hangs withing 1hour. i work with these 2 apps, so i cant really have one closed and wait for the problem since the problem is random.


> **carl4926 said:**
> I can't really pretend to understand all that, but perhaps someone will.

Pidgin is obviously having some kind of bad hair day.

But you mention Opera specifically. Does that mean that pidgin is OK with no opera and or with other browsers?

If you use fallback mode, do things work differently?

---

### Post by moviezzz on 2012-07-08
Hi,

yes, i have swap ->

jj@noobie:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3909       1468       2441          0         73        651
-/+ buffers/cache:        743       3166
Swap:         3975          0       3975

i installed my ubuntu alongside my windows 7 following the default install. changed nothing during the installation.

```

```
> **idoitprone said:**
> [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/976481](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/976481)

do you have swap?

cuz it sound like you are swapping without swap
```
free -m
```

---

### Post by moviezzz on 2012-07-08
hmm.. i am getting this in my syslog. i tried googling the error but nothing made sense to me. can someone tell me if this log shows anything wrong? i was only running opera at the time. went bathroom came back and system hung. notice the time 09.19 - 10.00, i rebooted the system around 09.39. ->

Jul  8 09:19:41 noobie kernel: [ 2157.053625] CPU2: Package power limit notifica
tion (total events = 200)
Jul  8 09:19:41 noobie kernel: [ 2157.053628] CPU1: Package power limit notifica
tion (total events = 200)
Jul  8 09:19:41 noobie kernel: [ 2157.053893] CPU3: Package power limit normal
Jul  8 09:19:41 noobie kernel: [ 2157.053895] CPU0: Package power limit normal
Jul  8 09:19:41 noobie kernel: [ 2157.053897] CPU2: Package power limit normal
Jul  8 09:19:41 noobie kernel: [ 2157.053898] CPU1: Package power limit normal
Jul  8 10:00:34 noobie kernel: [ 4609.806824] CPU0: Package power limit notifica
tion (total events = 319)
Jul  8 10:00:34 noobie kernel: [ 4609.806828] CPU2: Package power limit notifica
tion (total events = 319)
Jul  8 10:00:34 noobie kernel: [ 4609.806845] CPU3: Package power limit notifica
tion (total events = 320)
Jul  8 10:00:34 noobie kernel: [ 4609.806848] CPU1: Package power limit notifica
tion (total events = 320)

---

### Post by moviezzz on 2012-07-10
help me please.

---

### Post by idoitprone on 2012-07-10
> **moviezzz said:**
> help me please.


try and disable flash in opera

while your at it post the output of 

```
lspci -nnk
```

---

### Post by moviezzz on 2012-07-10
Hi,

I have flashed disabled. This is the output running lspci -nnk, thanks!

jj@noobie:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
	Subsystem: Dell Device [1028:0492]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
	Subsystem: Dell Device [1028:0492]
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Dell Device [1028:0492]
	Kernel driver in use: mei
	Kernel modules: mei
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Dell Device [1028:0492]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
	Subsystem: Dell Device [1028:0492]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
	Subsystem: Dell Device [1028:0492]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
	Subsystem: Dell Device [1028:0492]
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation QM67 Express Chipset Family LPC Controller [8086:1c4f] (rev 04)
	Subsystem: Dell Device [1028:0492]
	Kernel modules: iTCO_wdt
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 Mobile SATA Controller [RAID mode] [8086:282a] (rev 04)
	Subsystem: Dell Device [1028:0492]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
	Subsystem: Dell Device [1028:0492]
	Kernel modules: i2c-i801
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0082] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1321]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
0a:00.0 SD Host controller [0805]: O2 Micro, Inc. Device [1217:8221] (rev 05)
	Subsystem: Dell Device [1028:0492]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci


> **idoitprone said:**
> try and disable flash in opera

while your at it post the output of 

```
lspci -nnk
```

---

### Post by moviezzz on 2012-07-11
Hi,

I disabled flash in opera but system still hung. :(

> **idoitprone said:**
> try and disable flash in opera

while your at it post the output of 

```
lspci -nnk
```

---

### Post by carl4926 on 2012-07-11
I don't see any hardware from the lspci output that would give me cause for concern.

Personally I think you need to try working with other options in software and see if the problem is solved (such as Chromium and Empathy), if it is...
Then I would consider reporting to Launchpad bugs your problem with opera/pidgin

---

### Post by moviezzz on 2012-07-11
hi Carl,

i did as u suggested, only chromium was opened. but it hung and then powered off by itself.

> **carl4926 said:**
> I don't see any hardware from the lspci output that would give me cause for concern.

Personally I think you need to try working with other options in software and see if the problem is solved (such as Chromium and Empathy), if it is...
Then I would consider reporting to Launchpad bugs your problem with opera/pidgin

---

### Post by idoitprone on 2012-07-11
> **moviezzz said:**
> hi Carl,

i did as u suggested, only chromium was opened. but it hung and then powered off by itself.

```
sudo apt-get install lm-sensors
sudo sensors-detect # yes to everything

sensors
```post the output of lm-sensors.

you have a second gen i5 without the lastest kernel

does your computer feel warm?

---

### Post by moviezzz on 2012-07-11
Hi,

Thanks for your reply. This is the output, hope i get it right:

jj@noobie:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +25.0°C  (crit = +107.0°C)

I have a fan pad attached so it's always not warm. Just touched everywhere it wasn't warm. It has been running for about 3hrs already.

> **idoitprone said:**
> ```
sudo apt-get install lm-sensors
sudo sensors-detect # yes to everything

sensors
```post the output of lm-sensors.

you have a second gen i5 without the lastest kernel

does your computer feel warm?

---

### Post by idoitprone on 2012-07-11
> **moviezzz said:**
> Hi,

Thanks for your reply. This is the output, hope i get it right:

jj@noobie:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +25.0°C  (crit = +107.0°C)

I have a fan pad attached so it's always not warm. Just touched everywhere it wasn't warm. It has been running for about 3hrs already.

it does not say the core temp

Did you follow all the direction in the sensors-detect

such as

```
sudo modprobe coretemp
```

i believe that should be the correct module, but i usually let the sensors-detect tell me

---

### Post by moviezzz on 2012-07-11
Do you mean this? :

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)


jj@noobie:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +25.0°C  (crit = +107.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +51.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +51.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +47.0°C  (high = +86.0°C, crit = +100.0°C)

Ooops.. I see it now, i think. I must have missed something the last time.

JJ

> **idoitprone said:**
> it does not say the core temp

Did you follow all the direction in the sensors-detect

such as

```
sudo modprobe coretemp
```

i believe that should be the correct module, but i usually let the sensors-detect tell me

---

### Post by idoitprone on 2012-07-12
> **moviezzz said:**
> Do you mean this? :

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)


jj@noobie:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +25.0°C  (crit = +107.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +51.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +51.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +47.0°C  (high = +86.0°C, crit = +100.0°C)

Ooops.. I see it now, i think. I must have missed something the last time.

JJ

i guess it is not a heating issue. If it is, i guess check the temperature, when it hangs, but i am not really sure what i going on

---

### Post by moviezzz on 2012-07-12
is there some kind of logs that will give me a clue? :(

> **idoitprone said:**
> i guess it is not a heating issue. If it is, i guess check the temperature, when it hangs, but i am not really sure what i going on

---

### Post by idoitprone on 2012-07-13
> **moviezzz said:**
> is there some kind of logs that will give me a clue? :(

donno

i might as well tell you to run commands to lower you computer running temperature

```
sudo bash -c 'echo "options i915  i915_enable_rc6=1  i915_enable_fbc=1 lvds_downclock=1" > /etc/modprobe.d/i915.conf'
```

if the screen resolution does not work then

add these to you grub parameters
```
acpi_osi=Linux apci_backlight=vendor
```

if you want to change you kernel scheduler to redunce cpu time

```
elevator=deadline
```
also add this to grub

---

### Post by moviezzz on 2012-07-13
Hi,

I did the 1st line to reduce the temperature:

sudo bash -c 'echo "options i915  i915_enable_rc6=1  i915_enable_fbc=1 lvds_downclock=1" > /etc/modprobe.d/i915.conf'

It didn't mess up the resolution, so do i still need to issue the 2nd and 3rd cmd?

Thanks for replying.

JJ


> **idoitprone said:**
> donno

i might as well tell you to run commands to lower you computer running temperature

```
sudo bash -c 'echo "options i915  i915_enable_rc6=1  i915_enable_fbc=1 lvds_downclock=1" > /etc/modprobe.d/i915.conf'
```

if the screen resolution does not work then

add these to you grub parameters
```
acpi_osi=Linux apci_backlight=vendor
```

if you want to change you kernel scheduler to redunce cpu time

```
elevator=deadline
```
also add this to grub

---

