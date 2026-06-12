---
title: "back to debian again (laptop suggestions please)"
date: 2008-12-31
forum: Debian
---

### Post by cmay on 2008-12-31
hi .
i am going back to debian again.  i have had so many troubles  with the ubuntu installer  that i cant install  ubuntu or any of its derivatives   so i finally made up my mind and  decided to stick with etch until lenny is released as stable. i also use a debian derivative called 64studio which is a debian with all the programs for audio production installed and a modified kernel  which makes audio in real time sound much better and that is all the changes done to it. i would like to get a laptop for transporting my recordings of studio material from the studio i use and back home and do some recording and i am starting to look for a debian friendly laptop that simply works and has a fair price.  it needs to have some power as i will use it to record drums in the studio and i will  use a custom  debian  i  build  from the minimal  iso since i want it to be  my office  computer also  so i do not just stick the  64studio distro in it. 64studio  has a way of working exactly  as  it should until one installs too many programs that breaks other programs somehow. (have not found out why yet )
any suggestions. ?

---

### Post by kerry_s on 2008-12-31
i would say have a look at dell's, you can get it with ubuntu, so it is debian friendly. ibm's not bad, but i've had a few gotca's with them.

---

### Post by cmay on 2008-12-31
thanks. if the prices are right (or laptop used) then i could go for one of those. is it all dells that are usable or are there specific models that are more or less designed for linux.
i have a little asus EeePC which i use as just a laptop for when i get to go to the hospital and i found that it is really hard to fit all types of linux distributions in it. but asus eee are somewhere are little special also . just do not want to get a cat in a bag with webcam or sound and wireless as i also use skype  alot with this asus and i have a hard time imagine if i get a new laptop i wont need that to work also . i save some money by using skype so its  a good thing to give a little extra to have that working also .

---

### Post by kerry_s on 2008-12-31
not sure, you'll just have to do some google research.
the only thing i've looked into is the netbook, cause i want to get one this new year, i've chosen the 2gopc because it's 100% linux compatible even though it comes with windows.
this is the 1 i'm after:
[http://www.2gopc.com/2goPC_atom.html](http://www.2gopc.com/2goPC_atom.html)

i played with it in the store for hours, feels nice. :D

---

### Post by cmay on 2008-12-31
that look pretty nice. 
i never seen one of those before. but i think it maybe outsmart an asus EeePC if you are are a linux user. i been happy with my little asus but i would want a larger sized laptop with a much bigger harddrive than 8 gigabytes since crunch bang takes the four gigabytes already. then if  i use it as much more than just a travel computer  i have so little space left for my things that  i cant have room for it. the sound samples i use for electronic drumkit samplings are 9 gigabytes on two dvd so it kinda gives little option than a new laptop dedicated for audio recording and a larger harddrive. i need at least 80 gigabytes .
i will keep an eye out for those t2go ,i have a feeling that they could become popular here in Denmark as well. thanks for the link.

---

### Post by polmir on 2009-01-01
[URL="http://www.linuxcertified.com/linux_laptops.html"]	
Check here[/URL]

[and here.]("http://www.linux-laptop.net/")

---

### Post by cmay on 2009-01-16
i been searching for a laptop and found this homepage that actually sell used computers and with ubuntu preinstalled. for all those that live in denmark i posted the link to this page. 
[http://www.brugtecomputere.dk/group.asp?group=44](http://www.brugtecomputere.dk/group.asp?group=44)

thanks for the replies everyone. i at least know exactly where to buy my computers from now on. as i do not have that much money i am very happy to find a computer store that actually only sells used hardware and that they have ubuntu preinstalled is great. 
tread marked solved(when i get some more money i get laptop woohooo :) )

---

### Post by cmay on 2009-02-04
i got it today. it is a X one model h767 meze and i just installed ubuntu in it to rid myself of windows vista. everything works right out of the box in ubuntu so i guess when i have found out exactly how to get debian lenny working on it i can go right ahead and install it i will do that in a week or so i think.

first  i need to make sure i can have all things working before installing debian and read up on how to do it so i dont end up feeling i got the cat in the bag now that i seen whats its like when it all works perfect.







:) today == me happy :).

---

### Post by jay576 on 2009-02-04
If you post better hardware specifications, more people would be able to tell you what will work out of the box on debian.

---

### Post by cmay on 2009-02-04
good point. this is from the add

"15.4" TFT widescreen (WXGA/ GT 1280 x 800)
intel dual core T1600 (1.66 ghz)
160 gigabyte harddisk
2 gigabyte ddr-2 ram
dvd /rw dual layer 
1.3 mega pixel webcam
a wireless netcard
and a 4000Ah battery


and this is output of lshal > aha.txt 

