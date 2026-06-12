---
title: "HOWTO: XPS m1330 power savings"
date: 2008-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sdennie on 2008-07-02
Depending on how you use the machine, with a 9 cell battery, it's possible to get over 6 hours of battery life with an XPS m1330.  This is a guide for the scripts and general tips I've used on my XPS m1330.

**Specs:**
XPS m1330
T9300 CPU
NVidia 8400M GS GPU
7200rpm 200G disk
LED display
Intel 3945 wireless
9 cell battery

**Basic scripts**

[Edit] 
Several other people have written scripts in this thread and some of them have more options or go about doing things a different way.  There are many ways to do what I'm trying to accomplish and the other scripts are worth looking at once you've looked through this post and understand the basic idea of what's going on.  I'll link to them here so that people don't have to wade through the entire thread to find them:

- [atlas95s script]("http://ubuntuforums.org/showpost.php?p=5310874&postcount=4")
- [tinivoles script]("http://ubuntuforums.org/showpost.php?p=5319346&postcount=8")
- [motins script]("http://ubuntuforums.org/showpost.php?p=5380689&postcount=40")
- [bubbalouies script]("http://ubuntuforums.org/showpost.php?p=5390336&postcount=45")
[/Edit]

The first script is similar to laptop-mode but with tips from powertop and [www.lesswatts.org](www.lesswatts.org).  It's possible to use laptop-mode and make this script smaller but, my personal preference is to have everything in one place.  Here is the main script:

```

#!/bin/bash

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then
  [B]# Set the drive to mostly stay awake.  Some may want to change -B 200
  # to -B 255 to avoid accumulating Load_Cycle_Counts[/B]
  hdparm -B 200 -S 240 -M 254 /dev/sda

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  mount -o remount,commit=60 /
  mount -o remount,commit=60 /home

  # Turn off the laptop mode disk optimization
  echo 0 > /proc/sys/vm/laptop_mode

  # Manually set the wifi driver to no power savings.
  echo 6 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Only wakeup every 60 seconds to see if we need to write dirty pages
  # By default this is every 5 seconds but, I prefer 60 to reduce disk
  # activity.
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs

  # Turn off sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  
  # Set the SATA to max performance
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Enable the webcam driver
  modprobe uvcvideo

else # Save power

  [B]# Set the disks to aggressively save power and use the lowest acoustic
  # level.  Some might find these settings too aggressive.  If so, change 
  # "-S 4" to something larger like -S 24 (two minutes) and -B 1 to -B 255.[/B]
  hdparm -B 1 -S 4 -M 128 /dev/sda
  
  # Change the ext3 commit times to 10 minutes.  This reduces disk
  # activity
  mount -o remount,commit=600 /

  # Set laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945 driver to power savings.
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Set sound card power savings
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  # Set SATA to minimum power
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Remove the webcam driver
  modprobe -r uvcvideo
fi

```

Most these settings come from powertop/www.lesswatts.org but, some of them are using different values.  To install this script on Hardy, name it 99-savings and use:

```

sudo install 99-savings /etc/pm/sleep.d
sudo install 99-savings /etc/pm/power.d

```

To install it on Gutsy, use:

```

sudo install 99-savings /etc/acpi/start.d
sudo install 99-savings /etc/acpi/resume.d
sudo install 99-savings /etc/acpi/ac.d
sudo install 99-savings /etc/acpi/battery.d

```

**NVidia and compiz**
If you don't have an NVidia card (this is only tested on an 8400M GS in fact), and you aren't using compiz, this section propably won't be of any use to you.  

First, I recommend using this tutorial to get good compiz performance on AC and good power savings on battery: [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)

Then, we will set it up so that the NVidia driver uses as little power as possible.  First, edit /etc/X11/xorg.conf and find the section that describes the nvidia card.  You may have customized it in the past but, be sure it at least contains the following information:

```

Section "Device"
    Driver    "nvidia"
    Option    "OnDemandVBlankInterrupts" "True"

```

Now we will install a script that does 2 things: 1) Turns of sync to vblank when the machine is on battery power. 2) Changes the compiz Wall plugin to use a lower value.  This means that you can switch desktops without forcing the GPU into maximum power (it saves a lot of power).

```

#!/bin/bash

[b]
# Change this to your user name
XUSER=your_username
[/b]

if on_ac_power; then
  # Set vblank to on when on AC power
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 1"

  # Change wall switch time to default
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type float --set /apps/compiz/plugins/wall/allscreens/options/slide_duration 0.3"

  # Touch the nvidia card so it immediately goes to full power when we
  # plug the machine in
  DISPLAY=:0.0 su ${XUSER} -c "nvidia-settings -q all > /dev/null"

else

  # Turn off sync to vblank when on battery power so we reduce the nvidia
  # wakeups
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 0"
  
  # Set the wall slide duration much lower to prevent it from forcing the
  # card into full power
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type float --set /apps/compiz/plugins/wall/allscreens/options/slide_duration 0.1"
fi

```

Depending on what plugins you use, you may want to add even more values to that to prevent compiz from forcing the GPU to max power as often.  To find the names/values of particular features, use gconf-editor and go to /apps/compiz.  To install that script, name it 99-nvidia and do the following on Hardy:

```

sudo install 99-nvidia /etc/pm/sleep.d
sudo install 99-nvidia /etc/pm/power.d

```

On Gutsy:

```

sudo install 99-nvidia /etc/acpi/start.d
sudo install 99-nvidia /etc/acpi/resume.d
sudo install 99-nvidia /etc/acpi/ac.d
sudo install 99-nvidia /etc/acpi/battery.d

```

**General**

- If you never use bluetooth, I recommend going into the BIOS and setting the wifi/bluetooth switch on the laptop to only control Bluetooth and then leaving that switch off at all times.

- If you never use the webcam, it may be sufficient to just modprobe -r uvcvideo however, I haven't thoroughly checked this out.  It may be best to completely blacklist the driver but, I'm not sure if that setting sticks between suspend/resume so, you may have to delete the driver (make a backup of it first).

- If you never use USB/Bluetooth while on battery, removing most of the usb and bluetooth subsystem can save a huge amount of power.  In the first section of first script add:

```

  # Optional: Put back most of the bluetooth/usb subsystem
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd

```

In the section for battery mode, add:

```

  # Optional: Remove the most of the bluetooth/usb subsystem
  modprobe -r hci_usb
  modprobe -r rfcomm
  modprobe -r l2cap
  modprobe -r bluetooth
  modprobe -r usbhid
  modprobe -r uhci_hcd
  modprobe -r ehci_hcd

```

This can save upwards of 1 watt of power.

- For anyone running the new 2.6.26 kernel, [the PCI Express power savings]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=7d715a6c1ae5785d00fb9a876b5abdfc43abc44b") seems to save a huge amount of power (about 0.7W).  The commands to do this are:

```

# Use default on AC
echo default > /sys/module/pcie_aspm/parameters/policy

```

And, on battery:

```

# Use powersave on battery
echo powersave > /sys/module/pcie_aspm/parameters/policy

```

There is also a "performance" setting but, it makes the power usage so incredibly high that it can't be what the BIOS is using by default so I'm not willing to use it.

- Do *not* leave a firefox tab open with things like gmail while on battery power.  If at all possible, close all tabs but one and try to keep to sites that are light on javascript and try to stay away from anything with flash.

- If you find the disk spinning up too often, try:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"
tail -f /var/log/syslog

```

Then, to turn that functionality off:
```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

Wait for a while and see if you can figure out what application is causing the disk to wakeup too often.  The script above reduces the number of wakeups due to writes but, reads can still cause the disk to wakeup.

- Do *not* use virtual machines while on battery power.  They will drain the battery very quickly.

- I'm currently testing whether turning off the Firefox disk cache will keep the disk suspended for longer amounts of time (the theory being the disk won't wakeup to read the cached files).  It's hard to tell if it's making a difference but, to try it, type "about:config" in Firefox and search for cache and you can turn off the disk cache.

- Use powertop and top in conjunction with each other in two different windows to see if you have any misbehaving applications.  If possible, put them in small windows that stay on top (maybe reduce the font size too) and keep an eye on both while going about your normal work.

- Use the ondemand governor and not the powersave governor.  See: [http://mjg59.livejournal.com/88608.html](http://mjg59.livejournal.com/88608.html)

- Keep the backlight as low as you can possibly stand it.  Try to at least keep it at half power or less.  This can save a lot of power.

- Avoid listening music while on battery power.  In fact, don't keep any music applications open while on battery power because many will prevent the sound card from going to sleep.

- For the machine as spec'd above, you should expect idle power consumption in the range of ~12 watts with a handful of apps open.  For example, with Firefox, Pidgin, Nautilus, Evolution and a few terminals running, if I type the following and then walk away from the machine for 1 minute:

```

acpi
sudo powertop -d -t 60

```

The output looks like this on the lowest backlight setting (note that the machine is at 85% battery and not 100% battery in this example):

```

sdennie@zorba:~/src/scripts$ acpi
     Battery 1: discharging, 85%, 06:19:34 remaining
sdennie@zorba:~/src/scripts$ sudo powertop -t 60 -d
PowerTOP 1.9    (C) 2007 Intel Corporation 

Collecting data for 60 seconds 
Cn	          Avg residency
C0 (cpu running)        ( 4.6%)
C1		  0.0ms ( 0.0%)
C2		  0.5ms ( 1.1%)
C3		  5.5ms (94.4%)
P-states (frequencies)
  2.51 Ghz    83.3%
  2.50 Ghz     0.0%
  2.00 Ghz     0.0%
   800 Mhz    16.7%
Wakeups-from-idle per second : 191.3	interval: 60.0s
Power usage (ACPI estimate): 12.1W (6.4 hours) 
Top causes for wakeups:
  63.5% (137.1)      <kernel IPI> : Rescheduling interrupts 
   7.1% ( 15.3)       <interrupt> : iwl3945 
   6.7% ( 14.4)       <interrupt> : extra timer interrupt 
   6.5% ( 14.0)           firefox : futex_wait (hrtimer_wakeup) 
   6.3% ( 13.6)       compiz.real : schedule_timeout (process_timeout) 
...

```

If you are using the 2.6.26 kernel and have enabled PCI Express savings and the machine is very idle, you can expect these numbers to be much lower (as low as 10.3W for me).

I hope that helps.

---

### Post by madsmeg on 2008-07-02
Great guide even though i do not own a laptop (yet)

When i do i will be sure to put this to use.

---

### Post by sultanoswing on 2008-07-03
Great thread, thanks Vor...just in time for my brand new XPS 1330 with x64 Ubuntu!

This an other threads are MUCH appreciated as we optimise these already nice laptops with a much better OS than the default (being not in the US, I had to order mine with Vista, sadly, but MS is deluded if they count all such purchases as 'Windows users'. It was wiped within an hour.).

Having implemented most of your above suggestions has reduced battery drain markedly (not objectively measured yet, but the bar is going down much more slowly).

Your NVIDIA 8400M GS ac-power full-speed guide was great - I had been wondering why compiz wasn't quite smooth prior to enabling the card properly!

EDIT: one tiny amendment to your guide - you mention saving the file as '99-savings.sh', yet then sudo install '99-savings'

---

### Post by atlas95 on 2008-07-03
* Here my script for powersave my m1330 (sorry comment are in french and i don't remember all the tweak I have do)

If someone can help me to optimise it most, i run it with an icon, not automatically on plug on un-plug ac.

```

#! /bin/bash


verif_root(){ # Fonction qui verifi que l'on lance bien en tant que ROOT
	        	UID_ROOT=0
			if [ "$UID" -ne "$UID_ROOT" ]
			    then
			            zenity --error --title="Accès refusé" --text="Les droits d'administrateur n'ont pas été octroyés pour ce script. Veuillez le relancer avec les permissions root !"
			            exit
			fi
			}	

function icon(){
	zenity --notification --text="Cliquer ici pour revenir a la normal, performance max" --window-icon="/home/cyril/.icons/tango-d/scalable/apps/gstreamer-properties.svg"
}

function puissance_min(){
verif_root

XUSER=cyril

  # Set vblank to on when on AC power
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 1"

  # Change wall switch time to default
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type float --set /apps/compiz/plugins/wall/allscreens/options/slide_duration 0.3"

  # Touch the nvidia card so it immediately goes to full power when we
  # plug the machine in
  DISPLAY=:0.0 su ${XUSER} -c "nvidia-settings -q all > /dev/null"

# arret de service inutile sur batterie
/etc/init.d/postfix stop
/etc/init.d/anacron stop
/etc/init.d/ntp stop
/etc/init.d/rsync stop
/etc/init.d/smartmontools stop
/etc/init.d/cupsys stop
/etc/init.d/tor stop
/etc/init.d/cron stop
/etc/init.d/sysklogd stop
/etc/init.d/klogd stop
# powersave scheduler cpu
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
# disque dur
hdparm -B 1 -S 4 -M 128 /dev/sda
mount -o remount,commit=600 /
mount -o remount,commit=600 /home
# powersave carte son
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
# powersave usb
echo 1 > /sys/module/usbcore/parameters/autosuspend
# powersave iwl4965 wifi
echo 5 > /sys/bus/pci/drivers/iwl4965/0000\:0c\:00.0/power_level
# reglage sata
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
echo min_power > /sys/class/scsi_host/host2/link_power_management_policy
echo min_power > /sys/class/scsi_host/host3/link_power_management_policy
echo min_power > /sys/class/scsi_host/host4/link_power_management_policy
# reglage vm
echo 10 > /proc/sys/vm/swappiness
echo 0 > /proc/sys/vm/dirty_expire_centisecs
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 60 > /proc/sys/vm/dirty_background_ratio
echo 95 > /proc/sys/vm/dirty_ratio
# arret du polling cdrom
hal-disable-polling --device /dev/scd0
# vitesse lecture cd au mini
setcd -x min
# arret de la cam
modprobe -r uvcvideo
modprobe -r usbvision
# désactiver le Wake-On-Lan
ethtool -s eth0 wol d #inutile si module decharger ci-dessous
modprobe -r tg3
# si son système est stable, pas la peine de causer de nombreux
# réveils CPU avec la surveillance des "Non Maskable Interrupt".
echo 0 > /proc/sys/kernel/nmi_watchdog
# driver lecteur de carte off
#modprobe -r tifm_sd
modprobe -r ricoh_mmc
## switch off usb
modprobe -r ehci_hcd
modprobe -r uhci_hcd
# undervoltage
echo "27 27 17 11 6" > /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
synclient TouchpadOff=1
#openbox --replace
zenity --warning --text "Appuyer sur windows+F4 pour reactiver le touchpad"
}

function puissance_max(){
verif_root
########## parti pour revenir a la normal
XUSER=youruser

  # Turn off sync to vblank when on battery power so we reduce the nvidia
  # wakeups
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 0"
  
  # Set the wall slide duration much lower to prevent it from forcing the
  # card into full power
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type float --set /apps/compiz/plugins/wall/allscreens/options/slide_duration 0.1"

# sheduler des 2core
echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
# pas d'autosuspend usb
echo 2 > /sys/module/usbcore/parameters/autosuspend
# voltage normal
if on_ac_power = 1 ; then
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids > /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
else
# possibly on battery
echo "30 30 20 14 9" > /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
fi
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids > /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
# polling du cd on
hal-disable-polling --enable-polling --device /dev/scd0   
# pas de powersave audio et wifi
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
echo 6 >  /sys/bus/pci/drivers/iwl4965/0000\:0c\:00.0/power_level
# vitesse cd au max
setcd -x max
# sata performance
echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy
echo max_performance > /sys/class/scsi_host/host2/link_power_management_policy
echo max_performance > /sys/class/scsi_host/host3/link_power_management_policy
echo max_performance > /sys/class/scsi_host/host4/link_power_management_policy

# reglage memoire virtuelle
echo 60 > /proc/sys/vm/swappiness
echo 3000 > /proc/sys/vm/dirty_expire_centisecs
echo 30 > /proc/sys/vm/dirty_writeback_centisecs
echo 10 > /proc/sys/vm/dirty_background_ratio
echo 40 > /proc/sys/vm/dirty_ratio

# switch on bluetooth
#/etc/init.d/bluetooth restart
#dellWirelessCtl --sw_bt 1
#modprobe rfcomm
#modprobe l2cap
#modprobe bluetooth
#modprobe hci_usb
#hciconfig hci0 up
## switch on usb
modprobe ehci_hcd
modprobe uhci_hcd
# cam 
modprobe usbvision
modrobe uvcvideo
# si son système est stable, pas la peine de causer de nombreux
# réveils CPU avec la surveillance des "Non Maskable Interrupt".
# re-on
echo 1 > /proc/sys/kernel/nmi_watchdog
# driver lecteur de carte on
modprobe ricoh_mmc
#modprobe tifm_sd
# recharge module ethernet
modprobe tg3
# Power manager off
hdparm -B 255 -S 240 -M 254 /dev/sda
mount -o remount,commit=5 /
mount -o remount,commit=5 /home
#gestionnaire de fenetre par default
#metacity --replace
# demarrage des daemon
/etc/init.d/cupsys restart
/etc/init.d/cron restart
/etc/init.d/klogd restart
/etc/init.d/sysklogd restart
/etc/init.d/tor restart
/etc/init.d/privoxy restart
/etc/init.d/postfix restart
/etc/init.d/anacron restart
/etc/init.d/ntp restart
/etc/init.d/rsync restart
/etc/init.d/smartmontools restart
}


case $1 in
	*)
		zenity --question --title="Optimisation de l'autonomie" --text "Etes vous sur de vouloir baisser la puissance ?"
		if [ $? == 0 ]; then
		puissance_min
		icon
		puissance_max
		fi
		;;
	"--min")
		puissance_min
		icon
		;;
	"--max")
		puissance_max
		;;
esac

```

* Could you say me where I can buy a 9cellular battery cheaper :?

---

### Post by sdennie on 2008-07-03
> **sultanoswing said:**
> 
Having implemented most of your above suggestions has reduced battery drain markedly (not objectively measured yet, but the bar is going down much more slowly).


Let me know what you find.  I keep thinking I've forgotten something.

> 
EDIT: one tiny amendment to your guide - you mention saving the file as '99-savings.sh', yet then sudo install '99-savings'

Fixed, thanks.

> **atlas95 said:**
> * Here my script for powersave my m1330 (sorry comment are in french and i don't remember all the tweak I have do)

If someone can help me to optimise it most, i run it with an icon, not automatically on plug on un-plug ac.


That looks good to me.  The only thing I see that doesn't look right is that you have the nvidia commands backwards.  You have the power savings nvidia commands in puissance_max and the reset to default commands in puissance_min.

> 
* Could you say me where I can buy a 9cellular battery cheaper :?

I'm not sure.  I just ordered a 4 cell battery from Dell (they wouldn't sell me one at order time with an nvidia card in the laptop) and it was US$150 (more expensive than a 6 cell and about the same price as a 9 cell).

---

### Post by ajmorris on 2008-07-04
very nice Vor, but if i may suggest a couple of things?:

increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs 
This wakes the disk up less frequenty for background VM activity
-- You set yours to 60 seconds... i thought this was a bit too long, and found 15 to be nice, but to each their own :)

Enable the ondemand cpu speed governor for all processors via: 
 echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
(you could do conservative if you really wanted to... i prefer it ondemand though...)

These get wiped upon a reboot, so they would want to be added to the script to be run at boot time.


Also, for anyone that compiles their own kernel (i believe these are on by default in the ubuntu kernel):

Enable the CONFIG_NO_HZ kernel configuration option.
This option is required to get any kind of longer sleep times in the CPU.

Enable the CONFIG_USB_SUSPEND kernel configuration option.
This option will automatically disable UHCI USB when not in use, and could
save someone about 1 Watt of power.


AJ

---

### Post by sdennie on 2008-07-04
> **ajmorris said:**
> very nice Vor, but if i may suggest a couple of things?:

increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs 
This wakes the disk up less frequenty for background VM activity
-- You set yours to 60 seconds... i thought this was a bit too long, and found 15 to be nice, but to each their own :)


Actually, I set it to 60 seconds on AC and 10 minutes on battery.  The 60 seconds on AC is to reduce disk activity a bit which seems to help keep the palm rest a bit cooler on this machine.  The 10 minutes is to keep the disks in standby for long periods of time to help reduce power, heat and noise.  Unfortunately, there is a [bug in firefox 3]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/221009") that causes to disk to wakeup every time firefox loads a page which more or less defeats putting the disk into standby.  It's possible (but maybe slightly dangerous) to fix this bug and keep the disk suspended but, I would imagine that a proper fix will be out fairly soon.

> 
Enable the ondemand cpu speed governor for all processors via: 
 echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
(you could do conservative if you really wanted to... i prefer it ondemand though...)


Yeah, I mentioned to run ondemand (which should be the default) but, I'll go ahead and explicitly put it into the script to make sure.  Thanks.

---

### Post by ibuclaw on 2008-07-04
Hey Vor, I somehow managed to drop 10W...

Went from 25.9 to 15.4W.

I'm still trying to figure out what I did. (Tried to implement everything as I tweaked, but I seem to have forgotten to puts some things in, and haven't quite managed to acheive it again, yet).

