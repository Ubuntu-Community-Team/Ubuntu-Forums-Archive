---
title: "System won't go to suspend/standby/hibernate mode"
date: 2009-06-09
forum: General Help
---

### Post by Troublegum on 2009-06-09
Hey,

I need help. My problem is, that when I want the system to go to standby or hibernate mode, all I see is a black screen with a flashing prompt and the fans continue to run with full speed and the computer's power-led indicate it's still turned on (it glows blue when powered on and turns orange when in standby or when powered down. It doesn't do that in Ubuntu). 

So the problem is not that I can't wake the system from suspend. The system won't go to suspend mode in the first place.

When I logout instead choose standby mode from the gdm login screen, I see the following screen:
```
 * Stopping anac(h)ronistic cron anacron           __
```[COLOR=Red]but without the [OK] at the end of the line.[COLOR=Black] 
The system won't go past this point. 


The problem is not the graphic card driver (as often when I do a search for suspend), because the problem also occurs with a freshly installed Ubuntu without restricted graphic card drivers.

My hard- & software:
[/COLOR][/COLOR]
[LIST]
[*]Ubuntu 9.04 32bit, Kernel 2.6.28-11-generic
[*]Asus M3A78-EM mainboard (AMD780G chipset)
[*]Nvidia GeForce 6600 with nvidia driver version 180 (according to the restricted driver manager)
[*]AMD Athlon 5050e
[/LIST]


Any help appreciated. :)

---

### Post by Troublegum on 2009-06-10
Anyone? :)

---

### Post by Lampi on 2009-06-10
make sure you have STR (suspend to ram) activated in your mainboard bios.

---

### Post by Troublegum on 2009-06-10
Suspend mode is set to "auto" in bios. Available options are "s1 (pos) only" and "s3 only". Suspend and hibernate work great in WinXp so I guess the bios settings are okay.

I just disconnected my usb wifi adapter (zyxel g202) and tried again. To my surprise both suspend and hibernate mode worked without problem. With the wifi adapter plugged in it doesnt work. 
 The wifi adapter is a zyxel g202 that ubuntu recognize out of the box, so i did not need to install drivers.

How can i fix that? Sounds like a bug in ubuntu to me.

---

### Post by Lampi on 2009-06-10
no it's not a bug, it's a configuration issue - you need to stop your zyxel services, unload the zyxel kernel modules, then you should be able to STR fine

You need to add some power management rules in /etc/pm/ to do this automatically, like this it will load modules and services again if you return from STR

---

### Post by Troublegum on 2009-06-10
Hi lampi,

thanks for your help. But how do I do that? :confused:

I googled "ubuntu unload kernel modules suspend" and some variants of it, but that didn't provide me with the necessary information. 

/etc/pm/ contains the folder config.d, power.d, sleep.d. sleep.d contains two scripts: 99laptop-mode and action_wpa with the following contents:
```
#!/bin/sh
#
# 99laptop-mode: Re-apply laptop mode tools settings

case "$1" in
    hibernate|suspend)
        # Stopping is not required.
        ;;
    thaw|resume)
        # Make laptop mode tools forcibly re-apply the hardware settings
        # that laptop mode tools applies.            
        if [ -e /usr/sbin/laptop_mode ] ; then
            /usr/sbin/laptop_mode auto force
        fi
        ;;
    *) exit $NA
        ;;
esac
```

and 
```
#!/bin/sh

# Action script to enable/disable wpa-roam interfaces in reaction to
# pm-action or ifplugd events.
#
# Copyright: Copyright (c) 2008, Kel Modderman <kel@otaku42.de>
# License:   GPL-2
#

PATH=/sbin:/usr/sbin:/bin:/usr/bin

if [ ! -x /sbin/wpa_action ]; then
    exit 0
fi

SELF=action_wpa
COMMAND=
IFPLUGD_IFACE=

# pm-action(8) - <action> <suspend method>
#
# On suspend|hibernate, disconnect any wpa-roam managed interfaces,
# reconnect it on resume.

case "${1}" in
        suspend|hibernate)
                COMMAND=disconnect
                ;;
        resume|thaw)
                COMMAND=reconnect
                ;;
esac

if [ -z "$COMMAND" ]; then
    # ifplugd(8) - <iface> <action>
    #
    # If an ifplugd managed interface is brought up, disconnect any
    # wpa-roam managed interfaces so that only one "roaming" interface
    # remains active on the system.

    IFPLUGD_IFACE="${1}"

    case "${2}" in
        up)
            COMMAND=disconnect
            ;;
        down)
            COMMAND=reconnect
            ;;
        *)
            echo "${SELF}: unknown $0 arguments: ${@}" >&2
            exit 1
            ;;
        esac
fi

if [ -z "$COMMAND" ]; then
    echo "${SELF}: unknown arguments: ${@}" >&2
    exit 1
fi

for CTRL in /var/run/wpa_supplicant/*; do
    [ -S "${CTRL}" ] || continue

    IFACE="${CTRL#/var/run/wpa_supplicant/}"

    wpa_action "${IFACE}" check || continue

    if [ "${IFPLUGD_IFACE}" ] && [ "${IFPLUGD_IFACE}" = "${IFACE}" ]; then
        # if ifplugd is managing this interface (not likely but..)
        # do nothing
        continue
    fi

    wpa_cli -i "${IFACE}" "${COMMAND}"
done
```

