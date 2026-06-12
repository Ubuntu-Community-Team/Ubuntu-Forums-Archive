---
title: "What is usb autosuspend?"
date: 2009-05-26
forum: General Help
---

### Post by cody7002002 on 2009-05-26
After running powerTOP to see where most of my power consumption is taking place it tells me that the top cause of my wakeups is this

36.7% (41.0) <interrupt> : uhci_hcd:usb3, ath

then at the bottom it suggests how to fix that. It says
"enable usb autosuspend by pressing the U key or adding usbcore.autosuspend=1 to the kernel command line in the grub config"

I'd like to know exactly what that means before I enable it. Any info would help =)

---

### Post by 3rdalbum on 2009-05-26
My understanding is that it's a kind of powersaving mode for USB, but apart from that I don't know. It has not caused me any problems yet, and besides: if you pressed the U key and it caused problems, all you'd need to do is restart to get things back to normal. If Powertop changes your settings, it only does so temporarily.

---

### Post by karatedog on 2009-11-29
> **3rdalbum said:**
> My understanding is that it's a kind of powersaving mode for USB, but apart from that I don't know. It has not caused me any problems yet, and besides: if you pressed the U key and it caused problems, all you'd need to do is restart to get things back to normal. If Powertop changes your settings, it only does so temporarily.
Pressing U immediately stops my Logitech VX Nano mouse. I have to pull the wireless receiver out and put it back again.

---

### Post by Rinzwind on 2009-11-29
It is part of the laptop mode settings.

You can set this in /etc/laptop-mode/conf.d/usb-autosuspend.conf:

```

#
# Configuration file for Laptop Mode Tools module usb-autosuspend.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#


###############################################################################
# USB autosuspend settings
# ------------------------
#
# If you enable this setting, laptop mode tools will automatically enable the
# USB autosuspend feature for all devices.
#
###############################################################################

# Enable USB autosuspend feature?
CONTROL_USB_AUTOSUSPEND=1

```
0=off, 1=on

There are more of these config files inside /etc/laptopmode/conf.d
More info on all options: 

man laptop-mode.conf

From what I think I understand:
1. off means that USB is always active.
2. on means USB is deactivated and only activated when a USB device is inserted.

basically it saves battery life to put it on but it would also switch off any usb devices currently attached (like mice) to save powerconsumption.


OH! and lots of the options powertop advices on can be found in those files.
```

ac97-powersave.conf              lcd-brightness.conf
auto-hibernate.conf              sched-mc-power-savings.conf
battery-level-polling.conf       sched-mc-power-savings.conf~
bluetooth.conf                   start-stop-programs.conf
configuration-file-control.conf  terminal-blanking.conf
cpufreq.conf                     usb-autosuspend.conf
dpms-standby.conf                ethernet.conf                    
video-out.conf                   hal-polling.conf                 
wireless-ipw-power.conf          intel-hda-powersave.conf         
wireless-iwl-power.conf          intel-sata-powermgmt.conf
```

---