This is what I have so far (It's a mixture of yours plus a few addons).
```

#!/bin/bash
# Disable Wake on LAN and Reduce eth0 speed
  ethtool -s eth0 wol d
  ethtool -s eth0 speed 100 duplex half autoneg off
# Remove Other unnecessary modules
  hciconfig hci0 down
  MODULES="hci_usb rfcomm l2cap bluetooth usbhid uhci_hcd ehci_hcd i2c_algo_bit crc_ccitt joydev radeon serio_raw pcspkr i2c_i801 uvcvideo compat_ioctl32 videodev"
  for i in $MODULES
  do modprobe -r $i
  done
# Re-enable USB for those who need
  modprobe uhci_hcd
# Set Min Power to SATA Drives
  for i in /sys/class/scsi_host/*/link_power_management_policy
  do echo min_power > $i
  done
# Frequency Scaling = ondemand
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
# Lower Power Level of Wireless
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level
  iwconfig wlan0 txpower 7
# Auto Suspend Unused USB Busses (Timeout in seconds)
  for i in /sys/bus/usb/devices/usb?/power/autosuspend
  do echo 1 > $i
  done
# auto = autosupend
  for i in /sys/bus/usb/devices/usb?/power/level
  do echo auto > $i
  done
# Low Soundcard Power Level
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
# Reduce Disk activity
  echo 10 > /proc/sys/vm/swappiness
  echo 0 > /proc/sys/vm/dirty_expire_centisecs
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs
# Laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode
# Change mount commit
  mount -o remount,commit=600 /
# Separate partition needs separate command?
  mount -o remount,commit=600 /home
# Lowest HDPARM Values
  hdparm -B 1 -S 4 -M 128 /dev/sda
# Configure to use only one power core
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
# Stop unneccessary  services
  /etc/init.d/cron stop
  /etc/init.d/bluetooth stop
  /etc/init.d/preload stop
#  /etc/init.d/laptop-mode stop # Is this worth stopping?
# FINISH?
  echo FINISHED

```

Ooh, also.
Open up xorg.conf and put in the following section.
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
**        Option          "Coolbits"      "1"**
EndSection

```
Then restart X, and open up "**nvidia-settings**", then go into "**Clock Frequencies**" and enable Overclocking...
You can now underclock your Nvidia Card and save a bit more energy :D

[EDIT]
Thank-you Vor for pointing out the "ondemand" over "conservative" power savings. It now drops to 14Watts again!!!

Regards
Iain

---

### Post by var on 2008-07-06
hi vor,

thanks for your guide: is it usable on a Dell XPS M1530?

thanks again. :)

---

### Post by sdennie on 2008-07-06
> **var said:**
> hi vor,

thanks for your guide: is it usable on a Dell XPS M1530?

thanks again. :)

If I'm not mistaken, the m1530 is almost identical to the m1330 but slightly bigger.  Most of the guide should work on an m1530 I think.  It's certainly worth a try because it's very simple to undo/modify all the changes above.

---

### Post by var on 2008-07-06
> **vor said:**
> If I'm not mistaken, the m1530 is almost identical to the m1330 but slightly bigger.  Most of the guide should work on an m1530 I think.  It's certainly worth a try because it's very simple to undo/modify all the changes above.

thanks, but I've installed it after I noticed that my wireless card has a different PCI address. how can I safely uninstall and reinstall it?

thanks again. :)

---

### Post by sdennie on 2008-07-06
> **var said:**
> thanks, but I've installed it after I noticed that my wireless card has a different PCI address. how can I safely uninstall and reinstall it?

thanks again. :)

I'm constantly tweaking my scripts so, what I do is keep a user editable version of them in ~/src/scripts and then I have a script called "install_savings.sh" that just has:

```

install 99-savings /etc/pm/power.d/
install 99-savings /etc/pm/sleep.d/
install 99-nvidia /etc/pm/power.d/
install 99-nvidia /etc/pm/sleep.d/

```

When I modify my scripts, I just run that with sudo and clobber the older versions that are already installed.

So, to answer the original question, there is no need to uninstall before reinstalling the scripts.  You can just overwrite them.  The only files in /etc/pm/*/ are likely to be things that you've put there so, it's very easy to keep track of where the scripts are if you want to delete them (which is perfectly safe to do).

---

### Post by atlas95 on 2008-07-10
Hi ! 
How to automatically underclock the nvidia card??

I'm sur it is possible !

I search a .config for build my kernel, a .config optimized, with iwl4965 card, do you have this?
This will be good if we do one and post it, a lot of people have it, and with PAE activated (i have 4gb of ram in 32bit) ( [http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511))

---

### Post by sdennie on 2008-07-10
Tinivoles post (#8) explains how to underclock your nvidia card at the bottom.  You may also be able to set the values via the commandline with something similar to this:

```

nvidia-settings -a GPU3DClockFreqs=100,100

```

---

### Post by atlas95 on 2008-07-10
I have this :s

~$ nvidia-settings -a GPU3DClockFreqs=100,100

    The valid values for 'GPU3DClockFreqs' are in the ranges 100 - 800, 150 -
    1100 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

---

### Post by sdennie on 2008-07-10
> **atlas95 said:**
> I have this :s

~$ nvidia-settings -a GPU3DClockFreqs=100,100

    The valid values for 'GPU3DClockFreqs' are in the ranges 100 - 800, 150 -
    1100 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

Try:

```

nvidia-settings -a GPU3DClockFreqs=100,150

```

Not all frequencies are valid when underclocking so, it may take a while to find one that works.

---

### Post by atlas95 on 2008-07-10
This work, and for 2d :p ?
nvidia-settings -a GPU2DClockFreqs=100,100
which value min do you think i can make for have a correct 2d display for look video for example and gain power ? :) ?
We must add this too commande in 99-savings script !

edit: We must find a correct value for 2d, the command work but when i launch nvidia-settings, in 2d tab freq is at 169 yet :(

---

### Post by sdennie on 2008-07-10
Try using:

```

nvidia-settings -q GPU2DClockFreqs

```

That should give you the valid ranges for your card.  Again, not all underclocking frequencies are supported (if they are supported at all in 2D) so, it may take some time to find one that works.

---

### Post by atlas95 on 2008-07-10
Ok I will search the good one.

  Attribute 'GPU2DClockFreqs' (atlas-laptop:0.0): 169,100.
    The valid values for 'GPU2DClockFreqs' are in the ranges 42 - 338, 25 -
    1100 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

:-)

---

### Post by sdennie on 2008-07-11
> **atlas95 said:**
> Ok I will search the good one.

  Attribute 'GPU2DClockFreqs' (atlas-laptop:0.0): 169,100.
    The valid values for 'GPU2DClockFreqs' are in the ranges 42 - 338, 25 -
    1100 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

:-)

If you are using compiz, underclocking the 2D frequencies won't make any difference.  Also, tinivole said that he wasn't able to underclock 2D frequencies (or can cause instabilities) so, I don't recommend trying it.

---

### Post by atlas95 on 2008-07-11
No I hate compiz, i don't use it :)

> 
Thank-you Vor for pointing out the "ondemand" over "conservative" power savings. It now drops to 14Watts again!!!


What is the better for win some watt? ondemand or conservative? (sorry i don't understand 'complex' sentence :( )

Another thing, in gconf-editor:

/apps/gnome-power-manager/cpufreq/performance_battery 85
/apps/gnome-power-manager/cpufreq/performance_ac 25
/apps/gnome-power-manager/cpufreq/consider_nice false

Maybe this can be tweaked?

---

### Post by sdennie on 2008-07-11
I'm not sure what those gconf settings do but, ondemand is generally better for power savings than conservative or powersave.  If you test the settings on an idle machine, they will look similar but, under a normal user load, ondemand will save more power because it keeps the CPU in the idle state for longer periods of time (which is where the big CPU power savings is on modern CPUs).

---

### Post by atlas95 on 2008-07-11
So I must set ac on performance and battery on ondemand? You use ondemand for both?

---

### Post by sdennie on 2008-07-11
> **atlas95 said:**
> So I must set ac on performance and battery on ondemand? You use ondemand for both?

There is usually no reason to set the AC governor to performance.  Unless you are running something like Seti@Home which sets a nice level in a way that ondemand ignores, you aren't likely to notice a difference between ondemand and performance (except that ondemand will likely keep the machine cooler).

---

### Post by atlas95 on 2008-07-11
Ok so I have set ondemand for both, i have always tweak my system before with ondemand on ac and powersave on battery :/

What do you think about build a custom kernel? for improve boot time, enable pae etc, kernelcheck seems to work good but now we must disable all unecessary module etc... I need your help for tweaking !

thanks yet ;)

---

### Post by sdennie on 2008-07-11
> **atlas95 said:**
> Ok so I have set ondemand for both, i have always tweak my system before with ondemand on ac and powersave on battery :/


I recommend keeping it on ondemand at all times, yes.

> 
What do you think about build a custom kernel? for improve boot time, enable pae etc, kernelcheck seems to work good but now we must disable all unecessary module etc... I need your help for tweaking !

thanks yet ;)

I run a custom kernel for PAE support but, if it's not absolutely needed, I don't recommend it.  If you have 4GB of RAM, have a look here: [http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511).  Also building a custom kernel will probably not improve your boot time at all.  If you are using an XPS m1330, there isn't actually any need to reboot.  Just suspend/resume the machine and your effective boot time is less than 10 seconds.

---

### Post by atlas95 on 2008-07-11
Could you share your deb kernel please ... yes I have 4gb of ram and i want to be able to use it, i use a lot of vmware at work ...
You have only enable PAE in your kernel?

---

### Post by sdennie on 2008-07-11
> **atlas95 said:**
> Could you share your deb kernel please ... yes I have 4gb of ram and i want to be able to use it, i use a lot of vmware at work ...
You have only enable PAE in your kernel?

No, I can't.  It's a secret.  (I could tell you but then I'd have to kill you) ;)

Really, there is nothing special about what I'm doing.  The link I already posted above will get you moving in the right direction.

---

### Post by atlas95 on 2008-07-11
Which scheduler do you use? CFQ?

---

### Post by sdennie on 2008-07-11
> **atlas95 said:**
> Which scheduler do you use? CFQ?

Hehe.  Yes, CFQ.

---

### Post by atlas95 on 2008-07-11
I use pulsaudio, but in kernel config must i enable ALSA and OSS? only ALSA? only OSS?

---

### Post by sdennie on 2008-07-11
> **atlas95 said:**
> I use pulsaudio, but in kernel config must i enable ALSA and OSS? only ALSA? only OSS?

Hehe.  I think the thread has been diverted enough.  If you want to custom compile a kernel, use one of the guides in my previous post or google it.  It's non-trivial to compile a kernel and this is not the right thread to discuss it.  ;)

---

### Post by atlas95 on 2008-07-11
Could you see this topic please ! 
[http://ubuntuforums.org/showthread.php?p=5363670#post5363670](http://ubuntuforums.org/showthread.php?p=5363670#post5363670)


i have try with acpi=noirq, and i win a lot of watt but i'm some error before usplash, what do you think about that?

---

### Post by sdennie on 2008-07-11
I'm quite fond of my irqs and so don't run with acpi=noirq.

---

### Post by jeffeb3 on 2008-07-12
Is this thread dead?  only the beginning of last year.  Anything new happen in the m1330 power savings in the last year?

I wanted to mention something about your firefox disc writting thing.  I know you can mount part of the memory as a "ram disc" that is mounted somewhere in your filesystem.  If you could do this at boot, and tell firefox to cache it's junk there, then that would decrease the HD read/writes.  Although you might have other issues.  It's also volatile, so you could run into issues with firefox missing stuff... 

On second thought, maybe it's better to plead with mozilla to configure that property...

---

### Post by sdennie on 2008-07-12
> **jeffeb3 said:**
> Is this thread dead?  only the beginning of last year.  Anything new happen in the m1330 power savings in the last year?


This thread is still alive and only a week old.  ;)

> 
I wanted to mention something about your firefox disc writting thing.  I know you can mount part of the memory as a "ram disc" that is mounted somewhere in your filesystem.  If you could do this at boot, and tell firefox to cache it's junk there, then that would decrease the HD read/writes.  Although you might have other issues.  It's also volatile, so you could run into issues with firefox missing stuff... 

On second thought, maybe it's better to plead with mozilla to configure that property...

I thought about doing something like that (you can also set the databases to lazy write with some javascript) but, it's error prone and a hassle.  Hopefully the patch to really fix it will make it into the Ubuntu version of Firefox in the near future.

---

### Post by jeffeb3 on 2008-07-12
> **vor said:**
> This thread is still alive and only a week old.  ;)

heh, I just looked for a date, not the correct one...

BTW, I am using this script.  I didn't edit much, except removing the modprobe -r ucvideo.  I know I'll forget about this script when I'm traveling for work and want to video chat with home...

When I'm on battery power, the brightness keeps changing (not just the idle darker setting).  Is that part of this script?  I turn it all the way down when I can stand it.  It doesn't seem to stick though.

---

### Post by sdennie on 2008-07-12
> **jeffeb3 said:**
> 
When I'm on battery power, the brightness keeps changing (not just the idle darker setting).  Is that part of this script?  I turn it all the way down when I can stand it.  It doesn't seem to stick though.

It could be a conflict with the hardware brightness settings and gnome-power-manager.  See if you can disable brightness changes in gnome-power-manager by going to System->Preferences->Power Management.  That should allow you to have separate settings for AC/power that are provided by the hardware and not the software.

---

### Post by motin on 2008-07-13
Thanks a MILLION mate!

Just about a week ago I thought about starting an official XPS M1330 power-saving thread - and instead you did it - and much more thorough than I would have done it... great! :)

I'll get back shortly with questions and suggestions when I've tried your script!

> **vor said:**
> I thought about doing something like that (you can also set the databases to lazy write with some javascript) but, it's error prone and a hassle.  Hopefully the patch to really fix it will make it into the Ubuntu version of Firefox in the near future.

According to the comments in the bug report (one of them being my own...)
fsyncs are still issued by the firefox version shipped in the 8.04.1 update :(

In other words, it looks like it didn't make it this time - so do you have any plans on using/trying a proposed work-around?

> **var said:**
> thanks, but I've installed it after I noticed that my wireless card has a different PCI address. how can I safely uninstall and reinstall it?

thanks again. :)

tinivole's version is more generic. Use the following to alter the power saving levels instead:
```
echo 6 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level
```
and
```
echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level
```
respectively.

vor, maybe you can include this change in the OP?

---

### Post by motin on 2008-07-13
> **atlas95 said:**
> * Here my script for powersave my m1330 (sorry comment are in french and i don't remember all the tweak I have do)

If someone can help me to optimise it most, i run it with an icon, not automatically on plug on un-plug ac.

> **tinivole said:**
> Hey Vor, I somehow managed to drop 10W...

Went from 25.9 to 15.4W.

I'm still trying to figure out what I did. (Tried to implement everything as I tweaked, but I seem to have forgotten to puts some things in, and haven't quite managed to acheive it again, yet).

This is what I have so far (It's a mixture of yours plus a few addons).


Thanks for your contributed scripts!

I'm attempting to merge vor's script with your versions as well as with bubbalouie's version (sent to me generously by pm as a responsive in a different matter). 

I have picked most of these script's differences from vor's version into my merged version. Especially the [CPU undervoltaging part]("http://ubuntuforums.org/showthread.php?t=786402") was left out from vor's version (thanks bubbalouie and atlas95!). Hopefully we'll soon end up with a killer XPS M1330 power-saving script... 

Check my comments and questions below and hopefully vor can update the original script with some of the additions?

Whole current merged script:
```
#!/bin/bash

# == Section: Variable declaration - determines some script behaviors ==

# Debug - remove #-sign to enable bash debug output
#set -x;

# Specify ext3 partitions:
EXT3_PARTITIONS=`cat /etc/mtab | grep ext3 | awk '{print $2}'`;

# Partitions to disable atime for:
NOATIME_PARTITIONS=`cat /etc/mtab | grep -e 'ext3\|fat' | awk '{print $2}'`;

# Aggressive? Set to 1 to enable. Will disable web-cam, 2nd cpu core, usb and more. Inspect the code below for more details
AGGR="1";

# Misc options - under-spin your cd rom to the following speed (in terms of speed*150 kb/s, 
# for instance for 10x, set to "10") - needs "setcd" package installed. Set to "0" to disable
POWERSAVE_CD_SPEED="0";

# Determine wether we want to enable or disable power saving mode
if on_ac_power; then
  ENABLE="0";
else
  ENABLE="1";
fi

# Allow to enable power saving mode even when on AC power if run with 1st argument = 1
if [ "$1" == "1" ] ; then
  ENABLE="1";
fi

# == Section: Script logic start here ==

# Go fast when power saving mode is disabled.  Similar to default Ubuntu settings
if [ "$ENABLE" == "0" ] ; then

  echo "  * Disabling power saving mode..."

  # Restore of: If your system is stable, you can spare a few CPU cycles by disabling the surveillance of "Non Maskable Interrupt"
  # UNCERTAINTY - When is this necessary?
  # echo 1 > /proc/sys/kernel/nmi_watchdog

  # Restore default CPU voltages
  cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids > /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
  cat /sys/devices/system/cpu/cpu1/cpufreq/phc_default_vids > /sys/devices/system/cpu/cpu1/cpufreq/phc_vids

  # Enable Wake on LAN (check "sudo ethtool eth0" for what modes your card supports. XPS M1330 iwl4965 supports "g" only)
  ethtool -s eth0 wol g

  # Restore default eth0 speed
  # FIXME - WHAT ARE THE DEFAULTS?
  # ethtool -s eth0 speed 100 duplex half autoneg off

  # Set the drive to mostly stay awake
  hdparm -B 200 -S 240 -M 254 /dev/sda >> /dev/null

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  for i in $EXT3_PARTITIONS
  do mount -o remount,commit=600 $i
  done

  # Re-enable atime - FIXME - How is this done?
  for i in $NOATIME_PARTITIONS
  do mount -o remount,noatime $i
  done

  # Turn off the laptop mode disk optimization
  echo 0 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945/iwl4964 driver to no power savings
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level

  # Restore TX power to default 27 dBm
  iwconfig wlan0 txpower 27
  
  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Restore "Reduce Disk activity" to defaults
  echo 60 > /proc/sys/vm/swappiness
  echo 29 > /proc/sys/vm/dirty_expire_centisecs

  # Only wakeup every 60 seconds to see if we need to write dirty pages
  # By default this is every 5 seconds but, I prefer 60 to reduce disk
  # activity.
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs

  # Turn off sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  
  # Set the SATA to max performance
  for i in /sys/class/scsi_host/*/link_power_management_policy
  do echo max_performance > $i
  done

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Enable CD device polling
  hal-disable-polling --enable-polling --device /dev/scd0 &> /dev/null

  # Set head rate back to default (auto-detection)
  if [ ! "$POWERSAVE_CD_SPEED" == "0" ] ; then
    setcd -x 0 &> /dev/null
  fi

  if [ "$AGGR" == "1" ] ; then

    # Enable the webcam driver
    modprobe uvcvideo

    # Optional: Put back most of the bluetooth/usb subsystem
    modprobe  hci_usb
    modprobe  rfcomm
    modprobe  l2cap
    modprobe  bluetooth
    modprobe  usbhid
    modprobe  uhci_hcd
    modprobe  ehci_hcd

    # Start bluetooth services
    /etc/init.d/bluetooth start
    hciconfig hci0 up # Is this line necessary?

    # Configure to use two power cores
    echo 0 > /sys/devices/system/cpu/sched_mc_power_savings

  fi

else # Save power

  echo "  * Enabling power saving mode..."

  # If your system is stable, you can spare a few CPU cycles by disabling the surveillance of "Non Maskable Interrupt"
  # UNCERTAINTY - When is this necessary?
  # echo 0 > /proc/sys/kernel/nmi_watchdog

  # Reducing CPU voltage scale appr appr by 35% (the XPS will however not go under 19)
  echo "77:26 76:21 10:20 8:19 6:19 136:19" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:26 76:21 10:20 8:19 6:19 136:19" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls

  # Set the disks to aggressively save power and use the lowest acoustic level
  hdparm -B 1 -S 4 -M 128 /dev/sda >> /dev/null
  
  # Change the ext3 commit times to 10 minutes.  This reduces disk
  # activity
  for i in $EXT3_PARTITIONS
  do mount -o remount,commit=600 $i
  done

  # Disable atime for selection partitions
  for i in $NOATIME_PARTITIONS
  do mount -o remount,noatime $i
  done

  # Set laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945/iwl4965 driver to power savings.  
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level

  # Lower TX power from default 27 dBm to 7 dBm
  iwconfig wlan0 txpower 7

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # More "Reduce Disk activity" - (Is this necessary?)
  echo 10 > /proc/sys/vm/swappiness
  echo 0 > /proc/sys/vm/dirty_expire_centisecs

  # Set sound card power savings
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  # Set SATA to minimum power
  for i in /sys/class/scsi_host/*/link_power_management_policy
  do echo min_power > $i
  done

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Disable hal device polling for cd rom
  hal-disable-polling --device /dev/scd0 &> /dev/null

  # Set CD head rate down to 10x (for lower power usage / sound while on battery)
  if [ ! "$POWERSAVE_CD_SPEED" == "0" ] ; then
    setcd -x $POWERSAVE_CD_SPEED; &> /dev/null
  fi

  if [ "$AGGR" == "1" ] ; then

    # Stop bluetooth services
    /etc/init.d/bluetooth stop
    # hciconfig hci0 down; # Disabled as complains if bt already is disabled

    # Remove the webcam driver
    modprobe -r uvcvideo

    # Optional: Remove the most of the bluetooth/usb subsystem
    modprobe -r hci_usb
    modprobe -r rfcomm
    modprobe -r l2cap
    modprobe -r bluetooth
    modprobe -r usbhid
    modprobe -r uhci_hcd
    modprobe -r ehci_hcd

    # Configure to use only one power core
    echo 1 > /sys/devices/system/cpu/sched_mc_power_savings

  else # Try to enable USB auto-suspend only instead:

    # Auto Suspend Unused USB Buses (Timeout in seconds)
    for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 1 > $i
    done
    # USB Bus power levels -> auto = autosupend
    for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
    done

  fi

fi

# == Section: Needs restore commands + verification of necessity / explanation - currently inactivated ==

if false; then

  # Remove Other unnecessary modules
  hciconfig hci0 down
  MODULES="hci_usb rfcomm l2cap bluetooth usbhid uhci_hcd ehci_hcd i2c_algo_bit crc_ccitt joydev radeon serio_raw pcspkr i2c_i801 uvcvideo compat_ioctl32 videodev"
  for i in $MODULES
  do modprobe -r $i
  done

  # Re-enable USB for those who need
  modprobe uhci_hcd

fi
```

Diff (diff -w) against vor's version as of 14-jul-2008 03:00:
```
$ diff -w 99-battery-savings-xps 99-battery-savings-xps.org 
3,21c3
< # == Section: Variable declaration - determines some script behaviors ==
< 
< # Debug - remove #-sign to enable bash debug output
< #set -x;
< 
< # Specify ext3 partitions:
< EXT3_PARTITIONS=`cat /etc/mtab | grep ext3 | awk '{print $2}'`;
< 
< # Partitions to disable atime for:
< NOATIME_PARTITIONS=`cat /etc/mtab | grep -e 'ext3\|fat' | awk '{print $2}'`;
< 
< # Aggressive? Set to 1 to enable. Will disable web-cam, 2nd cpu core, usb and more. Inspect the code below for more details
< AGGR="1";
< 
< # Misc options - under-spin your cd rom to the following speed (in terms of speed*150 kb/s, 
< # for instance for 10x, set to "10") - needs "setcd" package installed. Set to "0" to disable
< POWERSAVE_CD_SPEED="0";
< 
< # Determine wether we want to enable or disable power saving mode
---
> # Go fast on AC power.  Similar to default Ubuntu settings
23,54d4
<   ENABLE="0";
< else
<   ENABLE="1";
< fi
< 
< # Allow to enable power saving mode even when on AC power if run with 1st argument = 1
< if [ "$1" == "1" ] ; then
<   ENABLE="1";
< fi
< 
< # == Section: Script logic start here ==
< 
< # Go fast when power saving mode is disabled.  Similar to default Ubuntu settings
< if [ "$ENABLE" == "0" ] ; then
< 
<   echo "  * Disabling power saving mode..."
< 
<   # Restore of: If your system is stable, you can spare a few CPU cycles by disabling the surveillance of "Non Maskable Interrupt"
<   # UNCERTAINTY - When is this necessary?
<   # echo 1 > /proc/sys/kernel/nmi_watchdog
< 
<   # Restore default CPU voltages
<   cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids > /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
<   cat /sys/devices/system/cpu/cpu1/cpufreq/phc_default_vids > /sys/devices/system/cpu/cpu1/cpufreq/phc_vids
< 
<   # Enable Wake on LAN (check "sudo ethtool eth0" for what modes your card supports. XPS M1330 iwl4965 supports "g" only)
<   ethtool -s eth0 wol g
< 
<   # Restore default eth0 speed
<   # FIXME - WHAT ARE THE DEFAULTS?
<   # ethtool -s eth0 speed 100 duplex half autoneg off
< 
56c6
<   hdparm -B 200 -S 240 -M 254 /dev/sda >> /dev/null
---
>   hdparm -B 200 -S 240 -M 254 /dev/sda
61,68c11,12
<   for i in $EXT3_PARTITIONS
<   do mount -o remount,commit=600 $i
<   done
< 
<   # Re-enable atime - FIXME - How is this done?
<   for i in $NOATIME_PARTITIONS
<   do mount -o remount,noatime $i
<   done
---
>   mount -o remount,commit=60 /
>   mount -o remount,commit=60 /home
73,77c17,20
<   # Manually set the iwl3945/iwl4964 driver to no power savings
<   echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level
< 
<   # Restore TX power to default 27 dBm
<   iwconfig wlan0 txpower 27
---
>   # Manually set the iwl3945 driver to no power savings.  This is machine
>   # specific and you may have to change both iwl3945 (to iwl4965) and the
>   # PCI address of the wifi card
>   echo 6 > "/sys/bus/pci/drivers/iwl3945/0000:0c:00.0/power_level"
83,86d25
<   # Restore "Reduce Disk activity" to defaults
<   echo 60 > /proc/sys/vm/swappiness
<   echo 29 > /proc/sys/vm/dirty_expire_centisecs
< 
96,98c35,36
<   for i in /sys/class/scsi_host/*/link_power_management_policy
<   do echo max_performance > $i
<   done
---
>   echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
>   echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy
103,112d40
<   # Enable CD device polling
<   hal-disable-polling --enable-polling --device /dev/scd0 &> /dev/null
< 
<   # Set head rate back to default (auto-detection)
<   if [ ! "$POWERSAVE_CD_SPEED" == "0" ] ; then
<     setcd -x 0 &> /dev/null
<   fi
< 
<   if [ "$AGGR" == "1" ] ; then
< 
116,133d43
<     # Optional: Put back most of the bluetooth/usb subsystem
<     modprobe  hci_usb
<     modprobe  rfcomm
<     modprobe  l2cap
<     modprobe  bluetooth
<     modprobe  usbhid
<     modprobe  uhci_hcd
<     modprobe  ehci_hcd
< 
<     # Start bluetooth services
<     /etc/init.d/bluetooth start
<     hciconfig hci0 up # Is this line necessary?
< 
<     # Configure to use two power cores
<     echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
< 
<   fi
< 
136,147c46,48
<   echo "  * Enabling power saving mode..."
< 
<   # If your system is stable, you can spare a few CPU cycles by disabling the surveillance of "Non Maskable Interrupt"
<   # UNCERTAINTY - When is this necessary?
<   # echo 0 > /proc/sys/kernel/nmi_watchdog
< 
<   # Reducing CPU voltage scale appr appr by 35% (the XPS will however not go under 19)
<   echo "77:26 76:21 10:20 8:19 6:19 136:19" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
<   echo "77:26 76:21 10:20 8:19 6:19 136:19" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
< 
<   # Set the disks to aggressively save power and use the lowest acoustic level
<   hdparm -B 1 -S 4 -M 128 /dev/sda >> /dev/null
---
>   # Set the disks to aggressively save power and use the lowest acoustic
>   # level
>   hdparm -B 1 -S 4 -M 128 /dev/sda
151,158c52
<   for i in $EXT3_PARTITIONS
<   do mount -o remount,commit=600 $i
<   done
< 
<   # Disable atime for selection partitions
<   for i in $NOATIME_PARTITIONS
<   do mount -o remount,noatime $i
<   done
---
>   mount -o remount,commit=600 /
163,167c57,60
<   # Manually set the iwl3945/iwl4965 driver to power savings.  
<   echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level
< 
<   # Lower TX power from default 27 dBm to 7 dBm
<   iwconfig wlan0 txpower 7
---
>   # Manually set the iwl3945 driver to power savings.  This is machine
>   # specific and you may have to change both iwl3945 (to iwl4965) and the
>   # PCI address of the wifi card
>   echo 5 > "/sys/bus/pci/drivers/iwl3945/0000:0c:00.0/power_level"
174,177d66
<   # More "Reduce Disk activity" - (Is this necessary?)
<   echo 10 > /proc/sys/vm/swappiness
<   echo 0 > /proc/sys/vm/dirty_expire_centisecs
< 
182,184c71,72
<   for i in /sys/class/scsi_host/*/link_power_management_policy
<   do echo min_power > $i
<   done
---
>   echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
>   echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
189,202d76
<   # Disable hal device polling for cd rom
<   hal-disable-polling --device /dev/scd0 &> /dev/null
< 
<   # Set CD head rate down to 10x (for lower power usage / sound while on battery)
<   if [ ! "$POWERSAVE_CD_SPEED" == "0" ] ; then
<     setcd -x $POWERSAVE_CD_SPEED; &> /dev/null
<   fi
< 
<   if [ "$AGGR" == "1" ] ; then
< 
<     # Stop bluetooth services
<     /etc/init.d/bluetooth stop
<     # hciconfig hci0 down; # Disabled as complains if bt already is disabled
< 
205,246d78
< 
<     # Optional: Remove the most of the bluetooth/usb subsystem
<     modprobe -r hci_usb
<     modprobe -r rfcomm
<     modprobe -r l2cap
<     modprobe -r bluetooth
<     modprobe -r usbhid
<     modprobe -r uhci_hcd
<     modprobe -r ehci_hcd
< 
<     # Configure to use only one power core
<     echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
< 
<   else # Try to enable USB auto-suspend only instead:
< 
<     # Auto Suspend Unused USB Buses (Timeout in seconds)
<     for i in /sys/bus/usb/devices/usb?/power/autosuspend
<     do echo 1 > $i
<     done
<     # USB Bus power levels -> auto = autosupend
<     for i in /sys/bus/usb/devices/usb?/power/level
<     do echo auto > $i
<     done
< 
<   fi
< 
< fi
< 
< # == Section: Needs restore commands + verification of necessity / explanation - currently inactivated ==
< 
< if false; then
< 
<   # Remove Other unnecessary modules
<   hciconfig hci0 down
<   MODULES="hci_usb rfcomm l2cap bluetooth usbhid uhci_hcd ehci_hcd i2c_algo_bit crc_ccitt joydev radeon serio_raw pcspkr i2c_i801 uvcvideo compat_ioctl32 videodev"
<   for i in $MODULES
<   do modprobe -r $i
<   done
< 
<   # Re-enable USB for those who need
<   modprobe uhci_hcd
< 

```

I'll update this post to stay up-to-date with comments and suggestions on this merged version.

Thanks about the tip on the "/proc/sys/vm/block_dump" setting btw - it lead to the discovery that timevault is not suitable to run while on battery.

HOWEVER: Even when running the most aggressive commands through the script, I still get no measurable power savings!
All I get is the annoying delays when the hard drive spins up (the whole computer lags for 0.5 secs everytime), but my watts are still around 19-22W as compared to 21-24W without any scripts... Not seeing any 13 W or 15 W wonder results here...

I am getting alot of the following wake-ups:
```
Wakeups-from-idle per second : 2308,1	interval: 60,0s
Power usage (ACPI estimate): 19,0W (1,0 hours) 
Top causes for wakeups:
  40,4% (911,8)      <kernel IPI> : Rescheduling interrupts 
  33,1% (746,7)       <interrupt> : extra timer interrupt 
  18,4% (415,5)       <interrupt> : PS/2 keyboard/mouse/touchpad 

```

Any other XPS owner that has experienced this and solved it? It certainly looks like a lot of power power can be saved by reducing the wake-ups from around 2300 -> ~100...

Cheers!

---

### Post by bubbalouie on 2008-07-13
I found that some applets I had running in the kicker (KDE task bar for gnome users) were causing a lot of wakeups, interestingly, kicker was reporting about 500 whilst the Kernel IPI reported a similar number (the kernel IPI number seems almost like it should be ignored), removing the offending applets from kicker saved me close to 1000 wakeups (including the kernel IPI). I recommend closing all the applications and applets so you have a barebones desktop running and seeing what happens, in either case, anything over 80 wakeups a second for an idle laptop is just huge (I get 45-65 [including kernel IPI] with no extra apps running besides the core desktop). The built in trackpad and keyboard also generate a lot of wakeups when being used (upto 600 a second if you move your finger quickly), try to avoid touching the laptop when it is gathering the wakeup numbers and see what happens. Also, if you haven't already done so, turning off 3D desktops would help with power (nvidia chips are a nightmare for power usage, just watch how hot those things get)...

Good luck

Ryan

---

### Post by sdennie on 2008-07-14
> **motin said:**
> 
According to the comments in the bug report (one of them being my own...)
fsyncs are still issued by the firefox version shipped in the 8.04.1 update :(

In other words, it looks like it didn't make it this time - so do you have any plans on using/trying a proposed work-around?


I did find a workaround but, the side effects were too dire to recommend it.  You can use a bit of javascript to prevent the sqlite DBs from doing fsync but, I had a lot of problems with bookmarks seeming to then never get saved.  I may see if I can find another browser (maybe back to Epiphany) that doesn't have that absurd behavior.

> 
tinivole's version is more generic. Use the following to alter the power saving levels instead:
```
echo 6 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level
```
and
```
echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level
```
respectively.

vor, maybe you can include this change in the OP?

Yes, I can add that.

> **motin said:**
> 
Whole current merged script:
```
#!/bin/bash

# == Section: Variable declaration - determines some script behaviors ==

# Debug - remove #-sign to enable bash debug output
#set -x;

# Specify ext3 partitions:
EXT3_PARTITIONS=`cat /etc/mtab | grep ext3 | awk '{print $2}'`;

# Partitions to disable atime for:
NOATIME_PARTITIONS=`cat /etc/mtab | grep -e 'ext3\|fat' | awk '{print $2}'`;

# Aggressive? Set to 1 to enable. Will disable web-cam, 2nd cpu core, usb and more. Inspect the code below for more details
AGGR="1";

# Misc options - under-spin your cd rom to the following speed (in terms of speed*150 kb/s, 
# for instance for 10x, set to "10") - needs "setcd" package installed. Set to "0" to disable
POWERSAVE_CD_SPEED="0";

# Determine wether we want to enable or disable power saving mode
if on_ac_power; then
  ENABLE="0";
else
  ENABLE="1";
fi

# Allow to enable power saving mode even when on AC power if run with 1st argument = 1
if [ "$1" == "1" ] ; then
  ENABLE="1";
fi

# == Section: Script logic start here ==

# Go fast when power saving mode is disabled.  Similar to default Ubuntu settings
if [ "$ENABLE" == "0" ] ; then

  echo "  * Disabling power saving mode..."

  # Restore of: If your system is stable, you can spare a few CPU cycles by disabling the surveillance of "Non Maskable Interrupt"
  # UNCERTAINTY - When is this necessary?
  # echo 1 > /proc/sys/kernel/nmi_watchdog

  # Restore default CPU voltages
  cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids > /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
  cat /sys/devices/system/cpu/cpu1/cpufreq/phc_default_vids > /sys/devices/system/cpu/cpu1/cpufreq/phc_vids

  # Enable Wake on LAN (check "sudo ethtool eth0" for what modes your card supports. XPS M1330 iwl4965 supports "g" only)
  ethtool -s eth0 wol g

  # Restore default eth0 speed
  # FIXME - WHAT ARE THE DEFAULTS?
  # ethtool -s eth0 speed 100 duplex half autoneg off

  # Set the drive to mostly stay awake
  hdparm -B 200 -S 240 -M 254 /dev/sda >> /dev/null

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  for i in $EXT3_PARTITIONS
  do mount -o remount,commit=600 $i
  done

  # Re-enable atime - FIXME - How is this done?
  for i in $NOATIME_PARTITIONS
  do mount -o remount,noatime $i
  done

  # Turn off the laptop mode disk optimization
  echo 0 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945/iwl4964 driver to no power savings
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level

  # Restore TX power to default 27 dBm
  iwconfig wlan0 txpower 27
  
  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Restore "Reduce Disk activity" to defaults
  echo 60 > /proc/sys/vm/swappiness
  echo 29 > /proc/sys/vm/dirty_expire_centisecs

  # Only wakeup every 60 seconds to see if we need to write dirty pages
  # By default this is every 5 seconds but, I prefer 60 to reduce disk

  # activity.
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs

  # Turn off sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  
  # Set the SATA to max performance
  for i in /sys/class/scsi_host/*/link_power_management_policy
  do echo max_performance > $i
  done

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Enable CD device polling
  hal-disable-polling --enable-polling --device /dev/scd0 &> /dev/null

  # Set head rate back to default (auto-detection)
  if [ ! "$POWERSAVE_CD_SPEED" == "0" ] ; then
    setcd -x 0 &> /dev/null
  fi

  if [ "$AGGR" == "1" ] ; then

    # Enable the webcam driver
    modprobe uvcvideo

    # Optional: Put back most of the bluetooth/usb subsystem
    modprobe  hci_usb
    modprobe  rfcomm
    modprobe  l2cap
    modprobe  bluetooth
    modprobe  usbhid
    modprobe  uhci_hcd
    modprobe  ehci_hcd

    # Start bluetooth services
    /etc/init.d/bluetooth start
    hciconfig hci0 up # Is this line necessary?

    # Configure to use two power cores
    echo 0 > /sys/devices/system/cpu/sched_mc_power_savings

  fi

else # Save power

  echo "  * Enabling power saving mode..."

  # If your system is stable, you can spare a few CPU cycles by disabling the surveillance of "Non Maskable Interrupt"
  # UNCERTAINTY - When is this necessary?
  # echo 0 > /proc/sys/kernel/nmi_watchdog

  # Reducing CPU voltage scale appr appr by 35% (the XPS will however not go under 19)
  echo "77:26 76:21 10:20 8:19 6:19 136:19" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:26 76:21 10:20 8:19 6:19 136:19" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls

  # Set the disks to aggressively save power and use the lowest acoustic level
  hdparm -B 1 -S 4 -M 128 /dev/sda >> /dev/null
  
  # Change the ext3 commit times to 10 minutes.  This reduces disk
  # activity
  for i in $EXT3_PARTITIONS
  do mount -o remount,commit=600 $i
  done

  # Disable atime for selection partitions
  for i in $NOATIME_PARTITIONS
  do mount -o remount,noatime $i
  done

  # Set laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945/iwl4965 driver to power savings.  
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level

  # Lower TX power from default 27 dBm to 7 dBm
  iwconfig wlan0 txpower 7

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # More "Reduce Disk activity" - (Is this necessary?)
  echo 10 > /proc/sys/vm/swappiness
  echo 0 > /proc/sys/vm/dirty_expire_centisecs

  # Set sound card power savings
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  # Set SATA to minimum power
  for i in /sys/class/scsi_host/*/link_power_management_policy
  do echo min_power > $i
  done

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Disable hal device polling for cd rom
  hal-disable-polling --device /dev/scd0 &> /dev/null

  # Set CD head rate down to 10x (for lower power usage / sound while on battery)
  if [ ! "$POWERSAVE_CD_SPEED" == "0" ] ; then
    setcd -x $POWERSAVE_CD_SPEED; &> /dev/null
  fi

  if [ "$AGGR" == "1" ] ; then

    # Stop bluetooth services
    /etc/init.d/bluetooth stop
    # hciconfig hci0 down; # Disabled as complains if bt already is disabled

    # Remove the webcam driver
    modprobe -r uvcvideo

    # Optional: Remove the most of the bluetooth/usb subsystem
    modprobe -r hci_usb
    modprobe -r rfcomm
    modprobe -r l2cap
    modprobe -r bluetooth
    modprobe -r usbhid
    modprobe -r uhci_hcd
    modprobe -r ehci_hcd

    # Configure to use only one power core
    echo 1 > /sys/devices/system/cpu/sched_mc_power_savings

  else # Try to enable USB auto-suspend only instead:

    # Auto Suspend Unused USB Buses (Timeout in seconds)
    for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 1 > $i
    done
    # USB Bus power levels -> auto = autosupend
    for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
    done

  fi

fi

# == Section: Needs restore commands + verification of necessity / explanation - currently inactivated ==

if false; then

  # Remove Other unnecessary modules
  hciconfig hci0 down
  MODULES="hci_usb rfcomm l2cap bluetooth usbhid uhci_hcd ehci_hcd i2c_algo_bit crc_ccitt joydev radeon serio_raw pcspkr i2c_i801 uvcvideo compat_ioctl32 videodev"
  for i in $MODULES
  do modprobe -r $i
  done

  # Re-enable USB for those who need
  modprobe uhci_hcd

fi
```


This script looks great.  I'll test it out a bit.  I can either link directly to your post from the first post or replace the original script script with this one.  Let me know which you'd prefer.

> 
I am getting alot of the following wake-ups:
```
Wakeups-from-idle per second : 2308,1	interval: 60,0s
Power usage (ACPI estimate): 19,0W (1,0 hours) 
Top causes for wakeups:
  40,4% (911,8)      <kernel IPI> : Rescheduling interrupts 
  33,1% (746,7)       <interrupt> : extra timer interrupt 
  18,4% (415,5)       <interrupt> : PS/2 keyboard/mouse/touchpad 

```


> **bubbalouie said:**
> I found that some applets I had running in the kicker (KDE task bar for gnome users) were causing a lot of wakeups, interestingly, kicker was reporting about 500 whilst the Kernel IPI reported a similar number (the kernel IPI number seems almost like it should be ignored), removing the offending applets from kicker saved me close to 1000 wakeups (including the kernel IPI). I recommend closing all the applications and applets so you have a barebones desktop running and seeing what happens, in either case, anything over 80 wakeups a second for an idle laptop is just huge (I get 45-65 [including kernel IPI] with no extra apps running besides the core desktop). The built in trackpad and keyboard also generate a lot of wakeups when being used (upto 600 a second if you move your finger quickly), try to avoid touching the laptop when it is gathering the wakeup numbers and see what happens. Also, if you haven't already done so, turning off 3D desktops would help with power (nvidia chips are a nightmare for power usage, just watch how hot those things get)...


If I remember right, the kernel IPI is when the kernel reschedules things from one core to another.  In 2.6.24 it's particularly bad (but not in 2.6.22 or 2.6.26).  You can take one of your cores offline on battery to prevent them but, that actually increases power usage.  2300 is very high but, with normal apps running but idle, around 100 isn't bad and reducing them to insane levels (I can get as low as 15ish using fluxbox) doesn't save as much power as one would hope.

Your laptop spends most of its time idle so, as bubbalouie said, to get an accurate measurement, you should really set powertop to run and then walk away from the computer (60 seconds is good but 5 minutes is probably better).  That's not going to give you a number that will tell you how long the battery will actually last but, it's the only way to get semi-consistent numbers that you can use for comparison for most of the changes you make.

---

### Post by atlas95 on 2008-07-14
So good ! We can maybe use the intrepid kernel for ipi problem?

---

### Post by sultanoswing on 2008-07-14
Dagnabbit!

I compiled my own kernel (2.6.24.3, from 2.6.26 sources) as I needed force feedback support. I was using the 99-scripts previously successfully on Hardy Heron, default 64-bit install with latest kernel - I have of course I kept the old kernel for when I don't want to run the force feedback (which solves the below issue).

I thought I'd checked the relevant hardware and power saving features in makeconfig, but now when I run the new kernel under AC power using the 99-scripts, the discs spin up frequently and powermizer shows the 8400M is at level '0' (it will wake up with activity) and interestingly shows the laptop on 'Battery' power, even though the taskbar notification area shows 'AC Power' with the correct icon. I'm using the nvidia tweak found here [http://ubuntuforums.org/showthread.php?t=828369&highlight=nvidia+full+speed+power](http://ubuntuforums.org/showthread.php?t=828369&highlight=nvidia+full+speed+power). Powermizer correctly reads the state by unplugging and replugging the power cable.

The following script helpfully stopped the excess hard drive spin ups:

```
sudo hdparm -B 200 -S 240 -M 254 /dev/sda >> /dev/null
```

...but was also reversed back to frequent spin ups by unplugging and replugging the AC power.

I'm guessing that somehow it seems to be confused between AC and Battery power.

While I appreciate that by 'rolling my own' I "broke my Ubuntu warranty", I'd be grateful if you have any obvious suggestions as to what could be going on and possible fixes. In the meantime, it's back to 2.6.24-19-generic!

Thanks in advance.

---

### Post by bubbalouie on 2008-07-15
I thought I'd share what I have done, given that it has borrowed a fair amount from Vor's, lesswatts.org', & Motin's original work but deviates slightly in its application.

I have configured my /etc/fstab to only use relatime on the root partition (noatime on home), also, I use laptop-mode-tools to handle hard disk spin down, head parking and atime on my root partition, the following link was my basis for configuring laptop-mode-tools:

[http://vale.homelinux.net/wordpress/2007/10/24/potential-risk-for-your-nx6325s-harddrive/](http://vale.homelinux.net/wordpress/2007/10/24/potential-risk-for-your-nx6325s-harddrive/)

I have undervolted my CPU, the following link should help:

[http://ubuntuforums.org/showthread.php?t=786402&page=6](http://ubuntuforums.org/showthread.php?t=786402&page=6)

The key difference is that I have invoked a default power profile at boot (for reference it is number 2), KDE power manager handles my CPU scaling policy, and laptop-mode-tools do the rest of the automagic stuff, the heavily customised parts I handle from a small menu on my kicker. This way I can switch between 'power states' when I see fit, thus if I decide I want my webcam I just pick the next power mode in the list (and vice versa). The script is below:

```
#!/bin/bash

export POWERMODE=$1

# This script must be run from a root console
if [ "$POWERMODE" == "-1" ];then
  echo "Invoking EXTREME power saving state"
  echo "  Enabling MC power saving scheduler"
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
  echo "  Disabling wake on LAN"
  ethtool -s eth0 wol d
  echo "  Lowering WiFi power level"
  echo 5 > /sys/bus/pci/drivers/iwl????/*/power_level >/dev/null
  echo "  Increasing dirty writeback time"
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo "  Increasing VM dirty ratio"
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo "  Disabling DVD-ROM Polling"
  hal-disable-polling --device /dev/scd0 >> /dev/null
  echo "  Enabling Intel HDA power saver"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo "  Stopping 'cron'"
  /etc/init.d/cron stop >> /dev/null
  echo "  Stopping 'anacron'"
  /etc/init.d/anacron stop >> /dev/null
  echo "  Stopping 'klogd'"
  /etc/init.d/klogd stop >> /dev/null
  echo "  Stopping 'sysklogd'"
  /etc/init.d/sysklogd stop >> /dev/null
  echo "  Reducing CPU voltage scale by 30%"
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
  echo "  Starting laptop mode"
  echo 5 > /proc/sys/vm/laptop_mode
  echo "  Enabling SATA ALPM power management mode"
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
  echo "  Unloading WebCam Driver"
  modprobe -r uvcvideo
  echo "  Unloading USB & Bluetooth Subsystem"
  /etc/init.d/bluetooth stop >> /dev/null
  modprobe -r hci_usb
  modprobe -r rfcomm
  modprobe -r l2cap
  modprobe -r bluetooth
  modprobe -r usbhid
  modprobe -r uhci_hcd
  modprobe -r ehci_hcd
  echo "Extreme powersaving features now enabled (USB & Bluetooth off)"
elif [ "$POWERMODE" == "0" ];then
  echo "Invoking lowest functional power state"
  echo "  Enabling MC power saving scheduler"
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
  echo "  Disabling wake on LAN"
  ethtool -s eth0 wol d
  echo "  Lowering WiFi power level"
  echo 5 > /sys/bus/pci/drivers/iwl????/*/power_level >/dev/null
  echo "  Increasing dirty writeback time"
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo "  Increasing VM dirty ratio"
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo "  Disabling DVD-ROM Polling"
  hal-disable-polling --device /dev/scd0 >> /dev/null
  echo "  Enabling Intel HDA power saver"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo "  Stopping 'cron'"
  /etc/init.d/cron stop >> /dev/null
  echo "  Stopping 'anacron'"
  /etc/init.d/anacron stop >> /dev/null
  echo "  Stopping 'klogd'"
  /etc/init.d/klogd stop >> /dev/null
  echo "  Stopping 'sysklogd'"
  /etc/init.d/sysklogd stop >> /dev/null
  echo "  Reducing CPU voltage scale by 30%"
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
  echo "  Starting laptop mode"
  echo 5 > /proc/sys/vm/laptop_mode
  echo "  Enabling SATA ALPM power management mode"
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
  echo "  Unloading WebCam Driver"
  modprobe -r uvcvideo
  echo "  Loading USB & Bluetooth Subsystem"
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd
  /etc/init.d/bluetooth start >> /dev/null
  echo "  Enabling USB auto suspend"
  # Auto Suspend Unused USB Buses (Timeout in seconds)
  for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 1 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
  done
  echo "Maximum powersaving features now enabled (USB & Bluetooth on)"
elif [ "$POWERMODE" == "1" ]; then
  echo "Invoking low power state"
  echo "  Enabling MC power saving scheduler"
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
  echo "  Disabling wake on LAN"
  ethtool -s eth0 wol d
  echo "  Lowering WiFi power level"
  echo 5 > /sys/bus/pci/drivers/iwl????/*/power_level >/dev/null
  echo "  Increasing dirty writeback time"
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo "  Increasing VM dirty ratio"
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo "  Disabling DVD-ROM Polling"
  hal-disable-polling --device /dev/scd0 >> /dev/null
  echo "  Enabling Intel HDA power saver"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo "  Stopping 'cron'"
  /etc/init.d/cron stop >> /dev/null
  echo "  Stopping 'anacron'"
  /etc/init.d/anacron stop >> /dev/null
  echo "  Stopping 'klogd'"
  /etc/init.d/klogd stop >> /dev/null
  echo "  Stopping 'sysklogd'"
  /etc/init.d/sysklogd stop >> /dev/null
  echo "  Reducing CPU voltage scale by 30%"
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
  echo "  Starting laptop mode"
  echo 5 > /proc/sys/vm/laptop_mode
  echo "  Enabling SATA ALPM power management mode"
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
  echo "  Loading WebCam Driver"
  modprobe uvcvideo
  echo "  Loading USB & Bluetooth Subsystem"
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd
  /etc/init.d/bluetooth start >> /dev/null
  echo "  Enabling USB auto suspend"
  # Auto Suspend Unused USB Buses (Timeout in seconds)
  for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 1 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
  done
  echo "Powersaving features now enabled"
elif [ "$POWERMODE" == "2" ];then
  echo "Invoking normal power state"
  echo "  Enabling MC power saving scheduler"
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
  echo "  Disabling wake on LAN"
  ethtool -s eth0 wol d
  echo "  Lowering WiFi power level"
  echo 5 > /sys/bus/pci/drivers/iwl????/*/power_level >/dev/null
  echo "  Decreasing dirty writeback time"
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo "  Adjusting VM dirty ratio"
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo "  Enabling SATA ALPM power management mode"
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
  echo "  Enabling DVD-ROM polling"
  hal-disable-polling --device /dev/scd0 --enable-polling >> /dev/null
  echo "  Disabling Intel HDA power saver"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo "  Starting 'cron'"
  /etc/init.d/cron start >> /dev/null
  echo "  Starting 'anacron'"
  /etc/init.d/anacron start >> /dev/null
  echo "  Starting 'klogd'"
  /etc/init.d/klogd start >> /dev/null
  echo "  Starting 'sysklogd'"
  /etc/init.d/sysklogd start >> /dev/null
  echo "  Reducing CPU voltage scale by 30%"
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
  echo "  Starting laptop mode"
  echo 5 > /proc/sys/vm/laptop_mode
  echo "  Loading WebCam Driver"
  modprobe uvcvideo
  echo "  Loading USB & Bluetooth Subsystem"
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd
  /etc/init.d/bluetooth start >> /dev/null
  echo "  Enabling USB auto suspend"
  # Auto Suspend Unused USB Buses (Timeout in seconds)
  for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 1 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
  done
  echo "Medium powersaving mode now enabled"
elif [ "$POWERMODE" == "3" ];then
  echo "Invoking performance power state"
  echo "  Disabling MC power saving scheduler"
  echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
  echo "  Restoring WiFi power level"
  echo 6 > /sys/bus/pci/drivers/iwl????/*/power_level >/dev/null
  echo "  Decreasing dirty writeback time"
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo "  Adjusting VM dirty ratio"
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo "  Disabling SATA ALPM power management mode"
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy
  echo "  Enabling DVD-ROM polling"
  hal-disable-polling --device /dev/scd0 --enable-polling >> /dev/null
  echo "  Disabling Intel HDA power saver"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo "  Starting 'cron'"
  /etc/init.d/cron start >> /dev/null
  echo "  Starting 'anacron'"
  /etc/init.d/anacron start >> /dev/null
  echo "  Starting 'klogd'"
  /etc/init.d/klogd start >> /dev/null
  echo "  Starting 'sysklogd'"
  /etc/init.d/sysklogd start >> /dev/null
  echo "  Restoring CPU voltage scale"
  echo "77:41 76:34 10:30 8:27 6:23 136:17" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:41 76:34 10:30 8:27 6:23 136:17" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
  echo "  Loading WebCam Driver"
  modprobe uvcvideo
  echo "  Loading USB & Bluetooth Subsystem"
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd
  /etc/init.d/bluetooth start >> /dev/null
  echo "  Enabling USB auto suspend"
  # Auto Suspend Unused USB Buses (Timeout in seconds)
  for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 2 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
  done
  echo "Powersaving features now disabled"
else
  echo "Usage: powermode <option> [interactive]"
  echo "Valid options are: -1 (Extreme savings camera, USB, bluetooth & DVD polling off)"
  echo "                   0 (Maximum power saving, camera & DVD polling off)"
  echo "                   1 (Nornaml power saving, DVD polling off)"
  echo "                   2 (Default mode)"
  echo "                   3 (Performance mode)"
  echo "If interactive=yes then prompt the user to press enter"
fi

if  [ "$2" == "yes" ];then
echo ""
read -p "Press \"Enter\" to close"
fi

```

To launch the script something like the following is run:

```
kdesudo 'konsole --vt_sz 80x24 --nomenubar --notabbar --noscrollbar --noresize --schema Transparent_darkbg.schema  -e sudo bash powermode 0 yes'
```

I also have 3 extra options in my kicker list, 'Enable DVD polling', 'Disable DVD polling' & finally 'Underclock GPU', the Underclock GPU command is below:

```
nvidia-settings --assign "[gpu:0]/GPUOverclockingState=1" --assign "[gpu:0]/GPU2DClockFreqs=169,100" --assign="[gpu:0]/GPU3DClockFreqs=169,150" 
```

My approach tends to be a bit more 'hackey' than the tightly integrated solution everyone else is running (just for starters it blindly tries to reload modules rather than checking if it needs doing), however, for those who like a little more 'control', perhaps this will save some time and effort.

Cheers

Ryan

---

### Post by sdennie on 2008-07-15
Updated the original post to point to the various other scripts that people have written in this thread.

---

### Post by atlas95 on 2008-07-15
> **bubbalouie said:**
> I thought I'd share what I have done, given that it has borrowed a fair amount from Vor's, lesswatts.org', & Motin's original work but deviates slightly in its application.

I have configured my /etc/fstab to only use relatime on the root partition (noatime on home), also, I use laptop-mode-tools to handle hard disk spin down, head parking and atime on my root partition, the following link was my basis for configuring laptop-mode-tools:

[http://vale.homelinux.net/wordpress/2007/10/24/potential-risk-for-your-nx6325s-harddrive/](http://vale.homelinux.net/wordpress/2007/10/24/potential-risk-for-your-nx6325s-harddrive/)

I have undervolted my CPU, the following link should help:

[http://ubuntuforums.org/showthread.php?t=786402&page=6](http://ubuntuforums.org/showthread.php?t=786402&page=6)

The key difference is that I have invoked a default power profile at boot (for reference it is number 2), KDE power manager handles my CPU scaling policy, and laptop-mode-tools do the rest of the automagic stuff, the heavily customised parts I handle from a small menu on my kicker. This way I can switch between 'power states' when I see fit, thus if I decide I want my webcam I just pick the next power mode in the list (and vice versa). The script is below:

```
#!/bin/bash

export POWERMODE=$1

# This script must be run from a root console
if [ "$POWERMODE" == "-1" ];then
  echo "Invoking EXTREME power saving state"
  echo "  Enabling MC power saving scheduler"
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
  echo "  Disabling wake on LAN"
  ethtool -s eth0 wol d
  echo "  Lowering WiFi power level"
  echo 5 > /sys/bus/pci/drivers/iwl????/*/power_level >/dev/null
  echo "  Increasing dirty writeback time"
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo "  Increasing VM dirty ratio"
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo "  Disabling DVD-ROM Polling"
  hal-disable-polling --device /dev/scd0 >> /dev/null
  echo "  Enabling Intel HDA power saver"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo "  Stopping 'cron'"
  /etc/init.d/cron stop >> /dev/null
  echo "  Stopping 'anacron'"
  /etc/init.d/anacron stop >> /dev/null
  echo "  Stopping 'klogd'"
  /etc/init.d/klogd stop >> /dev/null
  echo "  Stopping 'sysklogd'"
  /etc/init.d/sysklogd stop >> /dev/null
  echo "  Reducing CPU voltage scale by 30%"
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
  echo "  Starting laptop mode"
  echo 5 > /proc/sys/vm/laptop_mode
  echo "  Enabling SATA ALPM power management mode"
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
  echo "  Unloading WebCam Driver"
  modprobe -r uvcvideo
  echo "  Unloading USB & Bluetooth Subsystem"
  /etc/init.d/bluetooth stop >> /dev/null
  modprobe -r hci_usb
  modprobe -r rfcomm
  modprobe -r l2cap
  modprobe -r bluetooth
  modprobe -r usbhid
  modprobe -r uhci_hcd
  modprobe -r ehci_hcd
  echo "Extreme powersaving features now enabled (USB & Bluetooth off)"
elif [ "$POWERMODE" == "0" ];then
  echo "Invoking lowest functional power state"
  echo "  Enabling MC power saving scheduler"
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
  echo "  Disabling wake on LAN"
  ethtool -s eth0 wol d
  echo "  Lowering WiFi power level"
  echo 5 > /sys/bus/pci/drivers/iwl????/*/power_level >/dev/null
  echo "  Increasing dirty writeback time"
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo "  Increasing VM dirty ratio"
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo "  Disabling DVD-ROM Polling"
  hal-disable-polling --device /dev/scd0 >> /dev/null
  echo "  Enabling Intel HDA power saver"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo "  Stopping 'cron'"
  /etc/init.d/cron stop >> /dev/null
  echo "  Stopping 'anacron'"
  /etc/init.d/anacron stop >> /dev/null
  echo "  Stopping 'klogd'"
  /etc/init.d/klogd stop >> /dev/null
  echo "  Stopping 'sysklogd'"
  /etc/init.d/sysklogd stop >> /dev/null
  echo "  Reducing CPU voltage scale by 30%"
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
  echo "  Starting laptop mode"
  echo 5 > /proc/sys/vm/laptop_mode
  echo "  Enabling SATA ALPM power management mode"
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
  echo "  Unloading WebCam Driver"
  modprobe -r uvcvideo
  echo "  Loading USB & Bluetooth Subsystem"
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd
  /etc/init.d/bluetooth start >> /dev/null
  echo "  Enabling USB auto suspend"
  # Auto Suspend Unused USB Buses (Timeout in seconds)
  for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 1 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
  done
  echo "Maximum powersaving features now enabled (USB & Bluetooth on)"
elif [ "$POWERMODE" == "1" ]; then
  echo "Invoking low power state"
  echo "  Enabling MC power saving scheduler"
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
  echo "  Disabling wake on LAN"
  ethtool -s eth0 wol d
  echo "  Lowering WiFi power level"
  echo 5 > /sys/bus/pci/drivers/iwl????/*/power_level >/dev/null
  echo "  Increasing dirty writeback time"
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo "  Increasing VM dirty ratio"
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo "  Disabling DVD-ROM Polling"
  hal-disable-polling --device /dev/scd0 >> /dev/null
  echo "  Enabling Intel HDA power saver"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo "  Stopping 'cron'"
  /etc/init.d/cron stop >> /dev/null
  echo "  Stopping 'anacron'"
  /etc/init.d/anacron stop >> /dev/null
  echo "  Stopping 'klogd'"
  /etc/init.d/klogd stop >> /dev/null
  echo "  Stopping 'sysklogd'"
  /etc/init.d/sysklogd stop >> /dev/null
  echo "  Reducing CPU voltage scale by 30%"
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
  echo "  Starting laptop mode"
  echo 5 > /proc/sys/vm/laptop_mode
  echo "  Enabling SATA ALPM power management mode"
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
  echo "  Loading WebCam Driver"
  modprobe uvcvideo
  echo "  Loading USB & Bluetooth Subsystem"
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd
  /etc/init.d/bluetooth start >> /dev/null
  echo "  Enabling USB auto suspend"
  # Auto Suspend Unused USB Buses (Timeout in seconds)
  for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 1 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
  done
  echo "Powersaving features now enabled"
elif [ "$POWERMODE" == "2" ];then
  echo "Invoking normal power state"
  echo "  Enabling MC power saving scheduler"
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
  echo "  Disabling wake on LAN"
  ethtool -s eth0 wol d
  echo "  Lowering WiFi power level"
  echo 5 > /sys/bus/pci/drivers/iwl????/*/power_level >/dev/null
  echo "  Decreasing dirty writeback time"
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo "  Adjusting VM dirty ratio"
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo "  Enabling SATA ALPM power management mode"
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
  echo "  Enabling DVD-ROM polling"
  hal-disable-polling --device /dev/scd0 --enable-polling >> /dev/null
  echo "  Disabling Intel HDA power saver"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo "  Starting 'cron'"
  /etc/init.d/cron start >> /dev/null
  echo "  Starting 'anacron'"
  /etc/init.d/anacron start >> /dev/null
  echo "  Starting 'klogd'"
  /etc/init.d/klogd start >> /dev/null
  echo "  Starting 'sysklogd'"
  /etc/init.d/sysklogd start >> /dev/null
  echo "  Reducing CPU voltage scale by 30%"
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
  echo "  Starting laptop mode"
  echo 5 > /proc/sys/vm/laptop_mode
  echo "  Loading WebCam Driver"
  modprobe uvcvideo
  echo "  Loading USB & Bluetooth Subsystem"
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd
  /etc/init.d/bluetooth start >> /dev/null
  echo "  Enabling USB auto suspend"
  # Auto Suspend Unused USB Buses (Timeout in seconds)
  for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 1 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
  done
  echo "Medium powersaving mode now enabled"
elif [ "$POWERMODE" == "3" ];then
  echo "Invoking performance power state"
  echo "  Disabling MC power saving scheduler"
  echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
  echo "  Restoring WiFi power level"
  echo 6 > /sys/bus/pci/drivers/iwl????/*/power_level >/dev/null
  echo "  Decreasing dirty writeback time"
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo "  Adjusting VM dirty ratio"
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo "  Disabling SATA ALPM power management mode"
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy
  echo "  Enabling DVD-ROM polling"
  hal-disable-polling --device /dev/scd0 --enable-polling >> /dev/null
  echo "  Disabling Intel HDA power saver"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo "  Starting 'cron'"
  /etc/init.d/cron start >> /dev/null
  echo "  Starting 'anacron'"
  /etc/init.d/anacron start >> /dev/null
  echo "  Starting 'klogd'"
  /etc/init.d/klogd start >> /dev/null
  echo "  Starting 'sysklogd'"
  /etc/init.d/sysklogd start >> /dev/null
  echo "  Restoring CPU voltage scale"
  echo "77:41 76:34 10:30 8:27 6:23 136:17" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:41 76:34 10:30 8:27 6:23 136:17" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
  echo "  Loading WebCam Driver"
  modprobe uvcvideo
  echo "  Loading USB & Bluetooth Subsystem"
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd
  /etc/init.d/bluetooth start >> /dev/null
  echo "  Enabling USB auto suspend"
  # Auto Suspend Unused USB Buses (Timeout in seconds)
  for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 2 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
  done
  echo "Powersaving features now disabled"
else
  echo "Usage: powermode <option> [interactive]"
  echo "Valid options are: -1 (Extreme savings camera, USB, bluetooth & DVD polling off)"
  echo "                   0 (Maximum power saving, camera & DVD polling off)"
  echo "                   1 (Nornaml power saving, DVD polling off)"
  echo "                   2 (Default mode)"
  echo "                   3 (Performance mode)"
  echo "If interactive=yes then prompt the user to press enter"
fi

if  [ "$2" == "yes" ];then
echo ""
read -p "Press \"Enter\" to close"
fi

```

To launch the script something like the following is run:

```
kdesudo 'konsole --vt_sz 80x24 --nomenubar --notabbar --noscrollbar --noresize --schema Transparent_darkbg.schema  -e sudo bash powermode 0 yes'
```

I also have 3 extra options in my kicker list, 'Enable DVD polling', 'Disable DVD polling' & finally 'Underclock GPU', the Underclock GPU command is below:

```
nvidia-settings --assign "[gpu:0]/GPUOverclockingState=1" --assign "[gpu:0]/GPU2DClockFreqs=169,100" --assign="[gpu:0]/GPU3DClockFreqs=169,150" 
```

My approach tends to be a bit more 'hackey' than the tightly integrated solution everyone else is running (just for starters it blindly tries to reload modules rather than checking if it needs doing), however, for those who like a little more 'control', perhaps this will save some time and effort.

Cheers

Ryan

This will be wonderfull with a zenity gui or gtk gui !

---

### Post by sdennie on 2008-07-15
For anyone running the new 2.6.26 kernel, [the PCI Express power savings]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=7d715a6c1ae5785d00fb9a876b5abdfc43abc44b") seems to save a huge amount of power (about 0.7W).  The commands to do this are:

```

# Use default on AC
echo default > /sys/module/pcie_aspm/parameters/policy

```

And, on battery:
```

# Use powersave on battery
echo powersave > /sys/module/pcie_aspm/parameters/policy

```

There is also a "performance" setting but, it makes the power usage so incredibly high that it can't be what the BIOS is using by default so I'm not willing to use it.

This gets me down to around 10W with wifi on, backlight all the way down, normal apps open and an otherwise idle machine.  After trying about 10 60s tests at "default" and "powersave", the best I got on "default" was around 11.1W and the best on "powersave" was 10.3W:

```

$ sudo powertop -d -t 60
PowerTOP 1.9    (C) 2007 Intel Corporation 

Collecting data for 60 seconds 
Cn	          Avg residency
C0 (cpu running)        ( 2.5%)
C1		  0.0ms ( 0.0%)
C2		  0.0ms ( 0.0%)
C3		 10.9ms (97.5%)
P-states (frequencies)
  2.51 Ghz    34.3%
  2.50 Ghz     0.0%
  2.00 Ghz     0.0%
   800 Mhz    65.7%
Wakeups-from-idle per second : 90.3	interval: 60.0s
Power usage (ACPI estimate): 10.3W (8.1 hours) 
Top causes for wakeups:
  34.6% ( 26.5)      <kernel IPI> : Rescheduling interrupts 
  18.3% ( 14.1)       <interrupt> : iwl3945 
  12.8% (  9.8)       <interrupt> : extra timer interrupt 
   6.6% (  5.0)       compiz.real : schedule_timeout (process_timeout) 
   2.6% (  2.0)   multiload-apple : schedule_timeout (process_timeout) 
   2.2% (  1.7)    gnome-terminal : schedule_timeout (process_timeout) 
   2.0% (  1.5)    wpa_supplicant : schedule_timeout (process_timeout) 
   1.6% (  1.2)           firefox : futex_wait (hrtimer_wakeup) 
   1.4% (  1.1)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer)
   ....... 