---

### Post by Lampi on 2009-06-10
oh my... it's been a while I had to do that :D

Well, first make sure to find out what services (daemons, tasks) are bound to your wifi card. You stop these services and unload the modules, then you make a dry-run to see if STR works like it did when you simply unplugged your zyxel.

I guess there is one service bound to your wifi for sure: /etc/init.d/networking  - stop this service.

Maybe that's it already and you don't need to unload the modules - it's worth trying STR.

If it doesn't work you nedd to unload the modules.Use lsmod/dmesg/"modprobe --show-depends" to figure out what kernel modules your zyxel adapter is using. These modules need to be removed with sudo modprobe -r.

Then I'd try again STR - it should work now. And after that you can think about setting up a shell script in /etc/pm to do this steps automatically

---

### Post by Troublegum on 2009-06-10
Hi Lampi,

you've been a great help. Thank you for that! :)

My Zyxel wifi adapter has a Zydas 1211 chipset and lsmod revealed the kernel module "zd1211rw" with it's dependencies "mac80211" and "cfg80211". So I put these commands together to unload everything:

```
/etc/init.d/networking stop
sudo modprobe -r zd1211rw
sudo modprobe -r mac80211
sudo modprobe -r cfg80211
```After that, I can send the pc to suspend and wake up too. :)

I used these to undo the first script:
```
sudo modprobe cfg80211
sudo modprobe mac80211
sudo modprobe zd1211rw
/etc/init.d/networking start
```Now I need to automate that task. I assume it is not enough to just put a new file in /etc/pm/sleep.d?

---

### Post by kerry_s on 2009-06-10
> **Troublegum said:**
> Suspend mode is set to "auto" in bios. Available options are "s1 (pos) only" and "s3 only". Suspend and hibernate work great in WinXp so I guess the bios settings are okay.

I just disconnected my usb wifi adapter (zyxel g202) and tried again. To my surprise both suspend and hibernate mode worked without problem. With the wifi adapter plugged in it doesnt work. 
 The wifi adapter is a zyxel g202 that ubuntu recognize out of the box, so i did not need to install drivers.

How can i fix that? Sounds like a bug in ubuntu to me.

press **alt+f2**
type> **gksudo gedit /etc/pm/config.d/config**
put:
**SUSPEND_MODULES="usbcore zd1211rw"**

save it and you should be good to go.

---

### Post by Troublegum on 2009-06-10
Thank you, that works. :)

But I have another little problem: My htpc case has a built-in infrared receiver (USB) for remote control. I run the irtrans irserver ([www.irtrans.com]("http://www.irtrans.com")) which acts as an replacement for lirc.

Usually, I can start the irserver with:
```
sudo /usr/local/irtrans/irserver /dev/ttyUSB0
```where /dev/ttyUSB0 is the infrared receiver.

After wakeup from suspend mode that call yields:
```
Init Server Socket done
Init Events done
Opening Device: /dev/ttyUSB0
Init communication ...
Opening Device: /dev/ttyUSB0
Init communication ...
Opening Device: /dev/ttyUSB0
Init communication ...
Error opening COM/USB Port / LAN Device
```If I try /dev/ttyUSB1 instead, it works. 


Can I do something to ensure that the usb device has the same path/name after waking up from suspend mode?
Or maybe use another startup script for the irserver? one in /etc/init.d for the first boot and one in /etc/acpi/resume.d for the resume?

---

### Post by Lampi on 2009-06-10
Does it help if you stop irserver service before Suspend? If it helps it's again a rule you setup in /etc/pm

---

### Post by kerry_s on 2009-06-10
try removing the "usbcore" part: 
**SUSPEND_MODULES="zd1211rw"**

i take out the usb cause that's usually the part that causes problems, but for you i don't think you need to. that should leave your usb devices alone.

---

### Post by Lampi on 2009-06-11
> **kerry_s said:**
> try removing the "usbcore" part: 
**SUSPEND_MODULES="zd1211rw"**
I liked your idea of removing usbcore as well - like this no usbdevice will cause problems.

But if he doesn't stop all services bound to a module before rmmod, some /dev/ nods are not removed. So /dev/ttyUSB0 is still up when he returns from STR

he could write an udev rule for his receiver device, but I don't think it is necessary if he unloads the service before rmmod/STR.

---

### Post by Troublegum on 2009-06-12
Hey Lampi, Hey kerry_s,

thank you for help. :)
I'm stopping/starting the service now with a script in /etc/pm/sleep.d.

---

