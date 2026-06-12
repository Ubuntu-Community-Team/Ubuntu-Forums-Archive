---
title: "Ubuntu 11.10 on Dell  Studio 1558 (Fan problem)"
date: 2011-10-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JavaPenguin on 2011-10-19
I am running Ubuntu 11.10 on my Dell Studio 1558 laptop.

Everything works, but the fan stays on the whole time. Better than not working at all, but still irritating.

I installed **lm-sensors** and when I run **sensors** I get the following output:

acpitz-virtual-0
Adapter: Virtual device
temp1:        +26.8°C  (crit = +100.0°C)
temp2:         +0.0°C  (crit = +100.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +44.0°C  (high = +95.0°C, crit = +105.0°C)
Core 2:       +44.0°C  (high = +95.0°C, crit = +105.0°C)

radeon-pci-0200
Adapter: PCI adapter
temp1:        +75.5°C 

**fancontrol** gives me:
Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file

and **pwmconfig** gives me:
There are no pwm-capable sensor modules installed

Any help would be appreciated

---

### Post by buddhuu on 2011-10-20
Similar issue here on Acer Aspire 5920 laptop.

---

### Post by bentley4 on 2011-10-21
I have the same problem. Also have a Dell studio 1558 on ubuntu 11.10. Different **solutions** are suggested when you browse the **web**, I tried the following(but still doesn't work for me):
**I. [Update your _bios_]("http://shield008.blogspot.com/2008/12/dell-studio-1535-fan-seed-problem-and.html").**
To see your current bios version on yr laptop, type in terminal:
```
sudo dmidecode -s bios-version
```
Compare this to the last version of the bios update on the dell website.

**II. Add *acpi_osi=\"Linux\""*  &   *acpi.power_nocheck=1* in grub.cfg . as in [_this youtube video_]("http://www.youtube.com/watch?v=uKi1YHAq3wM").**
Check the video description for the step-by-step actions.
I did everything in the video discription => nothing changed.
I even changed *acpi_osi=\"Linux\""* to *acpi_osi="Linux"*(and reupdated grub) as suggested on this thread:
[http://ubuntuforums.org/showthread.php?t=1355341&page=2](http://ubuntuforums.org/showthread.php?t=1355341&page=2)
=> still doesn't work.

**III. Somebody on [_this thread_]("http://forums.techarena.in/hardware-peripherals/1365754.htm") said his friend had it fixed in a local shop and that the problem had something to do with the capacitors.**
=> Not the case with me. I also have a windows 7 partition. The fans and temperature are fine when I run applications in there. So this must mean that **the problem is ubuntu related**(in my case at least).

Does anybody have any clue how this could be fixed??

---

### Post by bobsageek on 2011-10-22
Similar issue here with a Dell 17R (n7110), not unbearably loud but I'd love to get it back under control.

---

### Post by Rackstar on 2011-10-22
Same here, but I think it was in previous ubuntu version too

Also Dell Studio 1558

---

### Post by bentley4 on 2011-10-23
K guys, I solved my problem. Not sure if it will help in your case though:
Go to 'System settings'=>additional drivers.
Then install the 'ATI/AMD proprietary FGLRX graphics driver'.
Reboot after installation. That should do it.
If that doesn't work check this:
_[http://board.blackbuntu.com/thread-786.html]("http://board.blackbuntu.com/thread-786.html")_
After I did that, somehow Xsensors didn't show core temperature for some reason, here's how to make them show again:
[_http://askubuntu.com/questions/54817/xsensors-shows-only-one-temperature_]("http://askubuntu.com/questions/54817/xsensors-shows-only-one-temperature")

---

### Post by madsbola on 2011-11-04
Same issue on Dell Vostro V131.

Anyone filled a bug?

---

### Post by Ansraliant on 2011-11-19
same issue on my 1558. 
Just made a fresh install on oneiric, i don't remember this happening back on Lucid Lynx.

---

### Post by zapotek6 on 2011-11-22
In my dell vostro v131 with ubuntu 11.10 64bit I've partially solved the problem of the fan an incremented the battery autonomy with the following steps gathered from more sites:

############################### KERNEL PARAMETERS ADDED ON GRUB
pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1


############################### SCRIPT
echo CPU Governor
for i in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo -n $i": " ; cat $i;  done
for i in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo powersave > $i; done
for i in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo -n $i": " ; cat $i;  done

echo Link Power Management
for i in /sys/class/scsi_host/host*/link_power_management_policy; do echo -n $i": "; cat $i; done
for i in /sys/class/scsi_host/host*/link_power_management_policy; do echo min_power > $i; done
for i in /sys/class/scsi_host/host*/link_power_management_policy; do echo -n $i": "; cat $i; done

echo WLAN0 Power
iwconfig wlan0 power timeout 750ms
iwconfig wlan0 txpower 3

echo USB Autosuspend
for i in /sys/bus/usb/devices/*/power/autosuspend; do echo -n $i": ";cat $i; done
for i in /sys/bus/usb/devices/*/power/autosuspend; do echo 20 > $i; done
for i in /sys/bus/usb/devices/*/power/autosuspend; do echo -n $i": ";cat $i; done
echo USB Power Level
for i in /sys/bus/usb/devices/*/power/level; do echo -n $i": "; cat $i; done
for i in /sys/bus/usb/devices/*/power/level; do echo auto > $i; done
for i in /sys/bus/usb/devices/*/power/level; do echo -n $i": "; cat $i; done

echo Disable Bluetooth
echo 0 >  /sys/class/bluetooth/hci0/rfkill0/state

---

### Post by madsbola on 2011-11-22
> **madsbola said:**
> Same issue on Dell Vostro V131.

Anyone filled a bug?

I tried installing this [https://launchpad.net/ubuntu/oneiric/+package/thinkfan](https://launchpad.net/ubuntu/oneiric/+package/thinkfan)
via "sudo apt-get install thinkfan" and will post my results soon

/Mads

---

### Post by byb3 on 2012-01-15
> **bentley4 said:**
> K guys, I solved my problem. Not sure if it will help in your case though:
Go to 'System settings'=>additional drivers.
Then install the 'ATI/AMD proprietary FGLRX graphics driver'.
Reboot after installation. That should do it.
If that doesn't work check this:
_[http://board.blackbuntu.com/thread-786.html](http://board.blackbuntu.com/thread-786.html)_
After I did that, somehow Xsensors didn't show core temperature for some reason, here's how to make them show again:
[_http://askubuntu.com/questions/54817/xsensors-shows-only-one-temperature_]("http://askubuntu.com/questions/54817/xsensors-shows-only-one-temperature")


I would like to add this has worked for me as well.  The fan has noticeably quitened since installing the proprietary drivers.  For reference, I am using Linux Mint based on Debian, with the main/contrib and non-free repositories on squeeze.

```

sudo apt-get install fglrx-driver

```

I am also having the issue where my GPU temperature is no longer showing under sensors, I'll have to dig some more.

---

### Post by aminshayegh on 2012-01-16
I have the same problem in Asus N55SF.

---

### Post by bond17_007 on 2012-11-05
> **byb3 said:**
> I would like to add this has worked for me as well.  The fan has noticeably quitened since installing the proprietary drivers.  For reference, I am using Linux Mint based on Debian, with the main/contrib and non-free repositories on squeeze.

```

sudo apt-get install fglrx-driver

```

I am also having the issue where my GPU temperature is no longer showing under sensors, I'll have to dig some more.

I am having the same issue but this solution did not work for me.. i get

$sudo apt-get install fglrx-driver
E: Package 'fglrx-driver' has no installation candidate

infact i have the Intel HD graphics 3000 not the ATI card.

---