```

---

### Post by atlas95 on 2008-07-16
I redo a kernel with kernelcheck for test this :D
edit: I can't get working nvidia 173 and uvcvideo hang hal at boot.:(

---

### Post by bubbalouie on 2008-07-23
I thought this may help some people:

sudo apt-get install irqbalance

It's more or less a compliment to the power saving scheduler that is already being invoked, more info at:

[http://irqbalance.org/](http://irqbalance.org/)

I haven't got any measurable results on using this, however, if someone has a way to quantify the effect of running the daemon it'd be interesting to see what they find.

Cheers

Ryan :)

---

### Post by sdennie on 2008-07-23
> **bubbalouie said:**
> I thought this may help some people:

sudo apt-get install irqbalance

It's more or less a compliment to the power saving scheduler that is already being invoked, more info at:

[http://irqbalance.org/](http://irqbalance.org/)


I'll have a look and, if it doesn't cause any problems, add it as a possible thing to try in the first post.

> 
I haven't got any measurable results on using this, however, if someone has a way to quantify the effect of running the daemon it'd be interesting to see what they find.


Yes, it's very difficult to measure power savings features when they don't make a difference during idle time (for example, underclocking the PowerMizer level 2 frequency).  It sounds like this could possibly lower the Kernel IPI wakeups so, at the very least it might make for more pleasing powertop displays.  :)

---

### Post by atlas95 on 2008-07-24
We only need to install irqbalance? no settings? we keep also other power daemon?
Thanks for your contrib!

---

### Post by bubbalouie on 2008-07-24
No config so far as I can tell, the daemon seems to be running (you can see it in your process list), however, as before, measuring the effect may not be so simple, the best I can think of is to give your hardware a work out (network traffic, and HID interrupts perhaps) and watch what happens in htop or powertop. Then repeat when on battery and see if the load is being distributed differently. I haven't had time for this though sorry, also I am not certain this is a good way to measure the effect, timed battery tests over several trips would probably reveal 'more' (I've found I get more than 6 hours at the moment, about 5-5.5 when I copy a mass of data [just over 90gb I seem to recall] from my laptop over scp using Ethernet in my max power save mode.... the network was kinda busy so it took a while, also no HPN on lappy).

As a side note (VERY off topic), if you want to improve SCP performance (or sftp for that matter), HPN-SSH is quite good, details below:
> 
Info partly from:

[http://www.psc.edu/networking/projects/hpn-ssh/](http://www.psc.edu/networking/projects/hpn-ssh/)

To build HPN-SSH:

wget [http://ftp.bit.nl/mirror/openssh/openssh-5.0p1.tar.gz](http://ftp.bit.nl/mirror/openssh/openssh-5.0p1.tar.gz)
tar -xvvf openssh-5.0p1.tar.gz
cd openssh-5.0p1/
wget [http://www.psc.edu/networking/projects/hpn-ssh/openssh-5.0p1-hpn13v3.diff.gz](http://www.psc.edu/networking/projects/hpn-ssh/openssh-5.0p1-hpn13v3.diff.gz)
zcat openssh-5.0p1-hpn13v3.diff.gz | patch
./configure
make
sudo make install

To tweak your networking:

#from /etc/sysctl.conf
# optimization start
# increase TCP max buffer size setable using setsockopt()
net.ipv4.tcp_rmem = 4096 87380 8388608
net.ipv4.tcp_wmem = 4096 87380 8388608
# increase Linux auto tuning TCP buffer limits
# min, default, and max number of bytes to use
# set max to at least 4MB, or higher if you use very high BDP paths
net.core.rmem_max = 8388608
net.core.wmem_max = 8388608
net.core.netdev_max_backlog = 5000
net.ipv4.tcp_window_scaling = 1
# optimization end

---

### Post by atlas95 on 2008-07-24
Thanks for this tweak!

---

### Post by sdennie on 2008-07-25
> **bubbalouie said:**
> No config so far as I can tell, the daemon seems to be running (you can see it in your process list), however, as before, measuring the effect may not be so simple, the best I can think of is to give your hardware a work out (network traffic, and HID interrupts perhaps) and watch what happens in htop or powertop. Then repeat when on battery and see if the load is being distributed differently.


I've installed it and will try to devise some tests to see if it helps with power savings at all.

> 
I've found I get more than 6 hours at the moment, about 5-5.5 when I copy a mass of data

I'm glad to hear you say this as I get close to 7 under normal usage as well (IRC/IM/Web at 50% backlight) so I'm glad other people are able to get similar results even with different methods.  

Out of curiosity, have you compared the battery life to that of Vista?  This machine came with Vista but I jammed an Ubuntu CD into the drive the first time I started it and erased the entire disk to install Ubuntu so I can't directly compare battery times.  However, looking at reviews online, it seems like after a bit of tweaking, the Ubuntu battery life is significantly better than the Vista battery life.

---

### Post by bubbalouie on 2008-07-25
No testing with Vista I am afraid, I made an image of the HDD and put Kubuntu on it right away (frankly Windows feels a little crippled).... However, I suspect that an unconfigured M1330 + Ubuntu actually gets worse battery life than Vista (from having read a few posts anyway). With the tweaking though, the gains are such that we do indeed seem to get better battery life (hopefully the next kernel will see further improvements), sadly I think this kind of messing about is outside of the average users capabilities, perhaps it'd be nice if there was a single M1330 power tweaker to help with this.

I have considered writing a python tool that lets users pick what to do in a simple way (an applet menu style program with a few config dialogs perhaps), I'd load it with a few predefined 'auto profiles' which detect system devices and determine a few different saver states the user could pick from. I expect this kind of task would be fairly simple, although it'd probably require a full week of coding (especially given it's a while since I've done any Python GUI stuff), and I seem to have trouble finding quality time to spend with family & friends, much less writing software out of work... I do not see any reason why this couldn't work though, really speaking it's just an extension of the powertop ideas... Perhaps in a few months I will revisit the idea and try and make something of it (the upshot here is I might be able to figure out a way to better the security, running a root service which handles the auto profiles that are requested by a user level app sounds ok, but I think it could be better)..

Cheers

Ryan

---

### Post by atlas95 on 2008-07-25
An applet will be wonderfull ! I would like to help you ! Thanks for your futur job !

---

### Post by treris on 2008-07-25
An applet sounds just about brilliant!! I've gotten myself a 1330 just about a week ago and would love to be able to get it to maximize its battery the extremely easy way. 

I know, I know, I'm a lazy bum, getting the scripts into place isn't hard to do either, but an applet would make it all seem so much more smooth (for lack of a better word).

I hope you find the time to write it, afraid I can't help much since I'm up to my ears in work and a master's thesis.

regards

---

### Post by sdennie on 2008-07-25
> **bubbalouie said:**
> However, I suspect that an unconfigured M1330 + Ubuntu actually gets worse battery life than Vista (from having read a few posts anyway).


Yes, by default none of the myriad of linux power savings features are enabled by default so, a Vista install tuned by the vendor is almost certainly better on battery life by default.

> 
hopefully the next kernel will see further improvements


It does.  I'm running a 2.6.26 kernel at the moment and the PCI-Express power savings makes a big difference.  It by itself saves around .7W of power but, it seems to have tipped the scale to the point where the heat is so low in the machine now that the fan spends a lot of time turned off (which further improves power savings).  Hopefully the Intrepid kernel has this feature enabled.

> 
I have considered writing a python tool that lets users pick what to do in a simple way (an applet menu style program with a few config dialogs perhaps)

I've actually started something like this as well (though, in perl) but I haven't had time to get very far with it.

---

### Post by motin on 2008-07-27
> **bubbalouie said:**
> I have considered writing a python tool that lets users pick what to do in a simple way (an applet menu style program with a few config dialogs perhaps), I'd load it with a few predefined 'auto profiles' which detect system devices and determine a few different saver states the user could pick from. I expect this kind of task would be fairly simple, although it'd probably require a full week of coding (especially given it's a while since I've done any Python GUI stuff), and I seem to have trouble finding quality time to spend with family & friends, much less writing software out of work... I do not see any reason why this couldn't work though, really speaking it's just an extension of the powertop ideas... Perhaps in a few months I will revisit the idea and try and make something of it (the upshot here is I might be able to figure out a way to better the security, running a root service which handles the auto profiles that are requested by a user level app sounds ok, but I think it could be better)..

Cheers

Ryan

> **atlas95 said:**
> An applet will be wonderfull ! I would like to help you ! Thanks for your future job !

> **treris said:**
> An applet sounds just about brilliant!! I've gotten myself a 1330 just about a week ago and would love to be able to get it to maximize its battery the extremely easy way. 

I know, I know, I'm a lazy bum, getting the scripts into place isn't hard to do either, but an applet would make it all seem so much more smooth (for lack of a better word).

I hope you find the time to write it, afraid I can't help much since I'm up to my ears in work and a master's thesis.

regards

> **vor said:**
> I've actually started something like this as well (though, in perl) but I haven't had time to get very far with it.

I was going to suggest that we take our five scripts found in this thread and combine them to a one-script-to-rule-them-all kind of script, but doing this in an even more usable way sounds even better!

I guess what we would be talking about is practically:
A. a front-end to laptop mode tools where we could control the tweaks offered by laptop-mode
B. A set of scripts for /etc/pm/ holding one tweak in each script
C. A Bootup-Manager like interface to the scripts, where we can read about the different tweaks, see and change which ones are running / available but not running etc.

Would it be possible to make a branch of bootupmanager and start from there you think?

---

### Post by motin on 2008-07-27
> **motin said:**
> Would it be possible to make a branch of bootupmanager and start from there you think?

Actually, looking at the source, this seems rather feasable. Bum is written in perl, there is not very much source code, everything seems structured and the interface is written i glade. 

I have never programmed in perl, but might be able to make some hacks so that the scripts in /etc/pm/power.d/ are displayed instead of /etc/rc or /etc/init.d/ but then I think I would run into problems making it all in all a stable and safe tool (running noob perl code under sudo is baaaad idea... :))

What would be call this new application/applet/package? powertweak is already taken... Maybe psm for power savings manager? Powertools? Wattcontrol? Watthunter? Hmm I like watthunter... What do you think?

In the extension we could keep a database with compatibility information (this script has been only been tested on the XPS M1330 - this script is not compatible with IBM Thinkpads, a certain hardware found on the system etc.) so that only the tested tweaks would be available to activate (without running the app with --list-untested or similar).

@vor: You started writing something i perl - would you mind sharing what you have done so far?

---

### Post by sdennie on 2008-07-27
```

svn checkout https://gpower.googlecode.com/svn/trunk gpower

```

I haven't had the chance to work on it in many months and so it basically consists of a very basic framework that I planed to build into a GUI that builds itself based on available features.  It only represents one night of coding so, there isn't much there.

---

### Post by motin on 2008-07-27
> **vor said:**
> ```

svn checkout https://gpower.googlecode.com/svn/trunk gpower