[php]Dumping 102 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/computer'
  info.addons = {'hald-addon-cpufreq', 'hald-addon-acpi'} (string list)
  info.callouts.add = {'hal-acl-tool --remove-all', 'hal-storage-cleanup-all-mountpoints'} (string list)
  info.callouts.session_active = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_add = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_inactive = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_remove = {'hal-acl-tool --reconfigure'} (string list)
  info.capabilities = {'cpufreq_control'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq'} (string list)
  info.product = 'Computer'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = {'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = {'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = {'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = {'i', 'i', '', '', '', 'b'} (string list)
  power_management.acpi.linux.version = '20080609'  (string)
  power_management.can_hibernate = true  (bool)
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
  power_management.is_powersave_set = false  (bool)
  power_management.type = 'acpi'  (string)
  system.chassis.manufacturer = 'SiS'  (string)
  system.chassis.type = 'Other'  (string)
  system.firmware.release_date = '08/05/0892'  (string)
  system.firmware.vendor = 'Phoenix Technologies LTD'  (string)
  system.firmware.version = '6.00'  (string)
  system.formfactor = 'laptop'  (string)
  system.hardware.primary_video.product = 25425  (0x6351)  (int)
  system.hardware.primary_video.vendor = 4153  (0x1039)  (int)
  system.hardware.product = 'M7x0S'  (string)
  system.hardware.serial = '12345678901234567'  (string)
  system.hardware.uuid = '0090F580-4C2D-0000-0000-000000000000'  (string)
  system.hardware.vendor = 'Phoenix/SiS'  (string)
  system.hardware.version = 'Rev. A1'  (string)
  system.kernel.machine = 'i686'  (string)
  system.kernel.name = 'Linux'  (string)
  system.kernel.version = '2.6.27-11-generic'  (string)

udi = '/org/freedesktop/Hal/devices/acpi_CPU0'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU0'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU0'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = true  (bool)
  processor.number = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/acpi_CPU1'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU1'  (string)
  linux.acpi_path = '/proc/acpi/processor/CPU1'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = true  (bool)
  processor.number = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  access_control.file = '/dev/snd/timer'  (string)
  access_control.type = 'sound'  (string)
  alsa.device_file = '/dev/snd/timer'  (string)
  alsa.type = 'timer'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Timer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'  (string)
  linux.device_file = '/dev/snd/timer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/timer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  access_control.file = '/dev/sequencer2'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'  (string)
  linux.device_file = '/dev/sequencer2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer2'  (string)
  oss.device_file = '/dev/sequencer2'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  access_control.file = '/dev/sequencer'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'  (string)
  linux.device_file = '/dev/sequencer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer'  (string)
  oss.device_file = '/dev/sequencer'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  access_control.file = '/dev/snd/seq'  (string)
  access_control.type = 'sound'  (string)
  alsa.device_file = '/dev/snd/seq'  (string)
[/php]

---

### Post by jay576 on 2009-02-04
What is the lspci output?

---

### Post by cmay on 2009-02-04
this is lspci output. i been told by the way that this machine should really not be one of the most compatible with linux but mine is an upgraded model so it works with out any problems. sound is a bit low as the only thing i can point a finger on. 
[PHP]
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
00:09.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
00:09.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
 [/PHP]

---

### Post by markharding557 on 2009-02-06
lenny is very stable so i would advise using it and it will save the bother of upgrading later

---

### Post by cmay on 2009-02-07
i already use the lenny  lxde + open box cd image on two on my older computers. i love using Debian but i have for the sake of simplicity installed ubuntu on my new laptop. it worked out of the box and i needed someting installed  as fast as possible. (to get rid of the preinstalled vista so i could have some peace of mind.)

 the project on my mind is to build a custom lenny audio prodution installation on my laptop so i can record and work on my programming everywhere. i may need to compile a custom kermel from the 64studio distriubution and find out exactlly how it is build as a audio prduction distribution before i install it in my laptop. 

 the reason i do not just use the 64studio is that i do not find the udgrade they made as distribution as pleasing. they use lenny which should be great but its not working on my hardware with sound as good as  the older version which is based on etch. i have a special soundcard that needs some restricted alsa modules which is not installed per default in lenny but it is on etch. and the overall grade as such gives me a headache in generel so i rather just learn to build my own setup as i go along instead. 

 i still se the older version of 64studio on my audio recording setup. it is very great so i just need something that can be carried and record drums. which i will in time be able to do with a beter soundcard on my laptop and a few good recording apps to go with when i do my jamsessions in the studio i can borrow.

---

### Post by em4r1z on 2009-02-12
> **cmay said:**
> i love using Debian but i have for the sake of simplicity installed ubuntu on my new laptop.
Ubuntu might be slightly easier but I do doubt it can be simpler than Debian.
If your current needs aren't too demanding, the HP-550 might be an excellent purchase. It works out of the box in GNU/Linux (make sure to get the variant with the Intel wireless card.)

---

### Post by cmay on 2009-02-13
> **em4r1z said:**
> Ubuntu might be slightly easier but I do doubt it can be simpler than Debian.
If your current needs aren't too demanding, the HP-550 might be an excellent purchase. It works out of the box in GNU/Linux (make sure to get the variant with the Intel wireless card.)
that has to with the sim card and wireless that are in it from the phone company. they link to a ubuntu package for having that work. i am waiting for an eye operation so i need it to work as painless as possible right away. (which it  does now) and when i can see again i want to use debian lenny on it and configure it as a sound recording unit for my debian sound studio setup  using somekind of extern usb microphone and soundcard. and still have my personal stuff and some movies on it. for when i  bring the laptop with me around. i got it for the sake of using debian lenny but i still see too bad to make it work i think. i have lots of time to do this so i just use ubuntu for a while on it first.

---