```

I haven't had the chance to work on it in many months and so it basically consists of a very basic framework that I planed to build into a GUI that builds itself based on available features.  It only represents one night of coding so, there isn't much there.

Aha nice - but I couldn't check the code out manually and logging in with my google credentials didn't help. Never used Google Code... Mind sharing what's needed for read (and maybe even write) access?

Thanks!

---

### Post by sdennie on 2008-07-27
> **motin said:**
> Aha nice - but I couldn't check the code out manually and logging in with my google credentials didn't help. Never used Google Code... Mind sharing what's needed for read (and maybe even write) access?

Thanks!

This page has download instructions that should work: [http://code.google.com/p/gpower/source/checkout](http://code.google.com/p/gpower/source/checkout)

---

### Post by bubbalouie on 2008-07-28
I was thinking more of a separation between the different parts of the system. A sort of client->service type arrangement. 

Have a service that can interpret profile files. The service runs as root (launched at boot and terminated at shutdown like any other service) and can be asked to invoke different profiles at run time by the user. Unfortunately communication between the client and service is a tricky subject for me, I keep coming back to using a socket that only accepts connections from localhost, though I imagine Linux would surely have a better mechanism than this (My coding has mostly been for embedded gadgets, or for web servers I'm afraid, so Perl, C, Java-script & a smidgen of Python are mostly what I've been using over the last 12 months).

The client is able to also read the profiles, and then let users determine which profile to use at any given time, maybe even some additional support for determining when to launch profiles would be handy (i.e. on battery launch profile 4, when a certain app [CAD application or K3B for example] is running invoke profile 6, or enable DVD polling for 30 seconds).

By using profiles we could build a framework that allows users to configure profiles for different laptops and submit them to the project (is there a way to determine what type of laptop a user has?), thus providing good support for many laptop types. We already know what is needed for exceptional M1330 performance, however on a VAIO for example USB can not be unloaded as it would kill the touch pad, also some devices have different names etc.

Additionally by creating a simple to control service, it should be possible to allow people to write different front ends (things like QT, GTK, Tk, Python, Perl etc become irrelevant).

Funnily though, I think the client side would be the most complicated part of the system, also deciding on a suitable set of protocols and formats could be tricky... However, a tool that allows this all in a simple user friendly fashion is exactly what Linux is missing at the moment, I know it would have saved me a great deal of time trying to figure out how to reduce power usage.

Thinking about it, a profile could be a script (Bash script) that has some additional markup in the comments for the client and service components to parse, it could accept standard set of parameters. The service would then only need to be able to run the scripts to determine or change the condition of a system (obviously it should make certain only root can write to the profile before running it, as a security measure), this would keep the service very simple and move the heavy lifting to the client app and some handy scripts. This would hopefully allow people to adapt scripts that they have already written to these tools (many people have their own variants of the power saving scripts we use for a myriad of different laptops).

I might get a start on figuring out a more detailed architecture tonight and come back with what I have if people are interested in this approach. I don't think however that I'll be able to write the whole thing by myself too quickly (mostly due to the client front end and the possible need for some tricky UI work), so again, if anyone is interested, and is keen on helping (and hopefully knows more than me :S ) please sing out.

Cheers

Ryan

**EDIT: I have decided to try and write this in Python (mostly so I can brush up on it a bit), I will try create a basic server & client which can launch a variant of my power saving script. Stage one will be a simple arrangement that provides a non configurable interface for users to change settings without needing to contstantly enter a password. Once I have it ready I'll be sure to share. *IF* I can make it work well I'll look at starting a proper project for it. I am sure that with the help of you guys it'd be possible to make a go of it, winter here looks like it's going to hang around for a while so I've got a bit of time to burn I guess.*

---

### Post by sdennie on 2008-07-28
> **bubbalouie said:**
> I was thinking more of a separation between the different parts of the system. A sort of client->service type arrangement.

That's an interesting idea.  I don't have time to flesh out the software I began to write but, if you start a project and publicly host it, let me know and I'll be happy to contribute to it or help out any way I can.

---

### Post by atlas95 on 2008-07-28
I will contribute too with my little knowledge !

---

### Post by sdennie on 2008-07-29
Just tonight I figured out how to make the disk stay in standby mode for arbitrary amounts of time.  It's difficult to setup, potentially dangerous and not something I recommend so, I will not give explicit instructions on how to do this but instead give the general idea and those that understand can implement it:

1) Mount various non-essential parts of the system as tmpfs.  This idea came from: [http://www.ubuntu-eee.com/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive](http://www.ubuntu-eee.com/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive) and is probably not dangerous.

2) Mount both ~/.mozilla and ~/.purple as tmpfs and then write a cron job to back them up to disk every 10 minutes or so.  You will then need to write init scripts to restore your backup at boot time (and permissions) and one to save it at shutdown time (and at suspend/hibernate time for safety).

These are not sane things to do but, if you understand the ramifications and get stuck somewhere in the implementation, I am willing to help via PM.  These are not changes I recommend for most users so don't try them at home...

---

### Post by bubbalouie on 2008-08-01
I am not sure how many people have NOT seen this:

[http://www.theinquirer.net/gb/inquirer/news/2008/07/09/nvidia-g84-g86-bad](http://www.theinquirer.net/gb/inquirer/news/2008/07/09/nvidia-g84-g86-bad)

But I thought I'd share anyway, maybe someone has some thoughts, sadly this includes us, I guess not using the 3D hardware may help, but this really bites, if it affects ALL M1330 nvidia laptops :(

Makes me wish I had an X3100 model....

---

### Post by linux_tech on 2008-08-01
Dell laptops usually have bios settings that can be changed 
to conserve power or use more power. They are usually under power-> power management. They allow you to select from three or four different power management timeout strategies, for example:

    * Maximum Battery Life — conserves the greatest amount of system power; sets Video Timeout, Hard Disk Timeout, and Auto Suspend Timeout to 2 minutes each.

    * Maximum Performance — conserves power but allows better system performance; sets Video Timeout to 10 minutes, Hard Disk Timeout to 5 minutes, and Auto Suspend Timeout to 10 minutes.

    * Customized (the default) — allows you to set each timeout as desired.

---

### Post by glantucan on 2008-08-04
Hi all

I'm using an ASUS X20SGseries laptop with:
Intel Core Duo T8100
12'' WXGA
3Gb RAM
802.11abgn + BT (using iwl4965 driver)

When I try 
```
sudo echo 5 > /sys/bus/pci/drivers/iwl4965/0000\:05\:00.0/power_level
```

it says 
```
bash: power_level: access denied
```
](*,)
If I ```
 sudo less /sys/bus/pci/drivers/iwl4965/0000\:05\:00.0/power_level
```
Then the following is shown
```
6 (AC) OFF
^@
power_level (END) 

```
So full power is still used, no matter what I do.
For now, as I don't use the wireless very much, I changed the corresponding line in my script to ```
rmmod iwl4965
```, but I would like to be able to connect to public wireless access points when I travel.
I know this thread is for Del computers but I don't see any other thread where to ask this.

Any help will be appreciated
Glantucan

---

### Post by sdennie on 2008-08-04
Try: 

```

sudo sh -c "echo 5 > /sys/bus/pci/drivers/iwl4965/0000\:05\:00.0/power_level"

```

---

### Post by igotnoluck on 2008-08-04
Can is run the 99-saving script on a LG e200 machine (it has an AMD graphic
card , but i don't see any thing regarding the Nvidia Card )

also, do i need to run this script each time i run my computer ?
does the setting get reset ?

thanks,
igotnoluckC1

---

### Post by glantucan on 2008-08-04
> **vor said:**
> Try: 

```

sudo sh -c "echo 5 > /sys/bus/pci/drivers/iwl4965/0000\:05\:00.0/power_level"

```

In my ignorance I don't understand why this is necessary but it worked like a charm. Thanks a lot.

I still have some more questions but they'll have to wait till I come back from my holidays. 
Pretty interesting all this thing. It kept me awake the whole night.

Cheers!

Glantucan

---

### Post by glantucan on 2008-08-04
> **igotnoluck said:**
> Can is run the 99-saving script on a LG e200 machine (it has an AMD graphic
card , but i don't see any thing regarding the Nvidia Card )


I don't see any reason not to test it. I did it with my ASUS and it works nicely. 
I need to tune it a little for my needs. Maybe using gconftool to change gnome settings to use less power (removing animations, screensaver..., changing default apps, etc,)

If you have a nvidia card you can use the second script. If not, better skip it.

> also, do i need to run this script each time i run my computer ?
does the setting get reset ?
You don't need to execute the script after you install it to /etc/pm/sleep.d and 
/etc/pm/power.d. 
The script will be run automatically every time you connect or disconnect the laptop to AC power. The script will detect which of this actions was performed and change settings properly.

Hey, thanks again, Vor :D

Glantucan

---

### Post by glantucan on 2008-08-04
By the way,

What services do you need to be running for this script to work:

laptop-mode (I guess this one is necessary), apmd, acpid, acpi-support, powernowd, ...?

In principle apmd can be deactivated in favor of acpid, right?

Glantucan

---

### Post by sdennie on 2008-08-05
> **igotnoluck said:**
> Can is run the 99-saving script on a LG e200 machine (it has an AMD graphic
card , but i don't see any thing regarding the Nvidia Card )


The same principles apply to all machines.  Some of the options may not be valid depending on your hardware though.

> **glantucan said:**
> In my ignorance I don't understand why this is necessary but it worked like a charm. Thanks a lot.


From: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Redirecting the output of commands run with sudo requires a different approach. For instance consider sudo ls > /root/somefile will not work since it is the shell that tries to write to that file. You can use ls | sudo tee -a /root/somefile to append, or ls | sudo tee /root/somefile to overwrite contents. You could also pass the whole command to a shell process run under sudo to have the file written to with root permissions, such as sudo bash -c "ls > /root/somefile". 

> **glantucan said:**
> 
What services do you need to be running for this script to work:

laptop-mode (I guess this one is necessary), apmd, acpid, acpi-support, powernowd, ...?


Probably just acpid.  Laptop-mode is something completely different and acpi-support is the old (pre-Hardy) way of doing things.  acpi-support may or may not still be needed because it's replacement (pm-utils) doesn't seem to be a full replacement.  So, to answer your question, you need whatever it takes to make pm-utils work properly.  Hope that help.s

---

### Post by Crowchild on 2008-08-05
I am hoping someone can walk me through a bit of this. I have tried the howto above and am still seeing pretty bad power usage. This is what I get with the acpi & powertop -d -t 60 commands:
> 

adam@dell-desktop:~$ acpi
     Battery 1: discharging, 21%, 00:35:38 remaining

adam@dell-desktop:~$  sudo powertop -d -t 60
PowerTOP 1.9    (C) 2007 Intel Corporation 

Collecting data for 60 seconds 
Cn	          Avg residency
C0 (cpu running)        (11.8%)
C1		  0.0ms ( 0.0%)
C2		  0.1ms ( 0.3%)
C3		  1.9ms (88.0%)
P-states (frequencies)
Wakeups-from-idle per second : 482.5	interval: 60.0s
Power usage (ACPI estimate): 16.1W (0.6 hours) 
Top causes for wakeups:
  45.3% (302.1)      <kernel IPI> : Rescheduling interrupts 
  13.3% ( 88.6)           firefox : schedule_timeout (process_timeout) 
  12.8% ( 85.4)       <interrupt> : extra timer interrupt 
  10.7% ( 71.4)           firefox : futex_wait (hrtimer_wakeup) 
   7.0% ( 46.9)       <interrupt> : uhci_hcd:usb2, uhci_hcd:usb4, HDA Intel 
   3.2% ( 21.1)       <interrupt> : iwl3945 
   1.7% ( 11.1)   gnome-power-man : schedule_timeout (process_timeout) 
   1.5% ( 10.1)       compiz.real : schedule_timeout (process_timeout) 
   0.6% (  4.0)   <kernel module> : usb_hcd_poll_rh_status (rh_timer_func) 
   0.6% (  4.0)    scim-panel-gtk : schedule_timeout (process_timeout) 
   0.5% (  3.6)            deluge : schedule_timeout (process_timeout) 
   0.3% (  2.1)           emerald : schedule_timeout (process_timeout) 
   0.3% (  2.0)       <interrupt> : nvidia 
   0.3% (  1.8)    gnome-terminal : schedule_timeout (process_timeout) 
   0.2% (  1.6)    wpa_supplicant : schedule_timeout (process_timeout) 
   0.2% (  1.2)        pulseaudio : schedule_timeout (process_timeout) 
   0.2% (  1.1)         nm-applet : schedule_timeout (process_timeout) 
   0.2% (  1.0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer) 
   0.2% (  1.0)    NetworkManager : tg3_open (tg3_timer) 
   0.2% (  1.0)            dhcdbd : schedule_timeout (process_timeout) 
   0.1% (  0.9)    NetworkManager : schedule_timeout (process_timeout) 
   0.1% (  0.7)   hald-addon-stor : schedule_timeout (process_timeout) 
   0.1% (  0.6)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0.1% (  0.5)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0.1% (  0.5)           iwl3945 : ieee80211_sta_work (ieee80211_sta_timer) 
   0.1% (  0.4)       gnome-panel : schedule_timeout (process_timeout) 
   0.0% (  0.2)   update-notifier : schedule_timeout (process_timeout) 
   0.0% (  0.2)          nautilus : schedule_timeout (process_timeout) 
   0.0% (  0.2)             udevd : rs_tx_status (iwl_bg_rate_scale_flush) 
   0.0% (  0.1)           preload : schedule_timeout (process_timeout) 
   0.0% (  0.1)      <kernel IPI> : TLB shootdowns 
   0.0% (  0.1)              Xorg : do_setitimer (it_real_fn) 
   0.0% (  0.1)         iwl3945/1 : sta_info_start (sta_info_cleanup) 
   0.0% (  0.1)              nmbd : schedule_timeout (process_timeout) 
   0.0% (  0.1)     <kernel core> : neigh_update (neigh_timer_handler) 
   0.0% (  0.1)   gnome-volume-ma : schedule_timeout (process_timeout) 
   0.0% (  0.1)              hald : schedule_timeout (process_timeout) 
   0.0% (  0.1)              smbd : schedule_timeout (process_timeout) 
   0.0% (  0.1)          gconfd-2 : schedule_timeout (process_timeout) 
   0.0% (  0.1)                ip : __dst_free (delayed_work_timer_fn) 
   0.0% (  0.0)              Xorg : schedule_timeout (process_timeout) 
   0.0% (  0.0)     <kernel core> : ip_rt_init (delayed_work_timer_fn) 
   0.0% (  0.0)     <kernel core> : inet_init (inet_frag_secret_rebuild) 
   0.0% (  0.0)     <kernel core> : flow_cache_init (flow_cache_new_hashrnd) 
   0.0% (  0.0)     <kernel core> : rif_init (rif_check_expire) 
   0.0% (  0.0)     <kernel core> : seqgen_init (delayed_work_timer_fn) 
   0.0% (  0.0)              cron : do_nanosleep (hrtimer_wakeup) 
   0.0% (  0.0)         iwl3945/1 : iwl_bg_alive_start (delayed_work_timer_fn) 

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Disable 'hal' from polling your cdrom with:  
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.



---

### Post by sdennie on 2008-08-05
> **Crowchild said:**
> I am hoping someone can walk me through a bit of this. I have tried the howto above and am still seeing pretty bad power usage. This is what I get with the acpi & powertop -d -t 60 commands:

My remote diagnosis (so, not accurate) is that you have 1 or more AJAX applications open in firefox (gmail, google reader, etc...) and music playing (or, at the very least a music playing application open).  That's all I can tell from the powertop output.  The fact that the C0 state is at 11% means that something else is running in the background.  I'd run "powertop" in one terminal and "top" in another to see what is causing such high CPU usage while idle.

---

### Post by Crowchild on 2008-08-06
> **vor said:**
> My remote diagnosis (so, not accurate) is that you have 1 or more AJAX applications open in firefox (gmail, google reader, etc...) and music playing (or, at the very least a music playing application open).  That's all I can tell from the powertop output.  The fact that the C0 state is at 11% means that something else is running in the background.  I'd run "powertop" in one terminal and "top" in another to see what is causing such high CPU usage while idle.


I am not really sure what I am looking for in powertop and top when they are run in unison.

I did manage to get a much better result by closing the gmail tab in firefox and removing gnome-power-manager. Now I am down to a more acceptable:
> 
Wakeups-from-idle per second : 133.8	interval: 60.0s

Power usage (ACPI estimate): 13.9W (2.2 hours) 



 Yet, I am still seeing:

> 

Top causes for wakeups:
  **37.2% ( 60.3)      <kernel IPI> : Rescheduling interrupts **
  11.2% ( 18.2)           firefox : futex_wait (hrtimer_wakeup) 
  ** 9.2% ( 15.0)       <interrupt> : extra timer interrupt **


Is this there any help for this or is it just a matter of waiting for the new kernel as was mentioned earlier in the thread?

---

### Post by sdennie on 2008-08-06
> **Crowchild said:**
> 
 Yet, I am still seeing:

...Some powertop output...

Is this there any help for this or is it just a matter of waiting for the new kernel as was mentioned earlier in the thread?

Those numbers seem reasonable to me.  It seems like the scripts are running but, you may want to double check that everything is working.  For example, if you connect to a wireless network while on battery, it resets the power savings state of the wireless card (About 1W of power lost by not resetting the powersavings state).

As for the kernel upgrade, it's actually very trivial to download the Ubuntu kernel source and patch it with ASPM support and rebuild it.  I'm actually running the equivalent of 2.6.24-19-generic but with PAE and ASPM support.  It's by far the best kernel I've used for this machine (After 2.6.24, the nvidia drivers are not very good for compiz).

---

### Post by peterquistgard on 2008-08-11
Hi Vor,

I'm about to try out your scripts on my M1330. I just want to make sure I can put everything back the way it was if I don't like it. How could I revert to my old settings after installing 99*.sh ?

I do a lot of heavy number crunching [parallel c code, dual cores are handy for testing :) ]. Do you think I would notice any performance drop?

Thanks,

Seán

---

### Post by sdennie on 2008-08-11
> **peterquistgard said:**
> Hi Vor,

I'm about to try out your scripts on my M1330. I just want to make sure I can put everything back the way it was if I don't like it. How could I revert to my old settings after installing 99*.sh ?


It's simply a matter of deleting the files you've installed:

```

sudo rm /etc/pm/*/99-savings /etc/pm/*/99-nvidia

```

> 
I do a lot of heavy number crunching [parallel c code, dual cores are handy for testing :) ]. Do you think I would notice any performance drop?


On AC power you shouldn't notice any drop in performance and, as long as you maintain the cpu scaling governor at "ondemand", the only performance decrease you should see on battery is if you aggressively set the disks to spin down but your code ends up doing a lot of non-cached disk reads (which will cause the thread in question to busy wait for the disks to spinup and the data to be read).

If you do notice a difference on battery power, it's fairly easy to take the script and turn it into a "go_fast.sh" script that turns off all the power savings features regardless of whether you are on_ac_power or not.  Then you could just run it manually to bring the machine to full power when you don't want power savings on while on battery.

---

### Post by glantucan on 2008-08-12
> **vor said:**
> The same principles apply to all machines.  Some of the options may not be valid depending on your hardware though.



From: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Redirecting the output of commands run with sudo requires a different approach. For instance consider sudo ls > /root/somefile will not work since it is the shell that tries to write to that file. You can use ls | sudo tee -a /root/somefile to append, or ls | sudo tee /root/somefile to overwrite contents. You could also pass the whole command to a shell process run under sudo to have the file written to with root permissions, such as sudo bash -c "ls > /root/somefile". 



Probably just acpid.  Laptop-mode is something completely different and acpi-support is the old (pre-Hardy) way of doing things.  acpi-support may or may not still be needed because it's replacement (pm-utils) doesn't seem to be a full replacement.  So, to answer your question, you need whatever it takes to make pm-utils work properly.  Hope that help.s

Thanks man. Now I understand.

I've uninstalled:
acpi-support
powermanagement-interface
apmd
laptop-mode-tools
powernowd

and now testing. I'll post any issues.

---

### Post by glantucan on 2008-08-14
**[SIZE="3"]Services test[/SIZE]**
I thought it would be interesting for us all to know which services are needed for vor's script to work properly. 
On the other hand, as power consumption is higher when more services are active, we'd want to keep as less services running as possible.

For the sake of completeness I include my specs:
[I]ASUS X20SG
Duo T8100
3GB RAM
nVIDIA 9300M G
Wireless 802.11abgn + BlueTooth
12" WXGA

Running ubuntu studio hardy, kernel 2.6.24-19-generic[/I]

And this the script I'm using:
```
#!/bin/bash
# Install: 
# 
# Go fast on AC power.  Similar to default Ubuntu settings

# Optional: Remove the most of the bluetooth/usb subsystem
  hciconfig hci0 down
  modprobe -r hci_usb
  modprobe -r rfcomm
  modprobe -r l2cap
  modprobe -r bluetooth

if on_ac_power; then
  # Set the drive to mostly stay awake
  hdparm -B 200 -S 240 -M 254 /dev/sda

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  mount -o remount,commit=60 /
 

  # Turn off the laptop mode disk optimization
  echo 0 > /proc/sys/vm/laptop_mode

  # NOT WORKING. Loading iwl4965 in case it was unloaded when on battery.
  # Manually set the wifi driver to no power savings.
  #echo 6 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  
  #modprobe iwl4965
sh -c "echo 6 > /sys/bus/pci/drivers/iwl4965/0000\:??\:00.0/power_level"
  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Only wakeup every 60 seconds to see if we need to write dirty pages
  # By default this is every 5 seconds but, I prefer 60 to reduce disk
  # activity.
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs

  # Turn off sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  
  # Set the SATA to max performance
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Enable the webcam driver
  modprobe uvcvideo

else # Save power

  # Set the disks to aggressively save power and use the lowest acoustic
  # level.  Note: Currently Firefox is very poorly behaved and some
  # might find these settings too aggressive.  If so, change "-S 4" to
  # something larger like -S 24 (two minutes).
  echo "Set the disks to aggressively save power"
  hdparm -B 1 -S 4 -M 128 /dev/sda
  
  # Change the ext3 commit times to 10 minutes.  This reduces disk
  # activity
  echo
  echo "Change the ext3 commit times to 10 minutes"
  mount -o remount,commit=600 /

  # Set laptop disk write mode
  echo
  echo "Set laptop disk write mode"
  echo 5 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945 driver to power savings.
  # ATTENTION!!! This seems not to be working (acces denied) unloading module
  #echo
  #echo "Manually set the iwl3945 driver to power savings"
  #echo 5 > /sys/bus/pci/drivers/iwl4965/0000\:??\:00.0/power_level  
  
sh -c "echo 5 > /sys/bus/pci/drivers/iwl4965/0000\:??\:00.0/power_level"
  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo
  echo "Reduce disk activity by waiting up to 10 minutes before doing writes"
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Set sound card power savings
  echo 
  echo "Set sound card power savings"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  # Set SATA to minimum power
  echo
  echo "Set SATA to minimum power"
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
  
  # Disable hal polling for /dev/cdrom
  hal-disable-polling --device /dev/cdrom

  # Make sure ondemand governor is set
  echo
  echo "Set ondemand governor"
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Remove the webcam driver
  echo
  echo "force remove of webcam driver"
  modprobe -r uvcvideo --force
  
  # Kill gnome screesnsaver
  killall gnome-screensaver

fi
```
I'll update this post as more tests are run.

**Start**
Well, I did deactivate:
acpi-support, powermanagement-interface, apmd, laptop-mode-tools,	powernowd, gnome-power-management

And some weird things happened:
[LIST=1]
[*]laptop hotkeys did not work anymore
[*]when logging out of gnome, the logout panel took out an eternity to show up (more than 1 minute, sometimes)
[*]_the script stopped working**!!!**_
[/LIST]

After some googling and tests on a desktop computer I'm trying to optimize for performance I came out to this guesses/conclusions (respectively)
[LIST=1]
[*]This because of acpi-support is disabled
[*]This happens when gnome-power-manager is deactivated. Giant bugs eat me if I know why (see [Gnome hangs on 'quit' button]("http://ubuntuforums.org/showthread.php?t=774977")).
[*]Again because of acpi-support.
[/LIST]

After activating those two services I got almost any hotkeys working, the script running (thought some tuning and understanding is still on my part) and the logout delay gone.

By the way gnome-power-manager activated some hotkeys that still didn't work even with acpid-support running. I think this may not be very important, but I wanted to control LCD brightness. If this is not your case you can run this script to logout: [http://ubuntuforums.org/showpost.php?p=5577318&postcount=14](http://ubuntuforums.org/showpost.php?p=5577318&postcount=14)

**Things still bothering me**
On battery, Bluetooth light is still on. Don't know if leaking much energy.
Any ideas?

Powertop still advice me to:
```
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
```
```
hal-disable-polling --device /dev/cdrom
```
([COLOR="Orange"]UPDATED August 14th[/COLOR]) but as vor says bellow it's probably a powertop bug


**Other things to be tested**([COLOR="Orange"]UPDATED August 14th[/COLOR] Two items erased. Not really related with power management)
[LIST=1]
[*]Disable trackerd when on batteries. ¿Would this allow *tracker-search* the database?. This will probably avoid spin-ups
[*]Disable *search for new hardware*. You don't change laptop hardware so often. TESTING, Nothing weird happened in one day. usb devices get detected as usual. Don know about PCMCIA or other expansion cards.
[*] I have, for some reason, battery-stats installed and active. Is this necessary for anything?
[*] I have the bad habit to place o lot of monitoring applets on my gnome panel. Find the way to disable them when in battery mode.
[*] Disable gnome-update-manager in battery mode. Who would update when on battery? (probably a stupid question)

[*] Use gconftool to change/read GNOME configuration entries. Like ```
gconftool -s /apps/gnome-screensaver/idle_activation_enabled --type=boolean 0
```Do these things happen instantaneously? 
[*] Don't create thumbs in nautilus in battery mode


[*] Make your own suggestions :D And forgive my English 
[/LIST]

To be continued...
Glantucan

---

### Post by sdennie on 2008-08-14
It's not terribly surprising that acpi-support is needed to make things work right.  Hardy has a baffling package called pm-utils that for some reason replaces some of the perfectly valid things in acpi-support but, doesn't provide all the functionality of acpi-support (nor remove the overlapping areas of acpi-support).  It's frustrating and annoying but, that's how it is.

As for powertop giving you those suggestions, I would ignore them.  It gives me the exact same two and both options are enabled (verified via checking on the command line).  It's a bug with powertop.

---

### Post by sdennie on 2008-08-14
> **glantucan said:**
> 
**Other things to be tested**
[LIST=1]
[*]Disable trackerd when on batteries. ¿Would this allow *tracker-search* the database?. This will probably avoid spin-ups
[*]Disable *search for new hardware*. You don't change laptop hardware so often. TESTING, Nothing weird happened in one day. usb devices get detected as usual. Don know about PCMCIA or ather expansion cards.
[*] I have, for some reason, battery-stats installed and active. Is this necessary for anything?
[*] I have the bad habit to place o lot of monitoring applets on my gnome panel. Find the way to disable them when in battery mode.
[*] Disable gnome-update-manager in battery mode. Who would update when on battery? (probably a stupid question)
[*] Disable cinestart. Again, I don't thing anybody will try to mount a film on batteries... Wait, cinestar run just once setting up just the locale and some configuration values... Hmmmm I don't know if I like that much this one```
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```. But this is off-topic.
[*] Use gconftool to change/read GNOME configuration entries. Like ```
gconftool -s /apps/gnome-screensaver/idle_activation_enabled --type=boolean 0
```Do these things happen instantaneously? 
[*] Don't create thumbs in nautilus in battery mode
[*] Disable apport service when on batteries

[*] Make your own suggestions :D And forgive my English 
[/LIST]

To be continued...
Glantucan

I responded before your had edited for your "Other things tested" so, I'll respond the best I can:

1-5) You could probably find a way to disable them on battery but, it's probably not needed.  What you really want to prevent are things that increase idle time power usage.  It may seem like you use your laptop a lot but, in reality, it's mostly idle.  If you can make it use less power while idle, the battery lasts a lot longer.  Preventing infrequent but potentially battery draining services from running probably won't help.

6) I don't know.

7) gconf changes happen almost instantaneously.

8) Not a bad idea and probably not hard via gconftool

9) I don't know what apport so, I'm not sure.

---

### Post by glantucan on 2008-08-14
> **vor said:**
> 1-5) You could probably find a way to disable them on battery but, it's probably not needed.  What you really want to prevent are things that increase idle time power usage.  It may seem like you use your laptop a lot but, in reality, it's mostly idle.  If you can make it use less power while idle, the battery lasts a lot longer.  Preventing infrequent but potentially battery draining services from running probably won't help.

Yes, but I put them there because I wonder if they make the hard disk to spin up, as trackerd reads a database and update it, monitoring applets read 'whatever' at fixed intervals that are usually short, and so on. . Maybe I'm wrong about that and all these programs are better thought than I would imagine. And you are right powertop never showed them as making the system to wake up.
> 6) I don't know.
Forget about it, it doesn't really matter as it only changes the amount of shared memory available for programs like cinelerra which use it a lot. I updated the post erasing this part.

> 

8) Not a bad idea and probably not hard via gconftool

It's good to know it :)

> 
9) I don't know what apport so, I'm not sure.

See [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport). Just my mistake, anyway. I get confused because I'm working on the performance of another computer at the same time, and I always try to run as less services as possible.

Just in case you missed it. Do you know how to check whether my bluetooth is doing something or not. It's supposed to be off when I turn off a switch, which is shared with wireless. The funny thing is that Wireless LED is off while bluetooth's one is not.
 
Hey, you really watch this thread :D

Thanks
Glantucan

---

### Post by sdennie on 2008-08-14
> **glantucan said:**
> Yes, but I put them there because I wonder if they make the hard disk to spin up, as trackerd reads a database and update it, monitoring applets read 'whatever' at fixed intervals that are usually short, and so on. . Maybe I'm wrong about that and all these programs are better thought than I would imagine. And you are right powertop never showed them as making the system to wake up.


Interesting.  I don't use things like trackerd (but, I do keep the locate daemon running) so, I'm not sure.  The only way that I'm aware of to determine if a program is waking up your disks is to be in a very quiet room where you can literally hear the disk spin up and down then, use the the /proc/sys/vm/block_dump command in my first post.  From there, you can often correlate the disk activity to the process that's causing it to wake up early.

Along those lines, if you really want to get extreme as far as disk spinups are concerned, there are various parts of the system that you can mount as tmpfs and write cron jobs to write them to disk every 10 minutes or so (or just let them die on reboot).  I have a post about it a few pages back and, mounting various parts of /var and all of ~/.mozilla and ~/.purple helps a lot.  With 4GB of RAM, after a day or two of uptime, the disk just wakes up every 10 minutes, writes to disk and then spins back down.

> 
Hey, you really watch this thread :D


I subscribe to it and really enjoy the things that have come out of it.  A number of interesting ideas have come out of the thread that I hadn't thought of and, though it's aimed at a specific laptop, the content of the entire thread is probably the best you'll find for a laptop user that wants to save power (outside of Intels fantastic site [www.lesswatts.org](www.lesswatts.org) which many of these tips are based on).  I'm glad that it has helped people and eagerly await more cool power savings tips.  ;)

---

### Post by patrickfromspain on 2008-08-17
I have a Fujitsu-Siemens Esprimo U9200 and most of these things work, however, the scsi_host link_power_management_policy won't change. I can do the echo min_power > stuff, but checking with cat will always return max_performance.

Any ideas?

Maybe my machine just isn't compatible with that stuff?

---

### Post by sdennie on 2008-08-19
> **patrickfromspain said:**
> I have a Fujitsu-Siemens Esprimo U9200 and most of these things work, however, the scsi_host link_power_management_policy won't change. I can do the echo min_power > stuff, but checking with cat will always return max_performance.

Any ideas?

Maybe my machine just isn't compatible with that stuff?

It's possible that it's just not supported.  On my machine, I have three hosts and min_power only "sticks" on one of them.  I'd make sure you are using the value on all the available hosts and then check to see if it works on at least one of them.

---

### Post by pranithkumar on 2008-08-20
does this take care of the hard drive bug in the bios?? i hear clicking sound on my laptop with these configs. The load cycle count keeps incrementing by 2-3 every minute, is that ok?

I removed this 99-savings to avoid the hard drive bug, but this doesnt seem to solve the problem. Now each time i login i have to manually do the hdparm -B 255 thingy, which is supposed to be bad. any idea on how to solve this??

---

### Post by sdennie on 2008-08-20
> **pranithkumar said:**
> does this take care of the hard drive bug in the bios?? i hear clicking sound on my laptop with these configs. The load cycle count keeps incrementing by 2-3 every minute, is that ok?

I removed this 99-savings to avoid the hard drive bug, but this doesnt seem to solve the problem. Now each time i login i have to manually do the hdparm -B 255 thingy, which is supposed to be bad. any idea on how to solve this??

The script I have in the original thread sets it so that Load_Cycle_Count only increments when on battery power and doesn't when on AC power.  Statistically, these should be safe settings because it's impossible to be on battery all the time.  I would use the settings for a month or two and, after that amount of time you can see how many Load_Cycle_Counts you are creating with your normal usage patterns and extrapolate that out to how long your disk is likely to last.  My guess is you'll find the number to be several years.

Note: To give that process a fair chance, make note of the Load_Cycle_Count and power on hours today and a month from now so you can properly estimate how long it will be before Load_Cycle_Count *might* become an issue for the disk with these settings.

---

### Post by the_softy on 2008-08-21
Hi, i'm to this forum. And i have a problem. I have made the script with some basic stuff. I gave everybody execute rights on the file. When i execute it normally ( ./99-save-power.sh ), it works. When i execute when on battery, the screen dims and all the rest works too. When on power cable, it works too.
 
But when I install it in sleep.d en power.d. Nothing happens when I go on battery. Not even the screen dims.

```
#!/bin/bash
if on_ac_power; then
# Reset back to normal settings
  sudo sh -c "echo 0 > /proc/sys/vm/laptop_mode"
  sudo sh -c "echo 10 > /proc/sys/vm/dirty_ratio"
  sudo sh -c "echo 5 > /proc/sys/vm/dirty_background_ratio"
  sudo sh -c "echo 500 > /proc/sys/vm/dirty_writeback_centisecs"
  sudo sh -c "echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy"
  
  sudo sh -c "xbacklight -set 100"

  sudo sh -c "ethtool -s eth0 wol g"		#enable wake up on lan
  sudo sh -c "ethtool -s eth0 autoneg on speed 1000"	 #set speed normaal, autoneg on
  echo "on power"

else
# Turn on aggressive power savings
  sudo sh -c "echo 5 > /proc/sys/vm/laptop_mode"
  sudo sh -c "echo 40 > /proc/sys/vm/dirty_ratio"
  sudo sh -c "echo 10 > /proc/sys/vm/dirty_background_ratio"
  sudo sh -c "echo 1500 > /proc/sys/vm/dirty_writeback_centisecs"
  sudo sh -c "echo min_power > /sys/class/scsi_host/host0/link_power_management_policy"

  sudo sh -c "xbacklight -set 50"
  sudo sh -c "ethtool -s eth0 wol d"		#disable wake up on lan
  sudo sh -c "ethtool -s eth0 autoneg off speed 100"	 #set speed minder, autoneg off
  echo "off power"
fi
```

I have tried
sudo sh -c "echo 5 > /proc/sys/vm/laptop_mode" 
as well as
echo 5 > /proc/sys/vm/laptop_mode

It doesn't work. Does anyone have a suggestion?

Thanks

---

### Post by sdennie on 2008-08-21
> **the_softy said:**
> Hi, i'm to this forum. And i have a problem. I have made the script with some basic stuff. I gave everybody execute rights on the file. When i execute it normally ( ./99-save-power.sh ), it works. When i execute when on battery, the screen dims and all the rest works too. When on power cable, it works too.
 
But when I install it in sleep.d en power.d. Nothing happens when I go on battery. Not even the screen dims.


1) You don't need the "sudo sh -c" parts because the script will be executed as root.

2) Are you sure you have the correct permissions on the file where it's at in /etc/pm/sleep.d and /etc/pm/power.d?

3) Are you running Ubuntu 8.04 and is pm-utils installed?  You can check the latter with:

```

dpkg -l | grep pm-utils

```

---

### Post by the_softy on 2008-08-21
> 1) You don't need the "sudo sh -c" parts because the script will be executed as root.
Ok, I removed those
> 2) Are you sure you have the correct permissions on the file where it's at in /etc/pm/sleep.d and /etc/pm/power.d?
I'm not sure what the right permissions are. Both files in power.d en sleep.d have these permissions:
-rwxr-xr-x 1 root root  937 2008-08-21 17:04 99-save_power.sh
I think these are correct because everybody has read and execute permission
> 3) Are you running Ubuntu 8.04 and is pm-utils installed?  You can check the latter with:
```

dpkg -l | grep pm-utils

```
I am running Ubuntu 8.04 and pm-utils are installed. Laptop mode tools are also installed and enabled. Could this be the problem?


Thank you for you comments

---

### Post by the_softy on 2008-08-23
OK, i checked around and i figured out that the on_ac_power; function doesn't return a value.

From what I understand this function/script checks /proc/acpi/ac_adapter/state for the battery status.

I found my battery status is at /proc/acpi/ac_adapter/C236/state.

```
jens@jens-laptop:~$ sudo cat /proc/acpi/ac_adapter/C236/state 
state:                   on-line
```

Can I read this value in my original script? So I can test this value and not the on_ac_power script. Is this possible?

```
#!/bin/bash
if on_ac_power; then # so replace this line with an other test

else

fi
```

---

### Post by sdennie on 2008-08-23
> **the_softy said:**
> OK, i checked around and i figured out that the on_ac_power; function doesn't return a value.

From what I understand this function/script checks /proc/acpi/ac_adapter/state for the battery status.

I found my battery status is at /proc/acpi/ac_adapter/C236/state.

```
jens@jens-laptop:~$ sudo cat /proc/acpi/ac_adapter/C236/state 
state:                   on-line
```

Can I read this value in my original script? So I can test this value and not the on_ac_power script. Is this possible?

```
#!/bin/bash
if on_ac_power; then # so replace this line with an other test

else

fi
```

You should be able to use something like:

```

if grep on-line /proc/acpi/battery/*/state > /dev/null ; then

else

fi

```

---

### Post by youthforlinux on 2008-08-23
sorta not on topic...tho thanks vor this script is sweet helping me out a lot...anyone have the nVidia problem where screen blanks and vertical lines appear?  I read that it is a video card overheat problem.

---

### Post by sdennie on 2008-08-23
> **youthforlinux said:**
> sorta not on topic...tho thanks vor this script is sweet helping me out a lot...anyone have the nVidia problem where screen blanks and vertical lines appear?  I read that it is a video card overheat problem.

I've only seen that when upgrading the BIOS and rebooting.  It's easy enough to monitor the temperature of your GPU though.  Just use nvidia-settings and look at the temperature.  If it's regularly well above 60C, you have a problem.

---

### Post by youthforlinux on 2008-08-23
Well I called dell, and they need to replace the mobo...sigh....its ok tho hopefully that will correct this...however i would recommend upgrading to A12 Bios to all m1330 users if not already done as that seems to help prevent the problem from occuring, as it is definetley a defect in the lappy!

check this out!  apparently the warranty has been extended to cope with this situation!

[http://direct2dell.com/one2one/archive/2008/08/18/nvidia-gpu-update-dell-to-offer-warranty-enhancement-to-all-affected-customers-worldwide.aspx]("http://direct2dell.com/one2one/archive/2008/08/18/nvidia-gpu-update-dell-to-offer-warranty-enhancement-to-all-affected-customers-worldwide.aspx")

---

### Post by sdennie on 2008-08-23
> **youthforlinux said:**
> Well I called dell, and they need to replace the mobo...sigh....its ok tho hopefully that will correct this...however i would recommend upgrading to A12 Bios to all m1330 users if not already done as that seems to help prevent the problem from occuring, as it is definetley a defect in the lappy!

check this out!  apparently the warranty has been extended to cope with this situation!

[http://direct2dell.com/one2one/archive/2008/08/18/nvidia-gpu-update-dell-to-offer-warranty-enhancement-to-all-affected-customers-worldwide.aspx]("http://direct2dell.com/one2one/archive/2008/08/18/nvidia-gpu-update-dell-to-offer-warranty-enhancement-to-all-affected-customers-worldwide.aspx")

Wow.  Other than the fact that nvidia drivers are quite poor (in my opinion), I haven't had any problems with the card.  I think I'll add this to the list of reasons why Dell needs to give me a new machine just before my warranty runs out (after 2243 hours of usage, the metal plating is starting to flake off the hand rest).

---

### Post by youthforlinux on 2008-08-23
yeah, except they seem to be using their band of home technicians for this job of replacing the motherboard, instead of shipping the laptop to them for a complete replacement.

well actually this is quite funny, when this problem started for me...i upgraded my vista driver, but it flaked out way way more than ubuntu did....but in Vista this lappy has always been running a lot hotter than Ubuntu has so I really wouldn't be surprised if Vista had more of a hand in this problem....

oh...and i have that flaked off hand rest too!

---

### Post by sdennie on 2008-08-23
> **youthforlinux said:**
> yeah, except they seem to be using their band of home technicians for this job of replacing the motherboard, instead of shipping the laptop to them for a complete replacement.

well actually this is quite funny, when this problem started for me...i upgraded my vista driver, but it flaked out way way more than ubuntu did....but it Vista has always been running a lot hotter than Ubuntu has so I really wouldn't be surprised if Vista had more of a hand in this problem....

oh...and i have that flaked off hand rest too!

Vista?  I'm not sure what you mean by that...

;)

---

### Post by micky0604 on 2008-08-23
NEW YORK (AP) - The Williams sisters would meet in the quarterfinals of the U.S. Open, [wow power leveling](http://www.wowpower-leveling.com/worldofwarcraft-powerleveing.php/)a bit earlier than their matchup in the final of the last Grand Slam, Wimbledon.On the men's side, struggling four-time defending champ Roger Federer might have to get through No. 3 Novak Djokovic to reach the final. Djokovic, the Australian Open champ, owns something Federer lacks this year: a Grand Slam title.[wow powerleveling](http://www.wowpower-leveling.com/)[wow pl](http://www.wowpower-leveling.com/)New No. 1 Rafael Nadal avoided a potential semifinal matchup with Djokovic, but several hot players are in his half of the draw.[wow power leveling](http://www.wowpower-leveling.com/world_of_warcraft-power-leveling.htm/) No. 17 seed Juan Martin Del Potro of Argentina has won four straight tournaments. American James Blake, the No. 9 seed, is coming off a breakthrough victory over Federer at the Olympics.[wow powerleveling](http://www.wowpower-leveling.com/world_of_warcraft-power-leveling.htm/)[wow pl](http://www.wowpower-leveling.com/world_of_warcraft-power-leveling.htm/)Top seed Ana Ivanovic could face No. 6 Dinara Safina in the women's quarters. Safina has been playing well lately and won an Olympic silver medal[wow powerleveling](http://www.wowpowerleveling.com/worldofwarcraft-powerleveing.php/)[wow pl](http://www.wowpower-leveling.com/worldofwarcraft-powerleveing.php/)Serena Williams is seeded No. 4, and Venus, who beat her sister at Wimbledon, is the No. 7 seed. Each is a two-time U.S. Open champ.[wow power leveling](http://www.wowpower-leveling.com/)

---

### Post by kerneloftruth on 2008-08-24
*subscribes*

I've been reading this thread for some time now and just wanted to say 'thank you', guys, for all the collected knowledge :KS

for those only having 1GB or 2GB of ram there's [compcache]("http://code.google.com/p/compcache/wiki/CompilingAndUsing")

it puts the swapped-out pages into a virtual swap in ram & therefore eliminating the need to trash the hdd :)

**edit:**

@vor:

please also include

echo 1 > /sys/devices/system/cpu/sched_mc_power_savings ***# (ok you already included it ;) )***

this should save some additional energy on the cpu

and

echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

should become

echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

(there are 2 CPU cores after all ;) )

thanks

---

### Post by kerneloftruth on 2008-08-24
> **tinivole said:**
> 

Ooh, also.
Open up xorg.conf and put in the following section.
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
**        Option          "Coolbits"      "1"**
EndSection

```
Then restart X, and open up "**nvidia-settings**", then go into "**Clock Frequencies**" and enable Overclocking...
You can now underclock your Nvidia Card and save a bit more energy :D



were you successful in doing so ? everytime I changed the frequencies it would lock up for me :confused:

many thanks in advance

**edit:**

ok, guess I need to experiment a little with those settings ;)
[B]
edit2:[/B]
[B]
@bubbalouie[/B]:

are those settings > echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
  echo "77:30 76:22 10:21 8:20 6:17 136:13" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls

for the T9300 ? if no for which model is it ?

anyone has those settings for the T7500 ?

many thanks in advance

keep up this great work, guys ! :)

**edit3:**

nvidia has released new drivers which solved most of the problems people encountered in combination with compiz, firefox, kde4, etc.
[177.68 (BETA) for Linux x86/x86-64 released]("http://www.nvnews.net/vbulletin/showthread.php?t=118244") (they're still beta but work better than anything else ahead of them I used)

enter the following in X:

```
nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1
```

device-section in xorg.conf:

```
Section "Device"

    #VideoRam    131072
    # Insert Clocks lines here if appropriate
    # Insert Clocks lines here if appropriate
#     Option         "DisableGLXRootClipping"        "True"
    #Enable Underclocking
    Identifier     "GeForce 8400M GS"
    Driver         "nvidia"
    Option         "TripleBuffer" "false"
    Option         "RenderAccel" "true"
    Option         "RandRRotation" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBGLXVisuals" "true"
    Option         "OnDemandVBlankInterrupts" "True"
    Option         "NvAGP" "0"
    Option         "DamageEvents" "1"
#    Option         "BackingStore" "1" 
    Option         "InitialPixmapPlacement" "2"
    Option         "PixmapCacheSize" "2000000"
    # If you use render events, be sure to boot with the idle=poll option
    Option         "UseEvents" "False"
    #VideoRam    262144
    Option         "DPMS" "TRUE"
    Option         "NoLogo" "1"
    Option         "AllowIndirectPixmaps" "false"
    Option         "AllowSHMPixmaps" "0"
# Workaround for ugly Qt bugs with recent nvidia drivers and compiz
    Option         "UseCompositeWrapper" "true"
#    Option         "XAANoOffscreenPixmaps" "1"
    Option         "Coolbits" "1"
EndSection
```

I don't know how well they work with underclocking - time will show ...

---

### Post by youthforlinux on 2008-08-24
> **vor said:**
> Vista?  I'm not sure what you mean by that...

;)


haha well i dual-boot for now because i use it to watch TV and i'm not a huge mythtv fan:lolflag::lolflag:

oh and for some games once in a while....

---

### Post by kerneloftruth on 2008-08-24
> **bubbalouie said:**
> I thought this may help some people:

sudo apt-get install irqbalance

It's more or less a compliment to the power saving scheduler that is already being invoked, more info at:

[http://irqbalance.org/](http://irqbalance.org/)

I haven't got any measurable results on using this, however, if someone has a way to quantify the effect of running the daemon it'd be interesting to see what they find.

Cheers

Ryan :)

> [...] and irqbalance daemon was stopped to reduce the idle
  wakeup rate


here you go:

once with irqbalance running:
> Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 3.5%)         2.21 Ghz    10.6%
polling           0.0ms ( 0.0%)         2.21 Ghz     0.0%
C1                0.0ms ( 0.0%)         1.60 Ghz     1.0%
C2                0.1ms ( 0.1%)          800 Mhz    88.4%
C4                9.7ms (96.5%)

Wakeups-from-idle per second : 103.7    interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
**  23.7% ( 19.0)      <kernel IPI> : Rescheduling interrupts **
  12.7% ( 10.2)     <kernel core> : ehci_work (ehci_watchdog) 
  12.5% ( 10.0)     <kernel core> : ipmi_init_msghandler (ipmi_timeout) 
  12.2% (  9.8)      <kernel IPI> : function call interrupts
   6.7% (  5.4)       <interrupt> : extra timer interrupt
   4.0% (  3.2)            python : schedule_timeout (process_timeout)

Suggestion: Enable wireless power saving mode by executing the following command
:
  echo 5 > /sys/bus/pci/drivers/iwl3945/0000:0c:00.0/power_level 


and once with irqbalance **disabled**:
> Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 2.8%)         2.21 Ghz     7.8%
polling           0.0ms ( 0.0%)         2.21 Ghz     0.0%
C1                0.0ms ( 0.0%)         1.60 Ghz     0.0%
C2                0.4ms ( 0.0%)          800 Mhz    92.2%
C4               11.2ms (97.2%)

Wakeups-from-idle per second : 87.9     interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  16.0% ( 10.0)     <kernel core> : ehci_work (ehci_watchdog) 
  16.0% ( 10.0)     <kernel core> : ipmi_init_msghandler (ipmi_timeout) 
**  13.1% (  8.2)      <kernel IPI> : Rescheduling interrupts**
  11.5% (  7.2)      <kernel IPI> : function call interrupts
   6.4% (  4.0)       <interrupt> : extra timer interrupt
   5.1% (  3.2)            python : schedule_timeout (process_timeout)

Suggestion: Enable wireless power saving mode by executing the following command
:
  echo 5 > /sys/bus/pci/drivers/iwl3945/0000:0c:00.0/power_level

---

### Post by shae on 2008-08-24
> **kerneloftruth said:**
> 
[B]
@bubbalouie[/B]:

are those settings 
for the T9300 ? if no for which model is it ?

anyone has those settings for the T7500 ?

many thanks in advance

keep up this great work, guys ! :)

I have a T7500 and I use:

```
echo "11:22 8:15 6:15 136:15" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
echo "11:22 8:15 6:15 136:15" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
```

---

### Post by kerneloftruth on 2008-08-25
> **shae said:**
> I have a T7500 and I use:

```
echo "11:22 8:15 6:15 136:15" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
echo "11:22 8:15 6:15 136:15" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
```

Thanks ! :KS

I'll use those as reference & compare them against the results I get with that testing-script :)

---

### Post by sdennie on 2008-08-25
> **kerneloftruth said:**
> were you successful in doing so ? everytime I changed the frequencies it would lock up for me :confused:


I'm actually not underclocking the GPU at the moment.  I was for a while but, I believe it was the cause of a lockup after resume for me so stopped doing it.

> 
nvidia has released new drivers which solved most of the problems people encountered in combination with compiz, firefox, kde4, etc.
[177.68 (BETA) for Linux x86/x86-64 released]("http://www.nvnews.net/vbulletin/showthread.php?t=118244") (they're still beta but work better than anything else ahead of them I used)


I have mixed feelings about those drivers and the settings they recommend using.  Specifically, I think InitialPixmapPlacement=2 + PixmapCacheSize causes a lot of problems with suspend/resume.  The drivers do work much better with post 2.6.24 kernels but, I'm quite content with the stable drivers and the Hardy 2.6.24 kernel patched for ASPM.

> **kerneloftruth said:**
> 
for those only having 1GB or 2GB of ram there's [compcache]("http://code.google.com/p/compcache/wiki/CompilingAndUsing")

it puts the swapped-out pages into a virtual swap in ram & therefore eliminating the need to trash the hdd :)


I've not heard of that before but I will have a look.

> 
@vor:

please also include

echo 1 > /sys/devices/system/cpu/sched_mc_power_savings ***# (ok you already included it ;) )***


As far as I understand, this only reschedules threads for a specific CPU package.  So, if you run a single CPU machine, even if it has multiple cores, this option doesn't do anything.  I could be wrong though.

> 
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

should become

echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

(there are 2 CPU cores after all ;) )


For me, the cpufreq of cpu1 is just a symlink to cpu0 so I didn't bother to explicitly include the cpu1 setting.

> **kerneloftruth said:**
> here you go:

once with irqbalance running:


and once with irqbalance **disabled**:

I think there are diminishing returns on optimizing for "wakeups".  As an experiment, I tried fluxbox and, with nothing open, my wakeups were something crazy like 15 a second.  In contrast, with gnome, they are well over 100 but, the power savings was very similar.  It was better with fluxbox to be sure, but, having 10x fewer wakeups made a surprisingly small difference.

---

### Post by eldragon on 2008-08-25
vor, i dont know if you remember me from previous threads concerning power savings....im still there trying to achieve over 1 hour of battery usage. cant :(

this time, i disabled wireless, wired, usb, dimmed display. hdd shut down, and yet i cannot manage to get the notebook under 18Watt (long run) whatever that means.

ive followed this thread closely, and applied all hacks that were relevant to this notebook. im stumped about what else to try.

---

### Post by sdennie on 2008-08-25
> **eldragon said:**
> vor, i dont know if you remember me from previous threads concerning power savings....im still there trying to achieve over 1 hour of battery usage. cant :(

this time, i disabled wireless, wired, usb, dimmed display. hdd shut down, and yet i cannot manage to get the notebook under 18Watt (long run) whatever that means.

ive followed this thread closely, and applied all hacks that were relevant to this notebook. im stumped about what else to try.

Hola eldragon,

I'm not really sure what could cause your machine to use so much power.  Though not a "silver bullet", using a kernel with ASPM support (PCI-E power savings) has made a huge difference for me.  The 2.6.26 kernel has the feature but, the patch applies cleanly against 2.6.24 (including the Ubuntu 2.6.24 kernel) so, that's something to try.  As I've said before ASPM tipped the scale for me and my machine is so cool now that the fan is rarely on (which further reduces power consumption).

---

### Post by eldragon on 2008-08-25
> **vor said:**
> Hola eldragon,

I'm not really sure what could cause your machine to use so much power.  Though not a "silver bullet", using a kernel with ASPM support (PCI-E power savings) has made a huge difference for me.  The 2.6.26 kernel has the feature but, the patch applies cleanly against 2.6.24 (including the Ubuntu 2.6.24 kernel) so, that's something to try.  As I've said before ASPM tipped the scale for me and my machine is so cool now that the fan is rarely on (which further reduces power consumption).

considering ive ruled out almost everything except for
[LIST]
[*]intel graphics (GMA945/950)
[*]PCI-E ASPM <-- i dont know how to do this
[/LIST]

and im sure this notebook is capable of doing 1.5hs with this battery, its worth checking it out.

ive read something on this thread about using ondemand something concerning the pci-e bus. and applied it to my power savings script. but i didnt feel the thing. do i need a special kernel? could you point me where to look for how to get ASPM going on?

thanks a lot

EDIT

ok, eldragon <--- im with stupid.

i need the .26 kernel. so, compile time, too bad i dont know how to do that, and i already know its not trivial to do...so i'll just have to wait for intrepid :(

EDIT2

ive got some free time, so im going to give a shot and compile (or try to...), im following the wiki's guide to complie through git, (ubuntu's git source), downloading intrepid's kernel... will that do?

EOEDIT2

---

### Post by sdennie on 2008-08-25
Hola eldragon,

I don't have Intel graphics so can't really advise you on that.  However, for ASPM, you'll need a custom kernel.  It can be 2.6.26 or 2.6.24 patched for ASPM.  I personally run the Hardy version of 2.6.24 patched with ASPM support and have been very pleased with it.  If you decide to try that, you'll need a good guide on how to patch/compile a kernel.  This guide has worked for me in the past: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) and I'm attaching the patch I use against the Ubuntu kernel for ASPM support.

---

### Post by eldragon on 2008-08-25
> **vor said:**
> Hola eldragon,

I don't have Intel graphics so can't really advise you on that.  However, for ASPM, you'll need a custom kernel.  It can be 2.6.26 or 2.6.24 patched for ASPM.  I personally run the Hardy version of 2.6.24 patched with ASPM support and have been very pleased with it.  If you decide to try that, you'll need a good guide on how to patch/compile a kernel.  This guide has worked for me in the past: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) and I'm attaching the patch I use against the Ubuntu kernel for ASPM support.

ok, im on it...
already had the 2.6.24 source, so one step closer :D

got the patch, and im test running the patch against the source. then i'll keep on with the rest of the guide, will post afterwards with results..


EDIT

its taking ages to apply the patch, is this ok?

ive run from my linux source dir:
```

patch aspm.patch -p1 --dry-run

```
doing dry-run in order to make sure it will work...but its taking a lot of time .. is that correct?

EOEDIT

---

### Post by sdennie on 2008-08-25
> **eldragon said:**
> ok, im on it...
already had the 2.6.24 source, so one step closer :D

got the patch, and im test running the patch against the source. then i'll keep on with the rest of the guide, will post afterwards with results..


EDIT

its taking ages to apply the patch, is this ok?

ive run from my linux source dir:
```

patch aspm.patch -p1 --dry-run

```
doing dry-run in order to make sure it will work...but its taking a lot of time .. is that correct?

EOEDIT

No, the patch should apply almost instantly.  Try:

```

patch -p1 < aspm.patch

```

---

### Post by eldragon on 2008-08-25
while the kernel compiles, a question:

every time i get a new kernel, i have to build my own wireless module... is there a way both modules can coexist? (The one for this kernel, and the one for my default kernel)?

EDIT

ASPM running, and verified on powersave. battery lasted: 1h

running powertop -d -t 60 gives about 11.6W of usage, but that doesnt correlate with the battery's capacity which is supposed to be 11.1v x 2.0Ah = 22.2Wh

am i missing something? i should be getting about 1:30 ~2hs 

anyone got any more suggestions?

one more detail is that this new kernel does not include any type of sound (?) did this unintentional but helps to rule that out.

im attaching my outputs so that someone can help debug some more.
EOEDIT.

---

### Post by kerneloftruth on 2008-08-26
> **eldragon said:**
> considering ive ruled out almost everything except for
[LIST]
[*]intel graphics (GMA945/950)
[*]PCI-E ASPM <-- i dont know how to do this
[/LIST]

and im sure this notebook is capable of doing 1.5hs with this battery, its worth checking it out.

ive read something on this thread about using ondemand something concerning the pci-e bus. and applied it to my power savings script. but i didnt feel the thing. do i need a special kernel? could you point me where to look for how to get ASPM going on?

thanks a lot

EDIT

ok, eldragon <--- im with stupid.

i need the .26 kernel. so, compile time, too bad i dont know how to do that, and i already know its not trivial to do...so i'll just have to wait for intrepid :(

EDIT2

ive got some free time, so im going to give a shot and compile (or try to...), im following the wiki's guide to complie through git, (ubuntu's git source), downloading intrepid's kernel... will that do?

EOEDIT2

eldragon, I'm sure you laptop in the new future will experience a **much** longer battery runtime :guitar:

for example: 
> Framebuffer compression
As described in the graphics project page, modern Intel integrated graphics controllers support a feature called "Framebuffer compression". The picture on the screen is compressed in memory, so that updating the screen (during refresh) consumes less memory bandwidth (and thus energy). In measurements with a solid background, we've measured up to 0.6 Watts of power saving using this feature.


The framebuffer compression feature is added to very recent versions of the Intel graphics driver. If you're using an older distribution, you may want to consider updating to such a newer version of the driver.


While the data compression works best on solid color backgrounds, many people prefer to use a picture as a background. Intel engineers have written a program to help optimize such background images, to enable the compression feature to work better.


You can download this program from the downloads page. 

see: [lesswatts.org on display and graphics power-saving]("http://www.lesswatts.org/projects/display-and-graphics/power-saving.php")

do you have the smallest battery with wireless, bluetooth, highest backlight brightness on or why are you only getting 1 hours out of it ?

> running powertop -d -t 60 gives about 11.6W of usage, but that doesnt correlate with the battery's capacity which is supposed to be 11.1v x 2.0Ah = 22.2Wh

that value should be fine I get around 11.2W-12.6W :)

---

### Post by kerneloftruth on 2008-08-26
> **shae said:**
> I have a T7500 and I use:

```
echo "11:22 8:15 6:15 136:15" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
echo "11:22 8:15 6:15 136:15" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
```

shae, could you please post the output of:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
```

many thanks in advance :)

---

### Post by eldragon on 2008-08-26
> **kerneloftruth said:**
> eldragon, I'm sure you laptop in the new future will experience a **much** longer battery runtime :guitar:

for example: 


see: [lesswatts.org on display and graphics power-saving]("http://www.lesswatts.org/projects/display-and-graphics/power-saving.php")

do you have the smallest battery with wireless, bluetooth, highest backlight brightness on or why are you only getting 1 hours out of it ?



that value should be fine I get around 11.2W-12.6W :)

hey, thanks for that, right now im testing disabling DRI and see if i get better results...

the problem is even if 13w is ok, its missing some power drain, because with a 22wh batt, i should get aprox 1.5hours of runtime, which i dont, no matter what i do. those measurements are with backlight completely dimmed, and all tweaks applied. disabling dri has cut wakups to 1/3 so that might help a bit, will post back later

---

### Post by shae on 2008-08-26
> **kerneloftruth said:**
> shae, could you please post the output of:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
```

many thanks in advance :)

22 15 15 15 (same for cpu1)

(note I find that turning off the feature where intel allows the chip to run at a higher frequency DRASTICALLY reduces the temperatures attained during usage (and from what I can tell the power usage too))

---

### Post by sdennie on 2008-08-26
> **shae said:**
> 22 15 15 15 (same for cpu1)

(note I find that turning off the feature where intel allows the chip to run at a higher frequency DRASTICALLY reduces the temperatures attained during usage (and from what I can tell the power usage too))

I think you are talking about the scaling governor (powersave vs. ondemand).  I suppose it's possible that under some circumstances, disabling the frequency scaling might save power but, usually, it's best to let the CPU scale up and down so that it can spend more time in the deeper sleep states.  This explains the idea well (and humorously): [http://mjg59.livejournal.com/88608.html](http://mjg59.livejournal.com/88608.html)

For heat (and more particularly noise), I found that really forcing the disk to stay spun down made a big difference.  It's eerie to use a machine that is cool to the touch and silent.  Unfortunately, it's also a massive hassle to set this up right and possibly dangerous as it involves mounting various parts of the system as tmpfs.

---

### Post by eldragon on 2008-08-26
doing some more research, i did a battery calibration test that comes with the notebook's bios, and it rated it at about 14Wh which rounds it up to 1hr of battery life with my numbers....mistery solved :D

will do a whole run tomorrow with the brand new 44wH battery ive got sitting around. should get about 4hs of battery life...

---

### Post by iggykoopa on 2008-08-27
I started on a python gui for this, right now it doesn't actually change any settings. So far I have the gui itself partially implemented and it creates the config files. I'm just starting with python though so if anyone wants to look over the code I'd appreciate it. I was planning on having it be in the notification area and on right click you can manually set it to powersaving or performance and left click opens the preferences dialog. I've attached what I have so far.

---

### Post by sdennie on 2008-08-27
> **iggykoopa said:**
> I started on a python gui for this, right now it doesn't actually change any settings. So far I have the gui itself partially implemented and it creates the config files. I'm just starting with python though so if anyone wants to look over the code I'd appreciate it. I was planning on having it be in the notification area and on right click you can manually set it to powersaving or performance and left click opens the preferences dialog. I've attached what I have so far.

Excellent.  If you've got an svn repo where people can download the code and you intend to keep working on it, I'll add it to the original post.  I'll have a look at the code and give you feedback based on what it does in a VM.

---

### Post by iggykoopa on 2008-08-28
ok I set up the svn repo, it's on my home server so no promises it'll be up all the time cause I'm using crappy comcast. Wasn't able to get to much done with the gui tonight because figuring out svn. anyway here's how to check it out:
svn co [http://svn.e-trom.com/powersaving/trunk](http://svn.e-trom.com/powersaving/trunk) powersaving.py

still trying to figure out how a couple things should be implemented as well, like whether to just run the script as root or have it create the shell scripts dynamically and ask for your root password to install them. any input from you guys would be helpfull as I'm just starting in python, but I figured this would be a good project to learn with.

---

### Post by bubbalouie on 2008-08-28
> **kerneloftruth said:**
> were you successful in doing so ? everytime I changed the frequencies it would lock up for me :confused:

many thanks in advance

**edit:**

ok, guess I need to experiment a little with those settings ;)
[B]
edit2:[/B]
[B]
@bubbalouie[/B]:

are those settings 
for the T9300 ? if no for which model is it ?

anyone has those settings for the T7500 ?

many thanks in advance

keep up this great work, guys ! :)

**edit3:**

nvidia has released new drivers which solved most of the problems people encountered in combination with compiz, firefox, kde4, etc.
[177.68 (BETA) for Linux x86/x86-64 released]("http://www.nvnews.net/vbulletin/showthread.php?t=118244") (they're still beta but work better than anything else ahead of them I used)

enter the following in X:

```
nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1
```

device-section in xorg.conf:

```
Section "Device"

    #VideoRam    131072
    # Insert Clocks lines here if appropriate
    # Insert Clocks lines here if appropriate
#     Option         "DisableGLXRootClipping"        "True"
    #Enable Underclocking
    Identifier     "GeForce 8400M GS"
    Driver         "nvidia"
    Option         "TripleBuffer" "false"
    Option         "RenderAccel" "true"
    Option         "RandRRotation" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBGLXVisuals" "true"
    Option         "OnDemandVBlankInterrupts" "True"
    Option         "NvAGP" "0"
    Option         "DamageEvents" "1"
#    Option         "BackingStore" "1" 
    Option         "InitialPixmapPlacement" "2"
    Option         "PixmapCacheSize" "2000000"
    # If you use render events, be sure to boot with the idle=poll option
    Option         "UseEvents" "False"
    #VideoRam    262144
    Option         "DPMS" "TRUE"
    Option         "NoLogo" "1"
    Option         "AllowIndirectPixmaps" "false"
    Option         "AllowSHMPixmaps" "0"
# Workaround for ugly Qt bugs with recent nvidia drivers and compiz
    Option         "UseCompositeWrapper" "true"
#    Option         "XAANoOffscreenPixmaps" "1"
    Option         "Coolbits" "1"
EndSection
```

I don't know how well they work with underclocking - time will show ...
Hi, sorry about the delay, I've been a bit busy the last few weeks, yep, that's a T9300, it will go a touch lower without crashing, but I decided it was safer to go 2-3 values above each minimum to be safe....

---

### Post by bubbalouie on 2008-08-28
Wow,I am very impressed to, I have not even managed to go further than the initial research into what's doable, good show :)

I can't wait to see what you end up producing, my experience of python is that it makes coding something complicated very easy (I have a few projects on at work right now which have implemented far more functionality in the same amount of code as their Perl counterparts).... sadly my Python UI coding skills are near zero (I've done a little TK, which looked horrible in linux, however it was for a friend to use in windblows, if you do get stuck though, feel free to PM (though I don't know how helpful I'll be)...

---

### Post by iggykoopa on 2008-08-29
The gui is coming along but I was wondering if anyone knew of any services that cause the disk to spin up or are power-hungry that I can set to disable as well. I figured tracker would be good to disable but I'm not sure if there are any others. Also I'm developing this on a 1420N, I was wondering if the module for the webcam was the same(I don't have a webcam on mine but just curious so I can start a readme or another config file with compatable laptops).

---

### Post by shae on 2008-08-30
> **vor said:**
> I think you are talking about the scaling governor (powersave vs. ondemand).  I suppose it's possible that under some circumstances, disabling the frequency scaling might save power but, usually, it's best to let the CPU scale up and down so that it can spend more time in the deeper sleep states.  This explains the idea well (and humorously): [http://mjg59.livejournal.com/88608.html](http://mjg59.livejournal.com/88608.html)

For heat (and more particularly noise), I found that really forcing the disk to stay spun down made a big difference.  It's eerie to use a machine that is cool to the touch and silent.  Unfortunately, it's also a massive hassle to set this up right and possibly dangerous as it involves mounting various parts of the system as tmpfs.

I was referring to Intel Dynamic Acceleration.  In my personal experience, I found it not effective so I disabled it.

---

### Post by eldragon on 2008-08-31
```

 echo 10 > /sys/module/snd_hda_intel/parameters/power_save

```

this makes sound not work anymore on my notebook. i do have the snd_hda_intel module btw. but i lose sound once i jump to battery-mode, and it stays that way when i plug the ac_adaptor...

any clues on why this might happen? ive disabled it for the time being

---

### Post by kerneloftruth on 2008-08-31
> **eldragon said:**
> ```

 echo 10 > /sys/module/snd_hda_intel/parameters/power_save

```

this makes sound not work anymore on my notebook. i do have the snd_hda_intel module btw. but i lose sound once i jump to battery-mode, and it stays that way when i plug the ac_adaptor...

any clues on why this might happen? ive disabled it for the time being

that's a bug with 2.6.24 kernels, I've experienced this too, but since ubuntu doesn't provide newer kernels you have 2 solutions:

1*) report to launchpad to get backported alsa-fixes and updated/working kernels

2*) get your hands on a newer kernel & use that instead

I'm using 2.6.27-rc5-zen* here & the intel-hda energy-saving works great (afaik it also worked fine with 2.6.26, not sure about 2.6.25 though)

---

### Post by sdennie on 2008-08-31
> **eldragon said:**
> ```

 echo 10 > /sys/module/snd_hda_intel/parameters/power_save

```

this makes sound not work anymore on my notebook. i do have the snd_hda_intel module btw. but i lose sound once i jump to battery-mode, and it stays that way when i plug the ac_adaptor...

any clues on why this might happen? ive disabled it for the time being

Another thing you could try would be to download the latest alsa-driver from: [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) build and install it.  It's very straightforward and may fix your problem (you'll have to remove the old sound modules and put the new ones in or reboot before you'll see any difference).

---

### Post by eldragon on 2008-08-31
considering ive got compiled and working 2.27-rc4-git6 with no sound, getting the drivers and using those, would that fix it?

i dont know why every time i compile a kernel not coming from the ubuntu repos i end up with no sound....is it always mandatory to get sound from the alsa page when getting the kernel.org code?

EDIT

that did the trick, didnt build on 2.27 since i dont know if i configured it correctly, but on the current 2.24.19 it worked ok, thanks!

EOEDIT

---

### Post by atlas95 on 2008-09-01
Cool an applet is coming !
I must reinstall phc and aspm so :D

---

### Post by iggykoopa on 2008-09-03
ok I've got a very beta version up on svn. Issues right now are you need to run it from a root terminal(not sure how to get around that), so to run:
sudo su
python powersaving.py

link_power_management_policy is not changing for some reason even when run from a root terminal. Also you can't change the settings yet unless you manually change them in the config file.Couple other things here and there I need to finish up and once I get everything in this version running correctly I'll add some more to it.

Sorry if it's hackish at all, this is one of my first python programs so still learning, but give it a try and let me know how it works. Also if anyone is graphically inclined and wants to make icons for me for power saving and performance mode I'd appreciate it. Otherwise your gonna end up with stick figures.

---

### Post by sygrup on 2008-09-04
hi vor,

thanks for your guide: is it usable on a Dell XPS M1530?

thanks again. :)

---

### Post by iggykoopa on 2008-09-04
you should be fine on a 1530, I'm using it on a 1420 and it works great.

---

### Post by kerneloftruth on 2008-09-05
**@vor:**

could you please add noatime,nodiratime

to your remount commands ?

the best would be to add both to /etc/fstab

otherwise people will get the same problem like Bráulio:

[http://news.gmane.org/gmane.comp.file-systems.reiserfs.general]("http://news.gmane.org/gmane.comp.file-systems.reiserfs.general")

thanks

---

### Post by iggykoopa on 2008-09-06
committed some more changes to svn. Saving preferences now works, fixed stopping trackerd. I found out trackerd is not actually a service so I had to use killall trackerd to stop it, not the cleanest way but unless someone can tell me a better way I'll have to stick with that. Still haven't figured out how to get link_power_management_policy to work right. I haven't test it yet but for now you should be able to change the journal commit option to 600,noatime,nodiratime to turn off access times. If it works than I'll change to option from journal commit to mount options or something. I'll add the stuff for the NVidia card and the newer kernel soon but I'm writing this on a 1420 with intel graphics so don't have a way to test it. If anyone thinks of any other power saving options let me know.

---

### Post by atlas95 on 2008-09-06
Hi !
For me good path to wlan setting iwl4965 is:
/sys/bus/pci/drivers/iwl4965/0000:0c:00.0/power_level

I have write it like this:

```

    if settings["wifi_power_performance_enabled"]:
        wifi_power_file = open("/sys/bus/pci/drivers/iwl4965/0000:0c:00.0/power_level","w")
        try:
            wifi_power_file.write(settings["6"])
        except:
            print "failed to set wifi power level"

```
because normally i switch like this ...

echo 6 > /sys/bus/pci/drivers/iwl4965/0000\:0c\:00.0/power_level
or
echo 5 > /sys/bus/pci/drivers/iwl4965/0000\:0c\:00.0/power_level

but this doesn't work.  :(

How to do?


AND, for sata, is use on m1330: host2,host3 and host4, no host0 and host1 .

The problem is if a settings fail, all the next setting aren't called.

Another problem is for launch trackerd, in bash for run it corretly i use "trackerd &" and in your script, trackerd is call without the & in python...

Thanks again, sorry for my english and i hope you understand me :)

---

### Post by iggykoopa on 2008-09-06
I'll have to use a regex for the wireless, haven't used them before so something new to learn tonight. If a command fails the other commands still run, just some of the commands don't have any output, I can have it say whether a command was successful if you would like. Also I believe I used the & for trackerd but I'll doublecheck. I should be able to get a new version up sometime tonight(U.S. mountain time). Also if anyone can help me figure out how to get the link power management policy to work right I'd appreciate it, what I think is happening is the same issue when you try to change it by sudo i.e.
sudo echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
if you try that from the terminal it will tell you permission denied.(change the host to whatever hosts your laptop uses). I believe the same thing is happening in this script even though I execute it from a root terminal.

---

### Post by iggykoopa on 2008-09-06
ok fixed link_power_management_policy so it actually works now, I just have it check all the hosts and change all their policy's. Also fixed the wireless. Now I just need some people to test it out some more before I add anything else or write the help for it, tell me if the labels for the settings make sense and if everything works for you. If everything works so far then I can start adding more options, i.e. changing swappiness, disabling hal polling, disable compiz.

---

### Post by sdennie on 2008-09-07
> **kerneloftruth said:**
> **@vor:**

could you please add noatime,nodiratime

to your remount commands ?

the best would be to add both to /etc/fstab

otherwise people will get the same problem like Bráulio:

[http://news.gmane.org/gmane.comp.file-systems.reiserfs.general]("http://news.gmane.org/gmane.comp.file-systems.reiserfs.general")

thanks

In Hardy, at the very least ext3 filesystems are mounted relatime by default so I'm not sure if it's needed.  I've been a bit busy but, I can take a look at those options.  At least for ext3, I'm pretty sure relatime is sufficient though.  When I'm positive my disks are spun down, I can edit a file that I know is cached and it doesn't spin the disks up.

> **iggykoopa said:**
> ok fixed link_power_management_policy so it actually works now, I just have it check all the hosts and change all their policy's. Also fixed the wireless. Now I just need some people to test it out some more before I add anything else or write the help for it, tell me if the labels for the settings make sense and if everything works for you. If everything works so far then I can start adding more options, i.e. changing swappiness, disabling hal polling, disable compiz.

I don't have time to check this out thoroughly at the moment.  It sounds interesting and I'd like to check it out but, I also don't want it to divert this thread too far off topic.  If you can post a link to a sourceforge or google code page for the project, I'll be happy to post it in the first thread though.

---

### Post by iggykoopa on 2008-09-07
heres my svn server I'm hosting it on:
[http://svn.e-trom.com/powersaving](http://svn.e-trom.com/powersaving)
if you want I can just start another thread on the gui, I was thinking about switching it to pysqlite for the config so I can make a compatibility database for different models so it wouldn't just be in the dell support forums anyway. Does anyone know another good way to store the configs thats built into python that I wouldn't require them to install anything else?

---

### Post by szuki on 2008-09-08
> **iggykoopa said:**
> heres my svn server I'm hosting it on:
[http://svn.e-trom.com/powersaving](http://svn.e-trom.com/powersaving)
if you want I can just start another thread on the gui, I was thinking about switching it to pysqlite for the config so I can make a compatibility database for different models so it wouldn't just be in the dell support forums anyway. Does anyone know another good way to store the configs thats built into python that I wouldn't require them to install anything else?

[http://docs.python.org/lib/module-ConfigParser.html](http://docs.python.org/lib/module-ConfigParser.html) ?

---

### Post by Gooler on 2008-09-10
> **the_softy said:**
> OK, i checked around and i figured out that the on_ac_power; function doesn't return a value.

I know I'm late to reply this but on_ac_power returns the information in it's exit status. If the laptop is on AC, the exit status is 0, when on battery is 1, and by UNIX convention 0 is true, so maybe you think it doesn't work when it really does.

You can check the exit status of any command by typing $? on the terminal after running that program. Should say something like: bash: 0: command not found. That 0 is the exit status.

[quote=kerneloftruth]echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

should become

echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

(there are 2 CPU cores after all )
[/quote]
Thanks for the tip, mine aren't symlinks and didn't realize to use it.

[quote=Vor]
Quote:
@vor:

please also include

echo 1 > /sys/devices/system/cpu/sched_mc_power_savings # (ok you already included it )
As far as I understand, this only reschedules threads for a specific CPU package. So, if you run a single CPU machine, even if it has multiple cores, this option doesn't do anything. I could be wrong though.[/quote]

From [http://www.bughost.org/pipermail/power/2007-June/000553.html]("http://www.bughost.org/pipermail/power/2007-June/000553.html") I understand that the setting actually saves some power.

By the way, Dell also changed my mainboard because the Nvidia chip died.

---

### Post by Oliver Acevedo on 2008-09-10
These scripts were great but they failed to mention that if your AP doesn't support Power Saving Poll, it will kill your network and you won't be able to connect anymore. 

I installed it in hopes to improve my battery and then my network started acting up. It would just randomly disconnect until now it doesn't connect at all. I can boot up into Vista and connect but not in Linux. 

My question is, how do I undo what I've done? I've tried taking out the lines 
echo 6 > /sys/bus/pci/drivers/iwl4965/0000\:0c\:00.0/power_level
and
echo 5 > /sys/bus/pci/drivers/iwl4965/0000\:0c\:00.0/power_level

and then running the script again but it still won't connect. I've never had problems connecting to the wireless network. I've tried everything and nothing has worked. My AP does not have a firmware that supports Power Saving Poll so my only option I think would be to uninstall the script some how. How do I go about doing this? Thanks

---

### Post by Gooler on 2008-09-11
You can try to disable the wifi power management: sudo iwconfig wlan0 power off

---

### Post by Oliver Acevedo on 2008-09-11
> **Gooler said:**
> You can try to disable the wifi power management: sudo iwconfig wlan0 power off

I tried that but it didn't work. I don't know to what extent that script changed the configuration of my wifi driver. Or if it was even that, that it changed. I don't have too much knowledge with Linux but I've done a lot of research about this and all I've found is that some AP aren't compatible and if you start having problems connecting, then you need to upgrade the firmware of your AP. My AP has the latest firmware which doesn't support power saving. I have yet to find a clue as to what to do if it's not compatible even with the latest firmware...

---

### Post by Gooler on 2008-09-11
Have you tried to run
```
cat /sys/bus/pci/drivers/iwl????/*/power_level
```
and see if the result is different from 6 (AC) OFF run? That would mean that the power saving is off on the card. If not, run
```
echo 6 > /sys/bus/pci/drivers/iwl????/*/power_level
```
and see what the cat command shows now and to connect again to your network.

---

### Post by Oliver Acevedo on 2008-09-11
> **Gooler said:**
> Have you tried to run
```
cat /sys/bus/pci/drivers/iwl????/*/power_level
```
and see if the result is different from 6 (AC) OFF run? That would mean that the power saving is off on the card. If not, run
```
echo 6 > /sys/bus/pci/drivers/iwl????/*/power_level
```
and see what the cat command shows now and to connect again to your network.


That's really weird because it does say 6 (AC) OFF. Another thing I noticed is that I can connect to other wireless networks, just not mine... I didn't change anything in the router and it works fine under Vista so I don't know what going on. This all started after I ran the script so maybe it's something else in the script? The power saving poll seemed to be the best bet for me because it's a known side effect but if it's off, then should I rule that one out?

here is my sudo lshw:
 *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 61
                serial: 00:1f:3b:d3:89:5b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

---

### Post by zrtom on 2008-09-11
I installed vor's original script and power went from 24 watts to around 12-15 watts!  Very nice!
Later I deleted the sleep.d and power.d folders in /etc/pm to check "Factory" power levels again.  When I ran
sudo install 99-savings /etc/pm/power.d
sudo install 99-savings /etc/pm/sleep.d
the second time, it didn't install 99-savings as a shell script within new folders power.d and sleep.d.  Instead, it installed 99-savings as D source code files in /etc/pm.  And I'm not sure whether its working.

Am I doing something wrong?
Tom

[SIZE="1"]XPS M1330, 2.2GHz, 4GB, 320GB, Quad Boot Ubuntu 8.04 x64, XP Pro x64, Vista Ultimate x64, Media Direct[/SIZE]

---

### Post by Oliver Acevedo on 2008-09-11
I've changed the driver to nsdwrapper because I tried to upgrade it and it just made it worse. Here's the new output

*-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 61
                serial: 00:1f:3b:d3:89:5b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+netw4x64 driverversion=1.52+Intel,03/13/2008,11.5.1.15 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g


But it still won't connect...

---

### Post by sdennie on 2008-09-12
> **zrtom said:**
> I installed vor's original script and power went from 24 watts to around 12-15 watts!  Very nice!
Later I deleted the sleep.d and power.d folders in /etc/pm to check "Factory" power levels again.  When I ran
sudo install 99-savings /etc/pm/power.d
sudo install 99-savings /etc/pm/sleep.d
the second time, it didn't install 99-savings as a shell script within new folders power.d and sleep.d.  Instead, it installed 99-savings as D source code files in /etc/pm.  And I'm not sure whether its working.

Am I doing something wrong?
Tom


That looks correct to me.  And, no, the script won't work out of just /etc/pm I don't think because it runs based on the events that power.d and sleep.d handle.  Do those directories still exist?

> **Oliver Acevedo said:**
> I've changed the driver to nsdwrapper because I tried to upgrade it and it just made it worse. Here's the new output

*-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 61
                serial: 00:1f:3b:d3:89:5b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+netw4x64 driverversion=1.52+Intel,03/13/2008,11.5.1.15 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g


But it still won't connect...

I wouldn't use ndiswrapper for that card.  It should be easy enough to test whether the scripts are causing the problem (I can't imagine that they are) by simply doing the following:

```

sudo rm /etc/pm/sleep.d/99-savings*
sudo rm /etc/pm/power.d/99-savings*

```

Then, to really make sure, you'll want to completely shutdown your machine and then turn it on again (not just reboot).  I have a feeling something else is going on though.  So, if it still doesn't work, post the output of:

```

iwconfig

```

---

### Post by zrtom on 2008-09-12
> **vor said:**
> That looks correct to me.  And, no, the script won't work out of just /etc/pm I don't think because it runs based on the events that power.d and sleep.d handle.  Do those directories still exist?

Well, I removed those two directories.  Maybe they were there when I first started and I thought installing 99-savings created them.  I THOUGHT config.d (empty) was the only folder when I started but maybe I didn't check that.  Were they supposed to be there in the first place (but empty perhaps)?  Anyway, I recreated the directories and installed 99-savings into them.  I'll see what happens.

Pls bear with my inexperience in Ubuntu.  I just started using it and I think I'm hooked.  I probably shouldn't even be posting my beginner-type questions.  But make no mistake...with my (ancient-20 years ago) programming experience I'll be sure to mess it up real good....LOL

Hey, a couple days ago I was posting on the Dell Forums that the M1330 was getting hot using Ubuntu and now here I am writing this, checking emails, etc., at around 14 watts.  Haven't heard the fan bump up all day.  I've learned more on this forum than probably all others combined.

Tom

---

### Post by Oliver Acevedo on 2008-09-12
I wouldn't use ndiswrapper for that card.  It should be easy enough to test whether the scripts are causing the problem (I can't imagine that they are) by simply doing the following:

```

sudo rm /etc/pm/sleep.d/99-savings*
sudo rm /etc/pm/power.d/99-savings*

```

Then, to really make sure, you'll want to completely shutdown your machine and then turn it on again (not just reboot).  I have a feeling something else is going on though.  So, if it still doesn't work, post the output of:

```

iwconfig

```[/QUOTE]

Well I just did a restore of my system back to last week. Everything seems to be working so far. If I have any problems pop up again (the restore still had the scripts) I'll post. Thanks

---

### Post by patrickfromspain on 2008-09-13
I don't know why, but now I'm getting over a 1000 wake-ups per second, I've even seen more than 30,000!

In the list I get with the process that are causing the wake ups I don't see anything wrong... may powertop be misbehaving??

```


Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (27,7%)         1,67 Ghz     5,8%
C1                0,0ms ( 0,0%)         1333 Mhz     0,0%
C2                0,0ms (72,3%)         1000 Mhz    94,2%



Wakeups-from-idle per second : 32997,6  interval: 10,0s
no ACPI power usage estimate available

Top causes for wakeups:
  26,0% ( 30,2)      <kernel IPI> : Rescheduling interrupts 
  21,1% ( 24,5)       <interrupt> : extra timer interrupt 
  16,4% ( 19,0)              Xorg : schedule_timeout (process_timeout) 
   9,0% ( 10,5)     <kernel core> : ehci_work (ehci_watchdog) 
   6,5% (  7,5)       <interrupt> : ehci_hcd:usb3, uhci_hcd:usb6
   5,2% (  6,0)   USB device  3-2 : USB Reader (Genesys )
   1,7% (  2,0)     <kernel core> : clocksource_register (clocksource_watchdog)
   1,7% (  2,0)    wpa_supplicant : schedule_timeout (process_timeout)
   1,5% (  1,7)    gnome-terminal : schedule_timeout (process_timeout)
   1,1% (  1,3)           firefox : futex_wait (hrtimer_wakeup)
   0,9% (  1,1)      <kernel IPI> : TLB shootdowns
   0,9% (  1,0)            dhcdbd : schedule_timeout (process_timeout)
   0,9% (  1,0)      tprintdaemon : schedule_timeout (process_timeout)
   0,9% (  1,0)        pulseaudio : schedule_timeout (process_timeout)
   0,9% (  1,0)            python : schedule_timeout (process_timeout)
   0,9% (  1,0)        checkgmail : schedule_timeout (process_timeout)
   0,5% (  0,6)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer)
   0,5% (  0,6)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer)
   0,4% (  0,5)   hald-addon-stor : schedule_timeout (process_timeout)
   0,4% (  0,5)              wicd : schedule_timeout (process_timeout)
   0,4% (  0,5)           iwl3945 : ieee80211_sta_work (ieee80211_sta_timer)
   0,4% (  0,5)      wicd-monitor : schedule_timeout (process_timeout)
   0,3% (  0,4)       gnome-panel : schedule_timeout (process_timeout)
   0,3% (  0,3)   gnome-power-man : schedule_timeout (process_timeout)
   0,2% (  0,2)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer)

```

---

### Post by sdennie on 2008-09-13
> **zrtom said:**
> Well, I removed those two directories.  Maybe they were there when I first started and I thought installing 99-savings created them.  I THOUGHT config.d (empty) was the only folder when I started but maybe I didn't check that.  Were they supposed to be there in the first place (but empty perhaps)?  Anyway, I recreated the directories and installed 99-savings into them.  I'll see what happens.


Recreating the directories and re-installing the scripts seems like the right idea to me.  The initially exist but are empty.

> 
Pls bear with my inexperience in Ubuntu.  I just started using it and I think I'm hooked.  I probably shouldn't even be posting my beginner-type questions.  But make no mistake...with my (ancient-20 years ago) programming experience I'll be sure to mess it up real good....LOL


If no one asked questions, we wouldn't need a forum.  ;)  Also, as a tip, whenever I'm going to do something that seems dangerous, I first try it in a virtual machine (VirtualBox).  That way I can test it without destroying my real machine.  I don't know how applicable this is to power savings stuff but, having an Ubuntu VM that you can try things in is incredibly valuable.

> 
Hey, a couple days ago I was posting on the Dell Forums that the M1330 was getting hot using Ubuntu and now here I am writing this, checking emails, etc., at around 14 watts.  Haven't heard the fan bump up all day.  I've learned more on this forum than probably all others combined.


The M1330 has fans?  ;)

> **patrickfromspain said:**
> I don't know why, but now I'm getting over a 1000 wake-ups per second, I've even seen more than 30,000!

In the list I get with the process that are causing the wake ups I don't see anything wrong... may powertop be misbehaving??

```


Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (27,7%)         1,67 Ghz     5,8%
C1                0,0ms ( 0,0%)         1333 Mhz     0,0%
C2                0,0ms (72,3%)         1000 Mhz    94,2%



Wakeups-from-idle per second : 32997,6  interval: 10,0s
no ACPI power usage estimate available

Top causes for wakeups:
  26,0% ( 30,2)      <kernel IPI> : Rescheduling interrupts 
  21,1% ( 24,5)       <interrupt> : extra timer interrupt 
  16,4% ( 19,0)              Xorg : schedule_timeout (process_timeout) 
   9,0% ( 10,5)     <kernel core> : ehci_work (ehci_watchdog) 
   6,5% (  7,5)       <interrupt> : ehci_hcd:usb3, uhci_hcd:usb6
   5,2% (  6,0)   USB device  3-2 : USB Reader (Genesys )
   1,7% (  2,0)     <kernel core> : clocksource_register (clocksource_watchdog)
   1,7% (  2,0)    wpa_supplicant : schedule_timeout (process_timeout)
   1,5% (  1,7)    gnome-terminal : schedule_timeout (process_timeout)
   1,1% (  1,3)           firefox : futex_wait (hrtimer_wakeup)
   0,9% (  1,1)      <kernel IPI> : TLB shootdowns
   0,9% (  1,0)            dhcdbd : schedule_timeout (process_timeout)
   0,9% (  1,0)      tprintdaemon : schedule_timeout (process_timeout)
   0,9% (  1,0)        pulseaudio : schedule_timeout (process_timeout)
   0,9% (  1,0)            python : schedule_timeout (process_timeout)
   0,9% (  1,0)        checkgmail : schedule_timeout (process_timeout)
   0,5% (  0,6)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer)
   0,5% (  0,6)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer)
   0,4% (  0,5)   hald-addon-stor : schedule_timeout (process_timeout)
   0,4% (  0,5)              wicd : schedule_timeout (process_timeout)
   0,4% (  0,5)           iwl3945 : ieee80211_sta_work (ieee80211_sta_timer)
   0,4% (  0,5)      wicd-monitor : schedule_timeout (process_timeout)
   0,3% (  0,4)       gnome-panel : schedule_timeout (process_timeout)
   0,3% (  0,3)   gnome-power-man : schedule_timeout (process_timeout)
   0,2% (  0,2)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer)

```

That looks like a bug in powertop.  If you mentally add the top few, it would be impossible to get to 30,000.  However, it's possible that you just need to wait for a minute for the machine to "stabilize".  Power savings is not an exact science and neither is system monitoring.  Having said that, the powertop output looks like you are using a USB disk while on battery.  I don't know the power ramifications of doing that but, it does mean that you can't shutdown the usb subsystem (which is a huge win for power savings).

---

### Post by patrickfromspain on 2008-09-13
There wasn't any usb disk connected, but I believe that's something to do with the card reader (also no card inserted).

I believe it must be some kind of bug, because with so many wakeups I believe the CPU would neve get into the C2 state, or would it?

As for the power, if I'm doing only firefox and light stuff, I get a power consumption of ~25W, (I can't enable sata power management, but I have a .26 kernel with pcie_aspm enabled and working). Is it "normal" or should I get much lower values? What readings do you get with firefox open or doing other light work?

EDIT: while idle (no firefox or other heavy apps), I've seen a power consumption as low as 9,8W.

---

### Post by atlas95 on 2008-10-28
Hello,
What new about this project?
What is the new svn repository?

thx

---

### Post by Gooler on 2008-10-28
For KDE4, there is a power management service in development called PowerDevil that supports per profiles scripts, so i think that pretty much solves it for KDE4 users.

---

### Post by patagonik on 2008-10-31
First of all congratulations to you all for this thread. Dell people should take goods notes from it!!!

I'd like to tell you my experience with first script posted. Is the one I'm using right now, but with two modifications:

1st - I've removed from it the webcam section, because even in battery mode I use it quite a lot altogether with skype. Disabling the webcam was a problem for me.

2nd - I've removed the wifi section, because the downloading ratio was too slow (some rates decreased from 600 kb/s in AC mode to 12 (!!!) kb/s in battery mode).

That's it. The rest I kept it the same. Sure it will help somehow, even if my m1330 won't last for six hours.

Of course,if someone has some advice to have this two functionalities working properly, saving energy at the same time, I'll test them for sure.

Thanks again and congratulations... 

pata

---

### Post by cyprusxr3 on 2008-11-05
Thanks Vor and all for the great tips. I'm down from 15 watts idle to ~12.

I do have a question regarding the pci express ASPM power management. The original post says the value should be written to:
```
/sys/module/pcie_aspm/parameters/policy
```

However, my system does not seem to have the pcie_aspm folder within /sys/module/ (nor can I create it). I am running the ubuntu 8.10 kernel (2.6.27), which I am assured comes with ASPM support. The only other thing I can think of is that I am mistaken and my laptop does not have PCI-E, though that seems unlikely, as it is very similar to Vor's. Any suggestions?

System Specs:
Dell m1330
Intel C2D T7500 ("Santa Rosa" Centrino)
nVidia 8400m GS
Intel 3945 wifi
LED Backlit

Ubuntu 8.10 
Kernel 2.6.27-7-generic

Thanks!

---

### Post by AndrewZorn on 2008-11-06
I used vor's config in the first post.

After I did this, my laptop (M1330 with 8400gs and Intrepid 64) would start to do something strange. After maybe 1min of being logged in, the taskbar wouldn't respond (the Applications, Places, System will light up but not expand), couldn't alt-tab, basically nothing except mouse movement.

I have to hard restart to fix this.

I thought it was the Nvidia script but I disabled that and this still happens.

---

### Post by eldragon on 2008-11-06
> **cyprusxr3 said:**
> Thanks Vor and all for the great tips. I'm down from 15 watts idle to ~12.

I do have a question regarding the pci express ASPM power management. The original post says the value should be written to:
```
/sys/module/pcie_aspm/parameters/policy
```

However, my system does not seem to have the pcie_aspm folder within /sys/module/ (nor can I create it). I am running the ubuntu 8.10 kernel (2.6.27), which I am assured comes with ASPM support. The only other thing I can think of is that I am mistaken and my laptop does not have PCI-E, though that seems unlikely, as it is very similar to Vor's. Any suggestions?

System Specs:
Dell m1330
Intel C2D T7500 ("Santa Rosa" Centrino)
nVidia 8400m GS
Intel 3945 wifi
LED Backlit

Ubuntu 8.10 
Kernel 2.6.27-7-generic

Thanks!

concerning the aspm tweak, it will only work if you have the patch applied to the 2.6.24 kernels (and compiling), or the 2.6.27 kernel (intrepid) recompiled with the feature enabled (the intrepid kernel has the patch applied, but its disabled by default).

so, if you are bold enough, check this guide: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

if under intrepid. dont need to apply any patch, just scan the config menues for the aspm enabling option.


ps. the patch has been attached on a previous post.

---

### Post by atlas95 on 2008-11-06
Hello,

Please someone could add the case in the powersaving.py gui script for control ASPM ?

Thanks a lot

---

### Post by cyprusxr3 on 2008-11-06
> **eldragon said:**
> concerning the aspm tweak, it will only work if you have the patch applied to the 2.6.24 kernels (and compiling), or the 2.6.27 kernel (intrepid) recompiled with the feature enabled (the intrepid kernel has the patch applied, but its disabled by default).

so, if you are bold enough, check this guide: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

if under intrepid. dont need to apply any patch, just scan the config menues for the aspm enabling option.


ps. the patch has been attached on a previous post.


Ah hah! Thanks very much Eldragon. I've already added the patch of PHC, I can't see that this would be so much harder. I'll get that going right away. 10W here I come!

UPDATE:

After configuring the kernel for ASPM, and using Vor's script with a few tweaks from others added in, I have seen usage as low as 10.5 watts. Thanks all, wonderful guide.

System specs:
T7500 C2D
nVidia 8400m GS
7200RPM 160GB HDD
Intel 3945 wifi
LED backlight
9 Cell Battery w/ 7 hr battery life (est.)

---

### Post by iggykoopa on 2008-11-07
Atlas the aspm option is being added to the python gui, but I have moved it to [www.planetwatt.com](www.planetwatt.com) it's now being called watt power manager (the name isn't totally settled yet) I'm working on a new version that's a lot nicer, it detects what hardware your running and adds a lot more options. I haven't had much of a chance to work on it in the last two weeks, and I reloaded my server with intrepid so I need to set subversion back up. But keep an eye on the forums there and I should have a new version up sometime soon (time...and my daughter permitting). Also I put a python script in the wattos forums to launch firefox and load the cache into a ramdisk...haven't done much testing with it but if you'd like to try it out it's in the software section.

---

### Post by cyprusxr3 on 2008-11-10
I have another odd question for anyone kind enough to help. I notice that the more "aggressive" settings of the script attempt to unload bluetooth and webcam modules. However, it seems that ubuntu kernel does not allow unloading of modules that are "in use," and therefore these portions of the script seem to do nothing. Manually running then in terminal results in "module in use" errors.

Doing some research, some suggested that rmmod -f might force these modules to unload, however that sometimes results in a "resource temporarily unavailable" error.

I have mollified this problem to some extend by setting the external switch on my m1330 to turn off bluetooth (without effecting wireless), but the problem persists while attempting to unload the web cam module (Powertop, for example, insists that when attempting to enable USB suspend "A USB device is active 100.0% of the time: USB device  7-6 : Laptop Integrated Webcam").

It seems like there must be a way to force the kernel to unload these modules even if they are in use (and accept the consequences of a cut connection). 

Any thoughts? Thanks for the helping out a linux newb.

---

### Post by sdennie on 2008-11-10
> **cyprusxr3 said:**
> I have another odd question for anyone kind enough to help. I notice that the more "aggressive" settings of the script attempt to unload bluetooth and webcam modules. However, it seems that ubuntu kernel does not allow unloading of modules that are "in use," and therefore these portions of the script seem to do nothing. Manually running then in terminal results in "module in use" errors.

Doing some research, some suggested that rmmod -f might force these modules to unload, however that sometimes results in a "resource temporarily unavailable" error.

I have mollified this problem to some extend by setting the external switch on my m1330 to turn off bluetooth (without effecting wireless), but the problem persists while attempting to unload the web cam module (Powertop, for example, insists that when attempting to enable USB suspend "A USB device is active 100.0% of the time: USB device  7-6 : Laptop Integrated Webcam").

It seems like there must be a way to force the kernel to unload these modules even if they are in use (and accept the consequences of a cut connection). 

Any thoughts? Thanks for the helping out a linux newb.

I also have my switch setup to only disable bluetooth.  I believe another option would be to use:

```

/etc/init.d/bluetooth start

```

Use that after the modprobe commands on AC power and this before them on battery:

```

/etc/init.d/bluetooth stop

```

As for the webcam, I'm not sure why it would be in use and you'd be unable to unload the uvcvideo module.  Usually the blue light comes on when the webcam is active so, unless it's on, I don't know why it would be considered in use (however, I'll irrationally blame Pulse Audio).  You could attempt to blacklist the driver if you never use it.  Try adding the following to /etc/modprobe.d/blacklist:

```

blacklist uvcvideo

```

---

### Post by Clockswork on 2008-11-10
Just a quick question, can I delete the files 99-savings and 99-nvidia after installing the scripts? 

OH! And one more, I installed the 99-savings script after the first step and when I came down to the step where I should disable the bluetooth and USB subsavings. Should I just apply those to my 99-savings script and install it again? Will it overwrite the old one? Thanks :)

---

### Post by cyprusxr3 on 2008-11-10
> **Clockswork said:**
> Just a quick question, can I delete the files 99-savings and 99-nvidia after installing the scripts? 

OH! And one more, I installed the 99-savings script after the first step and when I came down to the step where I should disable the bluetooth and USB subsavings. Should I just apply those to my 99-savings script and install it again? Will it overwrite the old one? Thanks :)

It seems that the install command simply moves the scripts into the /etc/pm/power.d and /etc/pm/sleep.d directories. So yes, deleting the scripts from your home or a scripts directory should be fine, as long as they still exist in the sleep.d and power.d locations.

Yes, changing your scripts and installing them will override the old scripts. Feel free to add, delete, and test different commands this way to tweak your power settings. As posted earlier in the thread, a file containing ```
sudo install 99-savings.sh /etc/pm/sleep.d
sudo install 99-savings.sh /etc/pm/power.d
sudo install 99-nvidia.sh /etc/pm/sleep.d
sudo install 99-nvidia.sh /etc/pm/power.d

``` might be helpful. Name it something memorable, put it in the same directory as the editable scripts (i.e., ~/bin or ~/scripts), and make sure to make it executable. Then when you modify either power saving script it is just one command to install. Best of luck.

---

### Post by Clockswork on 2008-11-10
> **cyprusxr3 said:**
> It seems that the install command simply moves the scripts into the /etc/pm/power.d and /etc/pm/sleep.d directories. So yes, deleting the scripts from your home or a scripts directory should be fine, as long as they still exist in the sleep.d and power.d locations.

Yes, changing your scripts and installing them will override the old scripts. Feel free to add, delete, and test different commands this way to tweak your power settings. As posted earlier in the thread, a file containing ```
sudo install 99-savings.sh /etc/pm/sleep.d
sudo install 99-savings.sh /etc/pm/power.d
sudo install 99-nvidia.sh /etc/pm/sleep.d
sudo install 99-nvidia.sh /etc/pm/power.d

``` might be helpful. Name it something memorable, put it in the same directory as the editable scripts (i.e., ~/bin or ~/scripts), and make sure to make it executable. Then when you modify either power saving script it is just one command to install. Best of luck.

Thanks :D

---

### Post by stecklum on 2008-11-13
Hi folks,

when trying to implement the aspm power savings on my XPS M1330 running 2.6.24-21-generic I got halfway stuck. I compiled a kernel with a power consumption of as low as 10.8 W. However, due to naming conventions this kernel cannot access the 2.6.24-21-generic modules. Do I have to go through the pain to compile all the stuff, aka restricted modules etc., or is it possible just to "replace" the standard kernel. This question was asked before but I might have overlooked the answer (if there was any).

regards,
          B.St.

---

### Post by sdennie on 2008-11-13
> **stecklum said:**
> Hi folks,

when trying to implement the aspm power savings on my XPS M1330 running 2.6.24-21-generic I got halfway stuck. I compiled a kernel with a power consumption of as low as 10.8 W. However, due to naming conventions this kernel cannot access the 2.6.24-21-generic modules. Do I have to go through the pain to compile all the stuff, aka restricted modules etc., or is it possible just to "replace" the standard kernel. This question was asked before but I might have overlooked the answer (if there was any).

regards,
          B.St.

How did you compile your kernel?  Normally the modules for a kernel are in the image .deb if you've compiled it using make-kpkg.  What specific modules are you unable to load?

---

### Post by stecklum on 2008-11-14
I build it first according to the "old fashioned debian way" of the kernel building instructions but as I said, this kernel gets another name, and therefore cannot load the 2.6.24-21-generic modules. Moreover, it lacks the ubuntu modules, e.g uvcvideo. Then I made a build following the git-tree/apt-get method and installed the updated 2.6.24-21-generic image and headers. With this I failed to get the recompiled Nvidia driver working because of unresolved symbols. Funnily, after the install of the patched kernel the update notifier showed up and recommended to "update" to the original version. This is all a bit strange. In the old days, I would have made a "make bzimage" and simply copied the kernel into /boot.

---

### Post by stecklum on 2008-11-19
Did not succeed with the patch for the Hardy kernel, possibly since this changes the source but not the kernel headers which is the reason to end up with unresolved symbols. So I switched to intrepid where ASPM is included but not yet activated. I followed [http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid/](http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid/) to build another flavour with ASPM on. Worked like a charm. Predicted battery lifetime > 7 hours. Thanks for your support!

---

### Post by iggykoopa on 2008-11-20
ok the power management gui I'm writing is coming along...as I mentioned before I'm developing it for wattos, here's the post I just made for it over there:
I've decided to go with google code for hosting the power management gui. If people could start checking out the svn version I would appreciate it. to checkout use: 
svn checkout [http://wattospm.googlecode.com/svn/trunk/](http://wattospm.googlecode.com/svn/trunk/) wattospm 
to run it go into the wattospm directory and type: 
sudo sh -c "python powersaving.py" 
Status so far... I have the hardware autodetection done, it will automatically check if your on battery power or not and change the settings accordingly if it is in auto mode. You can change it to manual mode (for if your on a desktop or gaming) and set it to powersaving or performance. I've added in a few other power saving options, I'll document them once v .2 is done (the version your checking out). 
what's not done.... The advanced configuration gui, for now please just select basic mode. if you want to edit any settings you will have to do it manually in the config file (named conf in the wattospm directory). If you want to enable some settings that aren't turned on in basic mode go into the conf file and set detected and enabled both to = 1. The code to change the settings is all written except for usb, bluetooth, firewire, and tracker. Tracker I just haven't got to but I haven't done the other three because I'm doing testing to see if there is a way I can actually powerdown the bluetooth(I was testing it out and useing hciconfig and then rmmoding the bluetooth modules wasn't powering down the device). Anyway if you could test it out for me and put any bugs you have on the google code issues page for the project it would help out a lot. I'll be adding a few more powersaving options then start work on the advanced config gui and documentation. Shouldn't be much longer and the next version will be out(when it's ready I'll make an installer as well so all the files go in directories that make sense).


also cyprus for removing the bluetooth modules you need to do the sudo /etc/init.d/bluetooth stop first, then use hciconfig to powerdorn the device, then rmmod the bluetooth module(it probably won't let you the first time you try but it will tell you what modules depend on it, remove those first and youll be fine) but as I mentioned in the post above when I did this on my 1420 it didn't actually powerdown the device, not sure if it's a bug or how it's intended to work.

---

### Post by motin on 2008-11-20
> **iggykoopa said:**
> ok the power management gui I'm writing is coming along...as I mentioned before I'm developing it for wattos, here's the post I just made for it over there:
I've decided to go with google code for hosting the power management gui. If people could start checking out the svn version I would appreciate it. to checkout use: 
svn checkout [http://wattospm.googlecode.com/svn/trunk/](http://wattospm.googlecode.com/svn/trunk/) wattospm 
to run it go into the wattospm directory and type: 
sudo sh -c "python powersaving.py" 
Status so far... I have the hardware autodetection done, it will automatically check if your on battery power or not and change the settings accordingly if it is in auto mode. You can change it to manual mode (for if your on a desktop or gaming) and set it to powersaving or performance. I've added in a few other power saving options, I'll document them once v .2 is done (the version your checking out). 
what's not done.... The advanced configuration gui, for now please just select basic mode. if you want to edit any settings you will have to do it manually in the config file (named conf in the wattospm directory). If you want to enable some settings that aren't turned on in basic mode go into the conf file and set detected and enabled both to = 1. The code to change the settings is all written except for usb, bluetooth, firewire, and tracker. Tracker I just haven't got to but I haven't done the other three because I'm doing testing to see if there is a way I can actually powerdown the bluetooth(I was testing it out and useing hciconfig and then rmmoding the bluetooth modules wasn't powering down the device). Anyway if you could test it out for me and put any bugs you have on the google code issues page for the project it would help out a lot. I'll be adding a few more powersaving options then start work on the advanced config gui and documentation. Shouldn't be much longer and the next version will be out(when it's ready I'll make an installer as well so all the files go in directories that make sense).


also cyprus for removing the bluetooth modules you need to do the sudo /etc/init.d/bluetooth stop first, then use hciconfig to powerdorn the device, then rmmod the bluetooth module(it probably won't let you the first time you try but it will tell you what modules depend on it, remove those first and youll be fine) but as I mentioned in the post above when I did this on my 1420 it didn't actually powerdown the device, not sure if it's a bug or how it's intended to work.

Would you mind creating a separate thread for wattospm? I'd like to discuss further development there, instead of hijacking this thread. 

Especially, I'd like to cast a vote to merge [poweeersave]("http://linux.softpedia.com/get/Utilities/powEEErsave-36798.shtml")'s code structure (with login in one file, and all the hardware-specific commands in another - so that different files can be contributed to support different hardware configurations) and preset management, with your specific hardware commands, the tray icon and the auto-switch feature...

Another approach would be to build upon kpowersave all the way, instead of writing a whole new application/GUI.

---

### Post by iggykoopa on 2008-11-20
ok new thread here [http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309) . sorry for hijacking I just figured it was ot.

---

### Post by atlas95 on 2008-11-20
Happy to see this project progress ! I test it on my m1330

---

### Post by iggykoopa on 2008-11-27
you'll have to change the part for the nvidia stuff if your using intrepid. They changed gconf to use dbus now so your old code doesn't work anymore, see this [http://ubuntuforums.org/showthread.php?t=961726](http://ubuntuforums.org/showthread.php?t=961726) thread to get an idea on how to rewrite it(I ended up having to go a different route for the gui but thats updated now).

---

### Post by sdennie on 2008-11-27
> **iggykoopa said:**
> you'll have to change the part for the nvidia stuff if your using intrepid. They changed gconf to use dbus now so your old code doesn't work anymore, see this [http://ubuntuforums.org/showthread.php?t=961726](http://ubuntuforums.org/showthread.php?t=961726) thread to get an idea on how to rewrite it(I ended up having to go a different route for the gui but thats updated now).

That's for the heads up.  I'll test some things out later and update the first post.

---

### Post by TedBonel on 2008-12-06
Hi, 

     I tried out vor's settings on my xps1330. This seems to introduce another problem: stuttering. For example, I am in the middle of typing text in emacs and the computer freezes for two or three seconds and then I can continue typing. This happens every now and then.
     Can you help me pin-point exactly which of vor's settings causes this so that I can benefit from low load_cyles but *no* stuttering?
     Thanks.
     Ted.

PD: Here is the output of smartctl:

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD2500BEVT-75ZCT2
Serial Number:    WD-WXE708PU2680
Firmware Version: 11.01A11
User Capacity:    250,059,350,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Dec  6 09:58:53 2008 ARST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (9180) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 109) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   197   184   021    Pre-fail  Always       -       1133
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       162
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       31
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       30
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       5
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       2575
194 Temperature_Celsius     0x0022   109   094   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   100   100   000    Old_age   Always       -       20
241 Unknown_Attribute       0x0032   198   198   000    Old_age   Always       -       2280622300947
242 Unknown_Attribute       0x0032   200   200   000    Old_age   Always       -       103212165

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        24         -
# 2  Short offline       Completed without error       00%        24         -
# 3  Short offline       Completed without error       00%         3         -
# 4  Short offline       Completed without error       00%         1         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

---

### Post by sdennie on 2008-12-06
> **TedBonel said:**
> Hi, 

     I tried out vor's settings on my xps1330. This seems to introduce another problem: stuttering. For example, I am in the middle of typing text in emacs and the computer freezes for two or three seconds and then I can continue typing. This happens every now and then.


It's almost certainly caused by the "hdparm" line.  Specifically, the "-S 4" option.  There is a big bold note about Firefox before that option and the advice might be useful for you as well.  Rather than use "-S 4", use "-S 24" (two minutes) or even higher ("-S 240" will essentially ensure the disks never go to sleep).

Saludos

---

### Post by TedBonel on 2008-12-06
In fact, I already had "-S 24" set up. So I changed that to "-S 60". We'll see how it goes.

One more related remark. With your exact script I noticed that every now and then the hardrive would make a churning sound which would last half a second. Now I know this is a rather vague description to make much from it. But I'll just mention it in case someone else out there has had a similar experience. Once again, if you could pinpoint exactly which of the settings of the script might be the culprit, thanks.

Thanks for your prompt reply. 

     Saludos.

---

### Post by sdennie on 2008-12-06
> **TedBonel said:**
> In fact, I already had "-S 24" set up. So I changed that to "-S 60". We'll see how it goes.

One more related remark. With your exact script I noticed that every now and then the hardrive would make a churning sound which would last half a second. Now I know this is a rather vague description to make much from it. But I'll just mention it in case someone else out there has had a similar experience. Once again, if you could pinpoint exactly which of the settings of the script might be the culprit, thanks.


This also sounds like the "hdparm -S" setting actually.  That particular setting has some unfortunate cosmetic side effects (the pauses you describe and the whine that accompanies the disks spinning back up) and may be too aggressive for some people.  I would try -S 240 to essentially disable it and see if it helps.  In your case, it sounds like lower -S values wouldn't save much power because the disks are spinning up a lot and so you lose the indirect power savings of the settings (a cooler disk so a cooler machine so less fan activity).

---

### Post by Oliver Acevedo on 2008-12-07
Is there a way to uninstall or undo everything from these power saving scripts? Ever since I did them, my laptop's been acting funning. Every now and then, it just freezes for a couple of seconds and makes this clicking sound. It's very annoying and I think it's got something to do with these scripts.

---

### Post by sdennie on 2008-12-09
> **Oliver Acevedo said:**
> Is there a way to uninstall or undo everything from these power saving scripts? Ever since I did them, my laptop's been acting funning. Every now and then, it just freezes for a couple of seconds and makes this clicking sound. It's very annoying and I think it's got something to do with these scripts.

You can just delete them from /etc/pm if you don't want them anymore.  However, you may want to see the advice in the last few posts on this thread because it sounds like you are experiencing the same issues and there are solutions better than "delete the scripts".

---

### Post by EIN502 on 2008-12-15
I am still a noob to linux and have no idea where to find ASPM config file to enable it.  Can anyone help out?  I am running 8.10 so it should just need to be enabled.  Any help would make me happy.

---

### Post by sdennie on 2008-12-15
> **EIN502 said:**
> I am still a noob to linux and have no idea where to find ASPM config file to enable it.  Can anyone help out?  I am running 8.10 so it should just need to be enabled.  Any help would make me happy.

Unforutnately, in 8.10, ASPM is not turned on in the kernel.  If you want to use this feature you'll have to compile your own kernel.  If you are new to linux, this can be a fairly daunting task so, depending on how fanatical you are about power savings, possibly not worth the effort.

---

### Post by EIN502 on 2008-12-15
This is what I get when running on battery with wireless on:
> PowerTOP 1.10    (C) 2007, 2008 Intel Corporation 

Collecting data for 840 seconds 


Cn	          Avg residency
C0 (cpu running)        ( 0.6%)
polling		  0.0ms ( 0.0%)
C1		 46.9ms (49.9%)
C3		  8.3ms (49.5%)
P-states (frequencies)
  2.51 Ghz     0.0%
  2.50 Ghz     0.0%
  2.00 Ghz     0.0%
   800 Mhz   100.0%
Wakeups-from-idle per second : 70.3	interval: 840.0s
no ACPI power usage estimate available
Top causes for wakeups:
  41.9% ( 12.2)       <interrupt> : iwlagn 
  12.7% (  3.7)      <kernel IPI> : Rescheduling interrupts 
   6.8% (  2.0)     <kernel core> : clocksource_check_watchdog (clocksource_watchdog) 
   5.8% (  1.7)      <kernel IPI> : function call interrupts 
   5.0% (  1.5)    cpufreq-applet : schedule_timeout (process_timeout) 
   3.4% (  1.0)       <interrupt> : nvidia 
   3.4% (  1.0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer) 
   3.0% (  0.9)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   2.7% (  0.8)       <interrupt> : acpi 
   2.1% (  0.6)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   1.8% (  0.5)       compiz.real : schedule_timeout (process_timeout) 
   1.7% (  0.5)        pulseaudio : schedule_timeout (process_timeout) 
   1.7% (  0.5)    sensors-applet : schedule_timeout (process_timeout) 
   1.7% (  0.5)            iwlagn : ieee80211_sta_work (ieee80211_sta_timer) 
   1.0% (  0.3)   gnome-power-man : schedule_timeout (process_timeout) 
   1.0% (  0.3)   gnome-screensav : schedule_timeout (process_timeout) 
   0.9% (  0.3)       gnome-panel : schedule_timeout (process_timeout) 
   0.7% (  0.2)   update-notifier : schedule_timeout (process_timeout) 
   0.6% (  0.2)    NetworkManager : schedule_timeout (process_timeout) 
   0.4% (  0.1)    sensors-applet : inet_twsk_schedule (inet_twdr_hangman) 
   0.4% (  0.1)       <interrupt> : ahci 
   0.3% (  0.1)   <kernel module> : sta_info_start (sta_info_cleanup) 
   0.1% (  0.0)           syslogd : do_setitimer (it_real_fn) 
   0.1% (  0.0)              hald : schedule_timeout (process_timeout) 
   0.1% (  0.0)          gconfd-2 : schedule_timeout (process_timeout) 
   0.1% (  0.0)              Xorg : schedule_timeout (process_timeout) 
   0.1% (  0.0)     <kernel core> : queue_delayed_work (delayed_work_timer_fn) 
   0.1% (  0.0)              cron : do_nanosleep (hrtimer_wakeup) 
   0.0% (  0.0)      <kernel IPI> : TLB shootdowns 
   0.0% (  0.0)     <kernel core> : inet_initpeers (peer_check_expire) 
   0.0% (  0.0)    gnome-terminal : schedule_timeout (process_timeout) 
   0.0% (  0.0)     <kernel core> : rif_init (rif_check_expire) 
   0.0% (  0.0)         nm-applet : schedule_timeout (process_timeout) 
   0.0% (  0.0)     <kernel core> : inet_frags_init (inet_frag_secret_rebuild) 
   0.0% (  0.0)     <kernel core> : flow_cache_init (flow_cache_new_hashrnd) 
   0.0% (  0.0)     <kernel core> : laptop_io_completion (laptop_timer_fn) 
   0.0% (  0.0)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer) 
   0.0% (  0.0)    jockey-backend : schedule_timeout (process_timeout) 
   0.0% (  0.0)       dbus-daemon : schedule_timeout (process_timeout) 
   0.0% (  0.0)     <kernel core> : page_writeback_init (wb_timer_fn) 

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Recent USB suspend statistics
Active  Device name

This is what I get when running on battery with wireless off:
> PowerTOP 1.10    (C) 2007, 2008 Intel Corporation 

Collecting data for 840 seconds 


Cn	          Avg residency
C0 (cpu running)        ( 0.5%)
polling		  0.0ms ( 0.0%)
C1		 63.8ms (51.1%)
C3		 11.2ms (48.4%)
P-states (frequencies)
  2.51 Ghz     0.0%
  2.50 Ghz     0.0%
  2.00 Ghz     0.0%
   800 Mhz   100.0%
Wakeups-from-idle per second : 51.1	interval: 840.0s
no ACPI power usage estimate available
Top causes for wakeups:
  39.9% ( 10.5)       <interrupt> : ata_piix 
  11.5% (  3.0)      <kernel IPI> : Rescheduling interrupts 
   7.6% (  2.0)     <kernel core> : clocksource_check_watchdog (clocksource_watchdog) 
   3.8% (  1.0)       <interrupt> : extra timer interrupt 
   3.8% (  1.0)       <interrupt> : nvidia 
   3.8% (  1.0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer) 
   3.8% (  1.0)    cpufreq-applet : schedule_timeout (process_timeout) 
   3.5% (  0.9)      <kernel IPI> : function call interrupts 
   3.0% (  0.8)       <interrupt> : acpi 
   2.8% (  0.7)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   2.4% (  0.6)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   2.0% (  0.5)       compiz.real : schedule_timeout (process_timeout) 
   1.9% (  0.5)        pulseaudio : schedule_timeout (process_timeout) 
   1.9% (  0.5)   hald-addon-stor : schedule_timeout (process_timeout) 
   1.9% (  0.5)    sensors-applet : schedule_timeout (process_timeout) 
   1.1% (  0.3)   gnome-power-man : schedule_timeout (process_timeout) 
   1.0% (  0.3)       gnome-panel : schedule_timeout (process_timeout) 
   1.0% (  0.2)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0.8% (  0.2)   update-notifier : schedule_timeout (process_timeout) 
   0.6% (  0.1)   gnome-screensav : schedule_timeout (process_timeout) 
   0.5% (  0.1)    sensors-applet : inet_twsk_schedule (inet_twdr_hangman) 
   0.4% (  0.1)   <kernel module> : sta_info_start (sta_info_cleanup) 
   0.2% (  0.1)       <interrupt> : ahci 
   0.2% (  0.0)     <kernel core> : queue_delayed_work (delayed_work_timer_fn) 
   0.1% (  0.0)          gconfd-2 : schedule_timeout (process_timeout) 
   0.1% (  0.0)              hald : schedule_timeout (process_timeout) 
   0.1% (  0.0)           syslogd : do_setitimer (it_real_fn) 
   0.1% (  0.0)              cron : do_nanosleep (hrtimer_wakeup) 
   0.0% (  0.0)              Xorg : schedule_timeout (process_timeout) 
   0.0% (  0.0)     <kernel core> : addrconf_verify (addrconf_verify) 
   0.0% (  0.0)     <kernel core> : inet_initpeers (peer_check_expire) 
   0.0% (  0.0)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer) 
   0.0% (  0.0)      <kernel IPI> : TLB shootdowns 
   0.0% (  0.0)       dbus-daemon : schedule_timeout (process_timeout) 
   0.0% (  0.0)         nm-applet : schedule_timeout (process_timeout) 
   0.0% (  0.0)    gnome-terminal : schedule_timeout (process_timeout) 
   0.0% (  0.0)     <kernel core> : laptop_io_completion (laptop_timer_fn) 
   0.0% (  0.0)     <kernel core> : rif_init (rif_check_expire) 
   0.0% (  0.0)     <kernel core> : inet_frags_init (inet_frag_secret_rebuild) 
   0.0% (  0.0)     <kernel core> : flow_cache_init (flow_cache_new_hashrnd) 
   0.0% (  0.0)   <kernel module> : inet_frags_init (inet_frag_secret_rebuild) 
   0.0% (  0.0)    jockey-backend : schedule_timeout (process_timeout) 
   0.0% (  0.0)     <kernel core> : page_writeback_init (wb_timer_fn) 
   0.0% (  0.0)              Xorg : __hrtick_start (hrtick) 
   0.0% (  0.0)              Xorg : hrtick_start_fair (hrtick) 
   0.0% (  0.0)             touch : start_this_handle (commit_timeout) 

Disable Ethernet Wake-On-Lan with the following command:
  ethtool -s eth0 wol d 
Wake-on-Lan keeps the phy active, this costs power.

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Disable 'hal' from polling your cdrom with:  
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

Recent USB suspend statistics
Active  Device name

The 99-savings file reads:
> #!/bin/bash

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then
  # Set the drive to mostly stay awake.  Some may want to change -B 200
  # to -B 255 to avoid accumulating Load_Cycle_Counts
  hdparm -B 200 -S 240 -M 254 /dev/sda

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  mount -o remount,commit=60 /
  mount -o remount,commit=60 /home

  # Turn off the laptop mode disk optimization
  echo 0 > /proc/sys/vm/laptop_mode

  # Manually set the wifi driver to no power savings.
  echo 6 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Only wakeup every 60 seconds to see if we need to write dirty pages
  # By default this is every 5 seconds but, I prefer 60 to reduce disk
  # activity.
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs

  # Turn off sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  
  # Set the SATA to max performance
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
  echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

  # Enable the webcam driver
  modprobe uvcvideo

  # Optional: Put back most of the bluetooth/usb subsystem
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd

  # Use default on AC
  echo default > /sys/module/pcie_aspm/parameters/policy

  # Enable CD device polling
  hal-disable-polling --enable-polling --device /dev/scd0 &> /dev/null

  # Start bluetooth services
  /etc/init.d/bluetooth start
  hciconfig hci0 up # Is this line necessary?

else # Save power

  # Set the disks to aggressively save power and use the lowest acoustic
  # level.  Some might find these settings too aggressive.  If so, change 
  # "-S 4" to something larger like -S 24 (two minutes) and -B 1 to -B 255.
  hdparm -B 1 -S 4 -M 128 /dev/sda
  
  # Change the ext3 commit times to 10 minutes.  This reduces disk
  # activity
  mount -o remount,commit=600 /

  # Set laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945 driver to power savings.
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Set sound card power savings
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  # Set SATA to minimum power
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
  echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

  # Remove the webcam driver
  modprobe -r uvcvideo

  # Optional: Remove the most of the bluetooth/usb subsystem
  modprobe -r hci_usb
  modprobe -r rfcomm
  modprobe -r l2cap
  modprobe -r bluetooth
  modprobe -r usbhid
  modprobe -r uhci_hcd
  modprobe -r ehci_hcd

  # Use powersave on battery
  echo powersave > /sys/module/pcie_aspm/parameters/policy

  # Disable hal device polling for cd rom
  hal-disable-polling --device /dev/scd0 &> /dev/null

  # Stop bluetooth services
  /etc/init.d/bluetooth stop
  # hciconfig hci0 down; # Disabled as complains if bt already is disabled
fi


Now I know some things might not work right like the pci-e part, but I hope to get it to work at some point.

Now I am still new to all this, but once I get something stuck in my head it is rather hard to get it out.  I am going to be having three classes straight and I would at least like to get through two of those classes before I have to change batteries.

My system reads as this:
HP Pavilion DV6700 CTO
Core2Duo T9300
4GB RAM
250 GB
GeForce 8400M GS
Intel 4965 w/BT

I really want to make this work, but I need a little more help then most.  Plus you don't learn if you don't try.  I have looked into compiling [here]("http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid/"), but I don't have any idea how to add what I want.

I would like to try everything I can with the 99-savings file first and move from there.

Once again any help is well thanked. :p

---

### Post by EIN502 on 2008-12-22
bump

Any ideas?

---

### Post by sdennie on 2008-12-22
> **EIN502 said:**
> bump

Any ideas?

I'm not sure what your question is.  Your hardware looks very similar to what we XPS M1330 users have so, the instructions in this thread will probably work fine for you.  They may not guarantee 6+ hours of battery life for you but, they should drastically increase your battery life.

---

### Post by EIN502 on 2008-12-23
> **vor said:**
> I'm not sure what your question is.  Your hardware looks very similar to what we XPS M1330 users have so, the instructions in this thread will probably work fine for you.  They may not guarantee 6+ hours of battery life for you but, they should drastically increase your battery life.

I have gone through the instructions and read through all the posts many times.  I have even spent a great deal of time going through the 99-savings files everyone has posted.  Many of the files I do not understand and am thus unsure if there is more I can do on my own.  Some things like undervolting were much easier for me under Windows, but I would still like to do them under linux.  My biggest problem is that I don't know that I have done all I can with the 99-savings file.  I need someone who has more experience and understanding then myself.  Second I would like to compile my own kernel so that I can take advantage of what lesswatts.org has as well as undervolting.  My problem here is that I have not found a guide for adding in what I need when making a kernel.

Thanks again.

---

### Post by Axx83 on 2008-12-24
> My biggest problem is that I don't know that I have done all I can with the 99-savings file

Well GOOD luck, this issue is a lot underestimated by linux developers, I have played with the script a lot too.

For example on my thinkpad I lower brightness this way:

# Set video brightness to 100%
echo 100 > /proc/acpi/video/VID/LCD0/brightness
echo 100 > /proc/acpi/video/VID1/LCD0/brightness

for ac

# Set video brightness to 40%
echo 40 > /proc/acpi/video/VID/LCD0/brightness
echo 40 > /proc/acpi/video/VID1/LCD0/brightness

for battery

and disable the brightness management of gnomepowermanager (by running "gconf-editor" and disabling it there).

I have better results this way...but maybe it's a thinkpad only trick

---

### Post by Axx83 on 2008-12-24
Oh and by the way, disabling gnome power manager putting the pc in saving mode actually saves MORE power than letting it do it.

Go again in gconf-editor and find the section that asks whether to put it in saving mode or not, you'll see the difference in powertop.

---

### Post by EIN502 on 2008-12-29
Under "gconf-editor" I have no idea where to go to make the changes.

---

### Post by Axx83 on 2008-12-29
apps > gnome power manager

there you will find many subcategories, I personally unchecked everything in ambient, in backlight, in general I tuned the sleep mode to turn off and back on the network, in lowpower at first I unchecked the modes there but I think that way it doesn't work properly.

Well check everything with powertop, the changes are instantaneous, it's fast and practical.

By the way, which notebook have you got ?

---

### Post by EIN502 on 2008-12-30
Sorry it is not a Dell:

HP Pavilion DV6700 CTO
Core2Duo T9300
4GB RAM
250 GB
GeForce 8400M GS
Intel 4965 w/BT

Any idea how to get xbacklight from lesswatts.org to work?

---

### Post by EIN502 on 2008-12-30
So in I got my wakeups-from-idle to below 20 (it seemed to stay at 15 or less) with wireless off and not touching the computer.  The problem seems to be that the power usage will not go down.  For some reason I am using less watts keeping the wireless on and typing this post then when the laptop was doing nothing.  I have gone from just under 30 W to less then 21 W.  I really don't get it.  My interruptions are up to over 200 and I am saving power?!  I have turned off many of that you have told me under gnome power manager.

I have noticed that my processor sits at C1 more then C3 most of the time.  Even when I am not doing anything.  Any ideas on how to get it to spend more time in C3 or how to make a kernel with C4.  I have searched, but really can't find the information needed to get more then a little of the way it.  I feel like if I take one more step I will be in over my head.

This is all why I am looking for people who have more experience and know how.

Many thanks! :KS

---

### Post by Axx83 on 2008-12-31
The answer is easy, turn off usb1, that's a killer but I don't know why.

On my computer whith usb1 turned on I can't efficiently get in c3, only half of the time if I turn it off I go down to 11-12 watts awesome

```
modprobe -r ehci_hcd
modprobe -r uhci_hcd
```

this turns off both usb1 and usb2 but anyway when you turn one off there's no reason to let the other stay, usb mice won't run anyway

if you need them back

```
modprobe uhci_hcd
modprobe ehci_hcd
```

let me know if something improves

---

### Post by EIN502 on 2008-12-31
So it appears that I already have that in my 99-savings.sh file.  Though it seems that somethings may not be working.  I will post it again.  See if you can tell if I am doing something wrong.

99-savings.sh:

```
#!/bin/bash

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then
  # Set the drive to mostly stay awake.  Some may want to change -B 200
  # to -B 255 to avoid accumulating Load_Cycle_Counts
  hdparm -B 200 -S 240 -M 254 /dev/sda

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  mount -o remount,commit=60 /
  mount -o remount,commit=60 /home

  # Turn off the laptop mode disk optimization
  echo 0 > /proc/sys/vm/laptop_mode

  # Manually set the wifi driver to no power savings.
  echo 6 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Only wakeup every 60 seconds to see if we need to write dirty pages
  # By default this is every 5 seconds but, I prefer 60 to reduce disk
  # activity.
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs

  # Set video brightness to 100%
  echo 100 > /proc/acpi/video/VID/LCD0/brightness
  echo 100 > /proc/acpi/video/VID1/LCD0/brightness

  # Turn off sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  
  # Set the SATA to max performance
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Enable the webcam driver
  modprobe uvcvideo

  # Optional: Put back most of the bluetooth/usb subsystem
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd

  # Use default on AC
  echo default > /sys/module/pcie_aspm/parameters/policy

else # Save power

  # Set the disks to aggressively save power and use the lowest acoustic
  # level.  Some might find these settings too aggressive.  If so, change 
  # "-S 4" to something larger like -S 24 (two minutes) and -B 1 to -B 255.
  hdparm -B 1 -S 4 -M 128 /dev/sda
  
  # Change the ext3 commit times to 10 minutes.  This reduces disk
  # activity
  mount -o remount,commit=600 /

  # Set laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945 driver to power savings.
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Set video brightness to 40%
  echo 40 > /proc/acpi/video/VID/LCD0/brightness
  echo 40 > /proc/acpi/video/VID1/LCD0/brightness

  # Set sound card power savings
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  # Set SATA to minimum power
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Remove the webcam driver
  modprobe -r uvcvideo

  # Optional: Remove the most of the bluetooth/usb subsystem
  modprobe -r hci_usb
  modprobe -r rfcomm
  modprobe -r l2cap
  modprobe -r bluetooth
  modprobe -r usbhid
  modprobe -r uhci_hcd
  modprobe -r ehci_hcd

  # Use powersave on battery
  echo powersave > /sys/module/pcie_aspm/parameters/policy
fi
```

Thanks again! :P

---

### Post by nwadams on 2009-03-11
```
#!/bin/bash

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then
  # Set the drive to mostly stay awake.  Some may want to change -B 200
  # to -B 255 to avoid accumulating Load_Cycle_Counts
  hdparm -B 200 -S 240 -M 254 /dev/sda

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  mount -o remount,commit=60 /
  mount -o remount,commit=60 /home

  # Turn off the laptop mode disk optimization
  echo 0 > /proc/sys/vm/laptop_mode

  # Manually set the wifi driver to no power savings.
  echo 6 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Restore TX power to default 27 dBm
  iwconfig wlan0 txpower 27

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Only wakeup every 60 seconds to see if we need to write dirty pages
  # By default this is every 5 seconds but, I prefer 60 to reduce disk
  # activity.
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs

  # Turn off sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  
  # Set the SATA to max performance
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  
  # Manually set the wifi driver to no power savings.
  echo 6 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Enable the webcam driver
  modprobe uvcvideo

  # Use default on AC
  echo default > /sys/module/pcie_aspm/parameters/policy

#re-enable hal polling for cdrom on AC
hal-disable-polling --device /dev/cdrom --enable-polling

else # Save power

  # Set the disks to aggressively save power and use the lowest acoustic
  # level.  Some might find these settings too aggressive.  If so, change 
  # "-S 4" to something larger like -S 24 (two minutes) and -B 1 to -B 255.
  #using 200 to decrease load cycle increase rate. Also manually adjusting to 128 or 1
  #if i'm in a situation where i need extra power/want to protect drive from bumps
  hdparm -B 200 -S 24 -M 128 /dev/sda
  
  # Change the ext3 commit times to 10 minutes.  This reduces disk
  # activity
  mount -o remount,commit=600 /
  mount -o remount,commit=600 /home

  # Set laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945 driver to power savings.
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Lower TX power from default 27 dBm to 7 dBm
  iwconfig wlan0 txpower 7

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Set sound card power savings
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  # Set SATA to minimum power
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Remove the webcam driver
  modprobe -r uvcvideo

  # Use powersave on battery
  echo powersave > /sys/module/pcie_aspm/parameters/policy

#disable hal polling for cd rom
hal-disable-polling --device /dev/cdrom

fi
```

There's my setup. Any advice on how to make it better. Will the PCI-e power save mode help me if i have the intel x3100 graphics chip or does it only help for the nvidia.

With the setup i have now i figure i'll be able to get around 6-7 hours. which is near what I get with vista. (more though). when i run power top, it still asks me to powersave the sata module even though it is in my script...

Also my wifi power saving is not re-enabling after i resume from a suspend. I was hoping someone would be able to tell me how to fix it
Thanks for any help you can provide

---

### Post by moutou on 2009-04-05
hola!

my xps m1330 has:

processor: T8100
graphic card: 8400M GS
hard disk: 160GB 5400rpm
LCD display: ULTRASHARP WXGA
wireless card: INTEL WIRELESS N
battery: 6 CELLS


i installed ubuntu intrepid and applied the above changes:


[http://ubuntuforums.org/showthread.php?t=539365&highlight=fan+ventilation](http://ubuntuforums.org/showthread.php?t=539365&highlight=fan+ventilation)

it made the fan to operate just a bit, and there are few times that is needed to go to higher speed...my usual operating temperatures are around 50 degrees, and a few times around 60


[http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)

i also needed to add the nvidia-power.sh to my start up programs and now is almost always at performance level 0, and goes higher if needed


[http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

this guide :) ...i installed the 99-savings and 99-nvidia scripts and turned off my bluetooth from bios...my battery indicator shows 1hous50minutes, my powertop -d -t 60 output shows 2hours10minutes...and my consuption with firefox with 4 tabs, skype, nvidia-settings, calculator and a few other programs running is 17.2Watt, and without them is 15.5Watt...


before i do all these changes my consumption was 25Watt...
i have the impression that i am more than satisfied :)
but is there anything else i could do?
i mean, everything looks to operate fine, but for example, how can i disable this biometric fingerprint reader that i never use?
or the 56k modem?...and will i get any results by doing this?

thanks a lot!

---

### Post by sdennie on 2009-04-06
Hola

> **moutou said:**
> 
this guide :) ...i installed the 99-savings and 99-nvidia scripts and turned off my bluetooth from bios...my battery indicator shows 1hous50minutes, my powertop -d -t 60 output shows 2hours10minutes...and my consuption with firefox with 4 tabs, skype, nvidia-settings, calculator and a few other programs running is 17.2Watt, and without them is 15.5Watt...


When powertop was released a huge number of popular apps were patched to reduce CPU wakeups while idle.  I always have at least 20 windows open and while the apps are idle they have no appreciable effect on power savings.  That's not true for all apps though.  For example, leaving applications that use the sound card on can sometimes prevent the sound card from power savings (skype may be that way too) and leaving some web pages open in Firefox can prevent the CPU staying in the deepest sleep mode.


> 
before i do all these changes my consumption was 25Watt...
i have the impression that i am more than satisfied :)
but is there anything else i could do?
i mean, everything looks to operate fine, but for example, how can i disable this biometric fingerprint reader that i never use?
or the 56k modem?...and will i get any results by doing this?

thanks a lot!

I'm glad the instructions worked for you.  The fingerprint reader is a USB device so, if you are removing the USB modules on power savings, it should be powered down.  I'm not sure about the modem though because I don't have one.

Saludos.

---

### Post by nick_edwards on 2009-04-08
I wish I had found this earlier this is brilliant.

I am having trouble with my webcam and fingerprint reader though

in my 99-savings script I have:
> 
  # Remove the webcam driver
  modprobe -r uvcvideo

  # Remove fingerprint driver
  modprobe -r uinput

however I still get in my powertop:

> A USB device is active 100.0% of the time:
USB device  7-6 : Laptop Integrated Webcam (OmniVision Technologies, Inc. -7670-07.09.28.1)

Suggestion: Enable USB autosuspend by pressing the U key or adding 
usbcore.autosuspend=1 to the kernel command line in the grub config

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Disable 'hal' from polling your cdrom with:  
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

Recent USB suspend statistics
Active  Device name
100.0%	USB device  6-1 : Biometric Coprocessor (STMicroelectronics)
100.0%	USB device  7-6 : Laptop Integrated Webcam (OmniVision Technologies, Inc. -7670-07.09.28.1)
100.0%	USB device usb7 : EHCI Host Controller (Linux 2.6.27-14-generic ehci_hcd)
100.0%	USB device usb6 : UHCI Host Controller (Linux 2.6.27-14-generic uhci_hcd)
  0.0%	USB device usb5 : UHCI Host Controller (Linux 2.6.27-14-generic uhci_hcd)
  0.0%	USB device usb4 : UHCI Host Controller (Linux 2.6.27-14-generic uhci_hcd)
  0.0%	USB device usb3 : EHCI Host Controller (Linux 2.6.27-14-generic ehci_hcd)
  0.0%	USB device usb2 : UHCI Host Controller (Linux 2.6.27-14-generic uhci_hcd)
  0.0%	USB device usb1 : UHCI Host Controller (Linux 2.6.27-14-generic uhci_hcd)


I can fix this by removing the usb drivers with:

>  # Remove usb drivers
  sudo modprobe -r uhci_hcd
  sudo modprobe -r ehci_hcd

but then I can't use the usb ports 

any suggestions

---

### Post by cyprusxr3 on 2009-04-26
Has anyone had success with this in Jaunty? It seems that the power.d and sleep.d directories no longer cause scripts to execute (see [this thread]("http://ubuntuforums.org/showthread.php?p=7154219"), "/etc/acpi/ac.d", etc may now work).

It also seems that my minimum power is up from 11W to 15W under jaunty. I'm not sure yet if this is caused by parts of the scripts not working or other changes. How are everyone else's experiences?

---

### Post by TylerMD on 2009-04-27
What happened to me after updating to Jaunty is that suspend wasn't working. After removing this script started to work fine.

---

### Post by Axx83 on 2009-04-27
same to me

if I put the script in /etc/pm/sleep.d the notebook can't suspend anymore, if I remove it everything is fine

---

### Post by cyprusxr3 on 2009-04-27
> **TylerMD said:**
> What happened to me after updating to Jaunty is that suspend wasn't working. After removing this script started to work fine.

I didn't even notice til you mentioned it. Same result for me. After you removed the script from sleep.d, did you notice whether the one in power.d was still working?

You can test by doing something like ```
cat /proc/sys/vm/laptop_mode
```
On AC it should be 10, on battery it should be 90.

It seems my modifications were not complete, as it works correctly on AC/battery switch, but not after resuming from sleep.

---

### Post by crazy2k on 2009-05-30
Isn't there any program that takes care of all this tuning? I mean, not something like powertop that gives you (pretty good, as far as I tested) suggestions, but something that tunes everything automatically according to my preferences.

---

### Post by Axx83 on 2009-05-30
> **crazy2k said:**
> Isn't there any program that takes care of all this tuning? I mean, not something like powertop that gives you (pretty good, as far as I tested) suggestions, but something that tunes everything automatically according to my preferences.

the latest Laptop-mode does that flawlessly. Follow my guide here:

[http://ubuntuforums.org/showpost.php?p=7271995&postcount=7]("http://ubuntuforums.org/showpost.php?p=7271995&postcount=7")

---

### Post by iggykoopa on 2009-05-30
you could use wattospm, heres the thread on it [http://ubuntuforums.org/showthread.php?t=988309&highlight=power+management+gui](http://ubuntuforums.org/showthread.php?t=988309&highlight=power+management+gui) . It does all this stuff automatically(well you have to check a couple checkboxes)

---

### Post by NESFreak on 2009-06-10
> **Axx83 said:**
> the latest Laptop-mode does that flawlessly. Follow my guide here:
[http://ubuntuforums.org/showpost.php?p=7271995&postcount=7]("http://ubuntuforums.org/showpost.php?p=7271995&postcount=7")
[COLOR="SlateGray"]
laptopmode makes my harddisk spin up so often, i'm afraid it will kill it, apart from that, power consumption also goes up from 17watt all the way to 34 according to powertop. On top of all of that there's the delay whenever you click something, cause your harddrive has to spinup first.

Laptopmode is completely ignorant of my changes to /etc/laptop-mode/laptop-mode.conf
[/COLOR]
---nevermind----


i'd love to see this thread updated for jaunty.

---

### Post by Axx83 on 2009-06-10
try setting 255 for hard drive -b value (it's in the conf) and see if that works, if not submit a bug @ launchpad

---

### Post by sdennie on 2009-06-10
> **NESFreak said:**
> laptopmode makes my harddisk spin up so often, i'm afraid it will kill it, apart from that, power consumption also goes up from 17watt all the way to 34 according to powertop. On top of all of that there's the delay whenever you click something, cause your harddrive has to spinup first.

Laptopmode is completely ignorant of my changes to /etc/laptop-mode/laptop-mode.conf

i'd love to see this thread updated for jaunty.

The guide only depends on a properly working interaction between acpid and pm-utils so, it should work for any modern distro.  I'm using it unmodified on a distro I built from scratch and, as long as acpid is notifying pm-utils of battery state changes, it works fine.

> **Axx83 said:**
> try setting 255 for hard drive -b value (it's in the conf) and see if that works, if not submit a bug @ launchpad

I'm fairly sure setting -B255 will disable the disk spinning down at all but, it's not something I've tried.

---

### Post by NESFreak on 2009-06-17
> **sdennie said:**
> 

I'm fairly sure setting -B255 will disable the disk spinning down at all but, it's not something I've tried.

thanks, the only thing i did was setting LM_BATT_HD_IDLE_TIMEOUT_SECONDS to something incredibly large. 

-B was set to 1 which i changed to 128. Which is its lowest powerconsumptionmode without spinning down.

---

### Post by mikewhatever on 2009-07-27
I've been trying to make the script work on a custom 9.04 installation for a few days, but to no avail. It's a command line install with LXDE and a bunch of programs. I've verified both acpid and pm-utils are installed, but the script is not executed when the power cord gets unplugged, nor is it on startup. What should I be looking for?

---

### Post by e24ohm on 2009-08-24
thanks for the post, this has really helped out my battery life.

---

### Post by mjwalfredo on 2009-08-27
So I just got this to work on my 9.04 installation.  The problem with 9.04 is that power.sh, the script that runs when you plugin / unplug your ac adapter, only executes scripts that have the .sh extension in the filename.

So I just changed 99-savings to 99-savings.sh and viola.


I am still having one problem though. Something else is setting the laptop_mode to level 2.  I just realized that I have laptop-mode-tools installed.  I am going to uninstall that package to see if that fixes the problem.


Edit:  After uninstalling laptop-mode-tools I discovered that these scripts and laptop-mode-tools are both trying to solve the same problem.  These scripts are nice because they have been configured to save power very nicely.  However, I think I am going to try to work all of the suggestions into the laptop-power-tools configuration.

---

### Post by vall on 2009-10-18
Hello,

I have a Sony laptop and I am trying to apply this ideas from this tread to extend the running the battery, but I don't have much success. I am running Fedora 11 64-bit, but I guess the ideas here ate distro-independent. 

Here are some details of the laptop.


Sony Vaio SR49VN/H
13.3" LED screen
 Intel(R) Core(TM)2 Duo CPU     P8800  @ 2.66GHz
4GiB RAM
400GB HTT Toshiba
ATI Mobility Radeon HD 3470
Intel Wireless WiFi Link 5100
SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller 


Here is my script and I checked that it executes correctly when unplug and plug the AC power. So it is doing what is it supposed to.


```

#!/bin/bash
if on_ac_power; then
# Reset back to normal settings

  # Set the drive to mostly stay awake
  hdparm -B 200 -S 240 -M 254 /dev/sda


  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  mount -o remount,commit=60 /


  echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
  echo 0 > /proc/sys/vm/laptop_mode
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs
  # Set sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  echo default > /sys/module/pcie_aspm/parameters/policy

  # Manually set the wifi driver to no power savings.
  echo 6 > /sys/bus/pci/drivers/iwl???/*/power_level
  # Restore TX power to default 27 dBm
  iwconfig wlan0 txpower 27




  ethtool -s eth0 wol g        #enable wake up on lan
  ethtool -s eth0 autoneg on speed 1000     #set speed normaal, autoneg on


  for i in /sys/class/scsi_host/*/link_power_management_policy
  do echo max_performance > $i
  done

  for i in /sys/devices/system/cpu/cpu?/cpufreq/scaling_governor
  do echo ondemand > $i
  done


  modprobe uvcvideo
  /etc/init.d/bluetooth start >> /dev/null
  modprobe -r uinput
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd

  hal-disable-polling --enable-polling --device /dev/scd0  >> /dev/null

  echo "  Enabling USB auto suspend"
  # Auto Suspend Unused USB Buses (Timeout in seconds)
  for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 2 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
  done


else
# Turn on aggressive power savings

  # Set the disks to aggressively save power and use the lowest acoustic
  # level.  Note: Currently Firefox is very poorly behaved and some
  # might find these settings too aggressive.  If so, change "-S 4" to
  # something larger like -S 24 (two minutes).
  
  hdparm -B 1 -S 60 -M 128 /dev/sda

  # Change the ext3 commit times to 10 minutes.  This reduces disk
  # activity
  mount -o remount,commit=600 /


  echo 5 > /proc/sys/vm/laptop_mode
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs
  
  echo "  Enabling MC power saving scheduler"
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings

  echo "  Lowering WiFi power level"
  iwconfig wlan0 power off
  echo 5 > /sys/bus/pci/drivers/iwl???/*/power_level 
  # Lower TX power from default 27 dBm to 7 dBm
  iwconfig wlan0 txpower 7


  ethtool -s eth0 wol d        #disable wake up on lan
  ethtool -s eth0 autoneg off speed 100     #set speed minder, autoneg off

  # Set sound card power savings

  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  echo powersave > /sys/module/pcie_aspm/parameters/policy
  
  for i in /sys/class/scsi_host/*/link_power_management_policy
  do echo min_power > $i
  done

  for i in /sys/devices/system/cpu/cpu?/cpufreq/scaling_governor
  do echo ondemand > $i
  done


  modprobe -r uvcvideo
  /etc/init.d/bluetooth stop >> /dev/null
  modprobe -r uinput
  modprobe -r hci_usb
  modprobe -r rfcomm
  modprobe -r l2cap
  modprobe -r bluetooth
  modprobe -r usbhid
  modprobe -r uhci_hcd
  modprobe -r ehci_hcd

  hal-disable-polling --device /dev/scd0  >> /dev/null
  
  echo "  Enabling USB auto suspend"
  # Auto Suspend Unused USB Buses (Timeout in seconds)
  for i in /sys/bus/usb/devices/usb?/power/autosuspend
    do echo 2 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/usb?/power/level
    do echo auto > $i
  done
    
fi
```

However, according the PowerTop and Gnome Power Manager there is no effect on how long I can run on battery. It is always ~2:30h. Here is the output from Powertop and running on battery, but with the AC power setting from the script:

```

$ sudo powertop -d -t 60
[sudo] password for vall: 
PowerTOP 1.11   (C) 2007, 2008 Intel Corporation 

Collecting data for 60 seconds 


Cn              Avg residency
C0 (cpu running)        ( 1.2%)
C0          0.0ms ( 0.0%)
C1 mwait      0.0ms ( 0.0%)
C2 mwait      0.5ms ( 0.2%)
C4 mwait     19.8ms (98.6%)
P-states (frequencies)
  2.67 Ghz     1.0%
  2.67 Ghz     0.0%
  2.14 Ghz     0.0%
  1.60 Ghz     0.0%
   800 Mhz    99.0%
Wakeups-from-idle per second : 54.3    interval: 60.0s
Power usage (ACPI estimate): 18.7W (2.2 hours) 
Top causes for wakeups:
  33.9% ( 31.6)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
  14.2% ( 13.2)     <kernel core> : hrtimer_start (tick_sched_timer) 
  14.0% ( 13.0)      <kernel IPI> : Rescheduling interrupts 
  11.5% ( 10.8)       <interrupt> : iwlagn 
   9.8% (  9.1)    sensors-applet : __mod_timer (process_timeout) 
   7.9% (  7.3)       <interrupt> : acpi 
   2.0% (  1.9)              hald : __mod_timer (process_timeout) 
   2.0% (  1.9)   devkit-power-da : __mod_timer (process_timeout) 
   0.6% (  0.5)      <kernel IPI> : Function call interrupts 
   0.6% (  0.5)    sensors-applet : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.5% (  0.5)              phy0 : __mod_timer (ieee80211_sta_timer) 
   0.3% (  0.3)      clock-applet : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.3)   gnome-screensav : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.2)       gnome-panel : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.2)     <kernel core> : __mod_timer (neigh_periodic_timer) 
   0.3% (  0.2)   gpk-update-icon : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.2)   <kernel module> : __mod_timer (neigh_periodic_timer) 
   0.2% (  0.2)       <interrupt> : ahci 
   0.2% (  0.2)    NetworkManager : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.1)   gnome-power-man : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)      work_for_cpu : __mod_timer (sta_info_cleanup) 
   0.1% (  0.1)        kerneloops : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)              mono : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)     <kernel core> : __mod_timer (neigh_timer_handler) 
   0.1% (  0.1)    gnome-terminal : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)           audispd : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)              Xorg : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)              hald : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)          gconfd-2 : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)   devkit-power-da : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)       <interrupt> : uhci_hcd:usb3, radeon@pci:0000:01:00.0, firewire_ohci 
   0.0% (  0.0)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer) 
   0.0% (  0.0)     <kernel core> : __mod_timer (death_by_timeout) 
   0.0% (  0.0)     <kernel core> : __mod_timer (peer_check_expire) 
   0.0% (  0.0)     <kernel core> : __mod_timer (wb_timer_fn) 
   0.0% (  0.0)           async/1 : __mod_timer (blk_rq_timed_out_timer) 
   0.0% (  0.0)   gdm-session-wor : __mod_timer (commit_timeout) 
   0.0% (  0.0)             crond : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)             mount : __mod_timer (commit_timeout) 
   0.0% (  0.0)     <kernel core> : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.0)            auditd : __mod_timer (process_timeout) 
   0.0% (  0.0)          rsyslogd : hrtimer_start_range_ns (hrtimer_wakeup) 

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Recent USB suspend statistics
Active  Device name
  0.0%    USB device  3-1 : Fingerprint Sensor    (TouchStrip        )
  0.0%    /sys/bus/usb/devices/1-2
  0.0%    USB device usb8 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb7 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb6 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb5 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb4 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb3 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb2 : EHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 ehci_hcd)
  0.0%    USB device usb1 : EHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 ehci_hcd)

```

and here is what comes out when on battery with the power saving settings from the scripts:

```

$ sudo powertop -d -t 60
PowerTOP 1.11   (C) 2007, 2008 Intel Corporation 

Collecting data for 60 seconds 


Cn              Avg residency
C0 (cpu running)        ( 1.1%)
C0          0.0ms ( 0.0%)
C1 mwait      0.0ms ( 0.0%)
C2 mwait      0.6ms ( 0.3%)
C4 mwait     21.9ms (98.6%)
P-states (frequencies)
  2.67 Ghz     1.1%
  2.67 Ghz     0.0%
  2.14 Ghz     0.0%
  1.60 Ghz     0.1%
   800 Mhz    98.8%
Wakeups-from-idle per second : 49.8    interval: 60.0s
Power usage (ACPI estimate): 18.0W (2.0 hours) 
Top causes for wakeups:
  34.9% ( 29.8)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
  13.7% ( 11.7)     <kernel core> : hrtimer_start (tick_sched_timer) 
  12.5% ( 10.7)      <kernel IPI> : Rescheduling interrupts 
  12.3% ( 10.4)       <interrupt> : iwlagn 
   8.5% (  7.2)    sensors-applet : __mod_timer (process_timeout) 
   7.4% (  6.3)       <interrupt> : acpi 
   2.2% (  1.9)   devkit-power-da : __mod_timer (process_timeout) 
   2.2% (  1.9)              hald : __mod_timer (process_timeout) 
   1.3% (  1.1)       <interrupt> : ahci 
   0.6% (  0.5)      <kernel IPI> : Function call interrupts 
   0.6% (  0.5)    sensors-applet : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.6% (  0.5)              phy0 : __mod_timer (ieee80211_sta_timer) 
   0.3% (  0.3)      clock-applet : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.2)     <kernel core> : __mod_timer (neigh_periodic_timer) 
   0.3% (  0.2)   gpk-update-icon : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.2)   <kernel module> : __mod_timer (neigh_periodic_timer) 
   0.3% (  0.2)   gnome-screensav : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.3% (  0.2)       gnome-panel : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.2)    NetworkManager : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.1)   gnome-power-man : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.2% (  0.1)       packagekitd : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)              mono : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)      work_for_cpu : __mod_timer (sta_info_cleanup) 
   0.1% (  0.1)        kerneloops : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)     <kernel core> : __mod_timer (laptop_timer_fn) 
   0.1% (  0.1)    gnome-terminal : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.1% (  0.1)   gdm-session-wor : __mod_timer (commit_timeout) 
   0.1% (  0.1)           audispd : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)              Xorg : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)           async/1 : __mod_timer (blk_rq_timed_out_timer) 
   0.0% (  0.0)     <kernel core> : __mod_timer (neigh_timer_handler) 
   0.0% (  0.0)   devkit-power-da : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)              hald : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)          gconfd-2 : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   0.0% (  0.0)       <interrupt> : uhci_hcd:usb3, radeon@pci:0000:01:00.0, firewire_ohci 
   0.0% (  0.0)             crond : hrtimer_start_range_ns (hrtimer_wakeup) 
   0.0% (  0.0)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer) 
   0.0% (  0.0)     <kernel core> : __mod_timer (death_by_timeout) 
   0.0% (  0.0)     <kernel core> : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.0)     <kernel core> : __mod_timer (peer_check_expire) 
   0.0% (  0.0)            auditd : __mod_timer (process_timeout) 
   0.0% (  0.0)          rsyslogd : hrtimer_start_range_ns (hrtimer_wakeup) 

Recent USB suspend statistics
Active  Device name
  0.0%    USB device  3-1 : Fingerprint Sensor    (TouchStrip        )
  0.0%    /sys/bus/usb/devices/1-2
  0.0%    USB device usb8 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb7 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb6 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb5 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb4 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb3 : UHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 uhci_hcd)
  0.0%    USB device usb2 : EHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 ehci_hcd)
  0.0%    USB device usb1 : EHCI Host Controller (Linux 2.6.30.8-64.fc11.x86_64 ehci_hcd)


```
As you see the power consumption is nearly the same, but almost everyone here reports quite of a drop of the consumption when usign the optimized settings. Any idea what I am doing wrong? Any help will be much appreciated.

I've tried to control the fan speeds according thr CPU temperature, but I can't do that. lm-sensors detects only the CPU temperarture and nothing else and PWMconfig says it can't change the fan speed. So, the fans are always on and constant speed, but I doubt this can be the problem.

Also, I have not been able to run the ATI Mobility Radeon HD 3400 Series driver, instead, I use the generic Radeon driver.

---

### Post by nwadams on 2009-10-19
> **mikewhatever said:**
> I've been trying to make the script work on a custom 9.04 installation for a few days, but to no avail. It's a command line install with LXDE and a bunch of programs. I've verified both acpid and pm-utils are installed, but the script is not executed when the power cord gets unplugged, nor is it on startup. What should I be looking for?

the location that you have to place the scripts has changed since 8.04. I believe you have to put them in /etc/acpi/*.d (but i may be wrong)

---

### Post by cong06 on 2009-12-24
I'm using karmic 9.10, and I wrote the script, tried several different directories to no avail. I also tried adding a "*.sh" extension.

Then I ran the "pm-powersave" program, and it seems that every time this tool is run, the files in /etc/pm/power.d etc. are run. In my case it had nothing to do with the extension.

---

### Post by cong06 on 2009-12-28
I think there's a bug in the "/etc/acpi/power.sh" file. I commended out all the lines except for the "pm-powersave $*" line, and my script started working (in /etc/pm/power.d)

[http://ubuntuforums.org/showpost.php?p=8569808&postcount=33](http://ubuntuforums.org/showpost.php?p=8569808&postcount=33)

---

### Post by mattkerle on 2010-05-18
great HOWTO!

quick thing, the power save script won't really work if you have multiple CPUs as it only changes cpu0 in the script. I have 8 cpus so still chew heaps of power.. :-( 

in 99-savings, find the line:
```
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
```

and replace it with this:
```
  for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
  do
     [ -f $CPUFREQ ] || continue
     echo -n ondemand > $CPUFREQ
  done
```

then try unplugging and plugging. I've got a Dell XPS studio with 9 cells and my battery applet currently reports 5hours life!! up from 4hours odd it reported previsously. cheers!

---

### Post by Ivkosky on 2010-06-19
> For heat (and more particularly noise), I found that really forcing the disk to stay spun down made a big difference.  It's eerie to use a machine that is cool to the touch and silent.  Unfortunately, it's also a massive hassle to set this up right and possibly dangerous as it involves mounting various parts of the system as tmpfs.

Hi

I have a huge problem and since I am total beginner in Ubuntu I am kindly asking for your help.

Since yesterday I encountered really strange behaviour of my Dell M1330 - the fan went terribly noisy and although it was always bit noisier than in Vista, this was something totally out of control... It became so noisy that I was afraid that laptop will explode just in front of me! :( The whole laptop was vibrating. I turned it off immediately. It happened once again since the first time.

I started googling and I found out that nvidia equipped M1330s have problems with overheating. I don't want to switch back to Vista, please help me!*:(

I installed LM sensors and found out that the temperatures are over 60C all the time! :( Especially GPU wich is 65-68C and CPU 63-65C.

I don't know whether this HOWTO can help me reduce a temperature a bit. I don't mind having fans on 100% and a bit noisier all the time, I just don't want to have my laptop crashed. :( I also don't have to tune my system to 100% performance and can lower it if it's possible and helps the situation...

I am a bit afraid to do any changes in Ubuntu now, I would really appreciate any suggestions! Thank you very much!

---

### Post by Alesh666 on 2011-03-20
> **sdennie said:**
> Depending on how you use the machine, with a 9 cell battery, it's possible to get over 6 hours of battery life with an XPS m1330.  This is a guide for the scripts and general tips I've used on my XPS m1330.

**Specs:**
XPS m1330
T9300 CPU
NVidia 8400M GS GPU
7200rpm 200G disk
LED display
Intel 3945 wireless
9 cell battery

**Basic scripts**

[Edit] 
.................................................

-

I hope that helps.

Hello,
i have Dell Studio XPS 1340 and Ubuntu 10.10, do you think, that I can use your script, as it is written? 
I tried to use your script which is in topic HOWTO: Improve battery life on laptop and it worked, but I had a little problem with my hard drive, because it sleeped most of time and when I was doing anything, for example only surfing the internet, it freezed for a second and I could hear that disk is starting to rotate and after that a i could do something. But during it disk fall asleep and when i clicked something, i had to wait again. Is here some solution how to improve this?
Thank you for your answer.

---

### Post by lawrencejohny on 2011-07-27
> **sdennie said:**
> Depending on how you use the machine, with a 9 cell battery, it's possible to get over 6 hours of battery life with an XPS m1330.  This is a guide for the scripts and general tips I've used on my XPS m1330.

**Specs:**
XPS m1330
T9300 CPU
NVidia 8400M GS GPU
7200rpm 200G disk
LED display
Intel 3945 wireless
9 cell battery

**Basic scripts**

[Edit] 
Several other people have written scripts in this thread and some of them have more options or go about doing things a different way.  There are many ways to do what I'm trying to accomplish and the other scripts are worth looking at once you've looked through this post and understand the basic idea of what's going on.  I'll link to them here so that people don't have to wade through the entire thread to find them:

- [atlas95s script]("http://ubuntuforums.org/showpost.php?p=5310874&postcount=4")
- [tinivoles script]("http://ubuntuforums.org/showpost.php?p=5319346&postcount=8")
- [motins script]("http://ubuntuforums.org/showpost.php?p=5380689&postcount=40")
- [bubbalouies script]("http://ubuntuforums.org/showpost.php?p=5390336&postcount=45")
[/Edit]

The first script is similar to laptop-mode but with tips from powertop and [www.lesswatts.org](www.lesswatts.org).  It's possible to use laptop-mode and make this script smaller but, my personal preference is to have everything in one place.  Here is the main script:

```

#!/bin/bash

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then
  [B]# Set the drive to mostly stay awake.  Some may want to change -B 200
  # to -B 255 to avoid accumulating Load_Cycle_Counts[/B]
  hdparm -B 200 -S 240 -M 254 /dev/sda

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  mount -o remount,commit=60 /
  mount -o remount,commit=60 /home

  # Turn off the laptop mode disk optimization
  echo 0 > /proc/sys/vm/laptop_mode

  # Manually set the wifi driver to no power savings.
  echo 6 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Only wakeup every 60 seconds to see if we need to write dirty pages
  # By default this is every 5 seconds but, I prefer 60 to reduce disk
  # activity.
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs

  # Turn off sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  
  # Set the SATA to max performance
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Enable the webcam driver
  modprobe uvcvideo

else # Save power

  [B]# Set the disks to aggressively save power and use the lowest acoustic
  # level.  Some might find these settings too aggressive.  If so, change 
  # "-S 4" to something larger like -S 24 (two minutes) and -B 1 to -B 255.[/B]
  hdparm -B 1 -S 4 -M 128 /dev/sda
  
  # Change the ext3 commit times to 10 minutes.  This reduces disk
  # activity
  mount -o remount,commit=600 /

  # Set laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945 driver to power savings.
  echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level  

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Set sound card power savings
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  # Set SATA to minimum power
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Remove the webcam driver
  modprobe -r uvcvideo
fi

```

Most these settings come from powertop/www.lesswatts.org but, some of them are using different values.  To install this script on Hardy, name it 99-savings and use:

```

sudo install 99-savings /etc/pm/sleep.d
sudo install 99-savings /etc/pm/power.d

```

To install it on Gutsy, use:

```

sudo install 99-savings /etc/acpi/start.d
sudo install 99-savings /etc/acpi/resume.d
sudo install 99-savings /etc/acpi/ac.d
sudo install 99-savings /etc/acpi/battery.d

```

**NVidia and compiz**
If you don't have an NVidia card (this is only tested on an 8400M GS in fact), and you aren't using compiz, this section propably won't be of any use to you.  

First, I recommend using this tutorial to get good compiz performance on AC and good power savings on battery: [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)

Then, we will set it up so that the NVidia driver uses as little power as possible.  First, edit /etc/X11/xorg.conf and find the section that describes the nvidia card.  You may have customized it in the past but, be sure it at least contains the following information:

```

Section "Device"
    Driver    "nvidia"
    Option    "OnDemandVBlankInterrupts" "True"

```

Now we will install a script that does 2 things: 1) Turns of sync to vblank when the machine is on battery power. 2) Changes the compiz Wall plugin to use a lower value.  This means that you can switch desktops without forcing the GPU into maximum power (it saves a lot of power).

```

#!/bin/bash

[b]
# Change this to your user name
XUSER=your_username
[/b]

if on_ac_power; then
  # Set vblank to on when on AC power
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 1"

  # Change wall switch time to default
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type float --set /apps/compiz/plugins/wall/allscreens/options/slide_duration 0.3"

  # Touch the nvidia card so it immediately goes to full power when we
  # plug the machine in
  DISPLAY=:0.0 su ${XUSER} -c "nvidia-settings -q all > /dev/null"

else

  # Turn off sync to vblank when on battery power so we reduce the nvidia
  # wakeups
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 0"
  
  # Set the wall slide duration much lower to prevent it from forcing the
  # card into full power
  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type float --set /apps/compiz/plugins/wall/allscreens/options/slide_duration 0.1"
fi

```

Depending on what plugins you use, you may want to add even more values to that to prevent compiz from forcing the GPU to max power as often.  To find the names/values of particular features, use gconf-editor and go to /apps/compiz.  To install that script, name it 99-nvidia and do the following on Hardy:

```

sudo install 99-nvidia /etc/pm/sleep.d
sudo install 99-nvidia /etc/pm/power.d

```

On Gutsy:

```

sudo install 99-nvidia /etc/acpi/start.d
sudo install 99-nvidia /etc/acpi/resume.d
sudo install 99-nvidia /etc/acpi/ac.d
sudo install 99-nvidia /etc/acpi/battery.d

```

**General**

- If you never use bluetooth, I recommend going into the BIOS and setting the wifi/bluetooth switch on the laptop to only control Bluetooth and then leaving that switch off at all times.

- If you never use the webcam, it may be sufficient to just modprobe -r uvcvideo however, I haven't thoroughly checked this out.  It may be best to completely blacklist the driver but, I'm not sure if that setting sticks between suspend/resume so, you may have to delete the driver (make a backup of it first).

- If you never use USB/Bluetooth while on battery, removing most of the usb and bluetooth subsystem can save a huge amount of power.  In the first section of first script add:

```

  # Optional: Put back most of the bluetooth/usb subsystem
  modprobe  hci_usb
  modprobe  rfcomm
  modprobe  l2cap
  modprobe  bluetooth
  modprobe  usbhid
  modprobe  uhci_hcd
  modprobe  ehci_hcd

```

In the section for battery mode, add:

```

  # Optional: Remove the most of the bluetooth/usb subsystem
  modprobe -r hci_usb
  modprobe -r rfcomm
  modprobe -r l2cap
  modprobe -r bluetooth
  modprobe -r usbhid
  modprobe -r uhci_hcd
  modprobe -r ehci_hcd

```

This can save upwards of 1 watt of power.

- For anyone running the new 2.6.26 kernel, [the PCI Express power savings]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=7d715a6c1ae5785d00fb9a876b5abdfc43abc44b") seems to save a huge amount of power (about 0.7W).  The commands to do this are:

```

# Use default on AC
echo default > /sys/module/pcie_aspm/parameters/policy

```

And, on battery:

```

# Use powersave on battery
echo powersave > /sys/module/pcie_aspm/parameters/policy

```

There is also a "performance" setting but, it makes the power usage so incredibly high that it can't be what the BIOS is using by default so I'm not willing to use it.

- Do *not* leave a firefox tab open with things like gmail while on battery power.  If at all possible, close all tabs but one and try to keep to sites that are light on javascript and try to stay away from anything with flash.

- If you find the disk spinning up too often, try:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"
tail -f /var/log/syslog

```

Then, to turn that functionality off:
```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

Wait for a while and see if you can figure out what application is causing the disk to wakeup too often.  The script above reduces the number of wakeups due to writes but, reads can still cause the disk to wakeup.

- Do *not* use virtual machines while on battery power.  They will drain the battery very quickly.

- I'm currently testing whether turning off the Firefox disk cache will keep the disk suspended for longer amounts of time (the theory being the disk won't wakeup to read the cached files).  It's hard to tell if it's making a difference but, to try it, type "about:config" in Firefox and search for cache and you can turn off the disk cache.

- Use powertop and top in conjunction with each other in two different windows to see if you have any misbehaving applications.  If possible, put them in small windows that stay on top (maybe reduce the font size too) and keep an eye on both while going about your normal work.

- Use the ondemand governor and not the powersave governor.  See: [http://mjg59.livejournal.com/88608.html](http://mjg59.livejournal.com/88608.html)

- Keep the backlight as low as you can possibly stand it.  Try to at least keep it at half power or less.  This can save a lot of power.

- Avoid listening music while on battery power.  In fact, don't keep any music applications open while on battery power because many will prevent the sound card from going to sleep.

- For the machine as spec'd above, you should expect idle power consumption in the range of ~12 watts with a handful of apps open.  For example, with Firefox, Pidgin, Nautilus, Evolution and a few terminals running, if I type the following and then walk away from the machine for 1 minute:

```

acpi
sudo powertop -d -t 60

```

The output looks like this on the lowest backlight setting (note that the machine is at 85% battery and not 100% battery in this example):

```

sdennie@zorba:~/src/scripts$ acpi
     Battery 1: discharging, 85%, 06:19:34 remaining
sdennie@zorba:~/src/scripts$ sudo powertop -t 60 -d
PowerTOP 1.9    (C) 2007 Intel Corporation 

Collecting data for 60 seconds 
Cn	          Avg residency
C0 (cpu running)        ( 4.6%)
C1		  0.0ms ( 0.0%)
C2		  0.5ms ( 1.1%)
C3		  5.5ms (94.4%)
P-states (frequencies)
  2.51 Ghz    83.3%
  2.50 Ghz     0.0%
  2.00 Ghz     0.0%
   800 Mhz    16.7%
Wakeups-from-idle per second : 191.3	interval: 60.0s
Power usage (ACPI estimate): 12.1W (6.4 hours) 
Top causes for wakeups:
  63.5% (137.1)      <kernel IPI> : Rescheduling interrupts 
   7.1% ( 15.3)       <interrupt> : iwl3945 
   6.7% ( 14.4)       <interrupt> : extra timer interrupt 
   6.5% ( 14.0)           firefox : futex_wait (hrtimer_wakeup) 
   6.3% ( 13.6)       compiz.real : schedule_timeout (process_timeout) 
...

```

If you are using the 2.6.26 kernel and have enabled PCI Express savings and the machine is very idle, you can expect these numbers to be much lower (as low as 10.3W for me).

I hope that helps.

Does this method work for Lucid Lynx? I have got Dell studio 1555 running Lucid Lynx.

---

### Post by nwadams on 2011-07-27
these instructions are very old. You shouldn't need them any more.

---

