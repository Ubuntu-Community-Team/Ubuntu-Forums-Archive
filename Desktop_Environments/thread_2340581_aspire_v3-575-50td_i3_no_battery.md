---
title: "aspire v3-575-50td i3 no battery"
date: 2016-10-19
forum: Desktop Environments
---

### Post by rev-matthewagilmore on 2016-10-19
This happens every time I do a clean install on  this laptop. and for some reason I cant find what made it work the last time.
I do remember it being the path that makes it work

 this is the i3status.config file

```


[B]# i3status configuration file.
# see "man i3status" for documentation.

# It is important that this file is edited as UTF-8.
# The following line should contain a sharp s:
# ß
# If the above line is not correctly displayed, fix your editor first!

general {
        colors = true
        interval = 5
}
order += "wireless _first_"
order += "tztime local"
order += "load"
#order += "ipv6"
order += "disk /"
order += "run_watch DHCP"
order += "run_watch VPN"

order += "ethernet _first_"
order += "battery 1"



wireless _first_ {
        format_up = "W: (%quality at %essid) %ip"
        format_down = "W: down"
}

ethernet _first_ {
        # if you use %speed, i3status requires root privileges
        format_up = "E: %ip (%speed)"
        format_down = "E: down"
}
#battery 0 is default
#battery 0 {
#          format = "%status %percentage %remaining"
#}

battery 1 {
format = "%status %percentage %remaining"
path = "/org/freedesktop/UPower/devices/battery_BAT1"
}


run_watch DHCP {
        pidfile = "/var/run/dhclient*.pid"
}

run_watch VPN {
        pidfile = "/var/run/vpnc/pid"
}

tztime local {
        format = "%Y-%m-%d %H:%M:%S"
}

load {
        format = "%1min"
}

disk "/" {
        format = "%avail"
}

[/B]
```

before you ask , i did try changing the path to /org/freedesktop/UPower/devices/battery_BAT1
I ran upower -i /org/freedesktop/UPower/devices/battery_BAT1

this is what popped up
```

native-path:          BAT1
  vendor:               SANYO
  model:                AL15A32
  serial:               58874
  power supply:         yes
  updated:              Wed 19 Oct 2016 08:57:45 PM CDT (80 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              19.9504 Wh
    energy-empty:        0 Wh
    energy-full:         33.6404 Wh
    energy-full-design:  37 Wh
    energy-rate:         11.4404 W
    voltage:             15.856 V
    time to empty:       1.7 hours
    percentage:          59%
    capacity:            90.92%
    technology:          lithium-ion
    icon-name:          'battery-good-symbolic'
  History (charge):
    1476928664    59.000    discharging
  History (rate):
    1476928665    11.440    discharging
    1476928664    17.686    discharging



```

---

### Post by rev-matthewagilmore on 2016-10-19
I found the  right file path
```

path = "/sys/class/power_supply/BAT1/uevent"

```
 to find it i just looked around int the /sys/class/power_supply moving my way up till i found uevent

---

### Post by Bucky Ball on 2016-10-19
If this is solved please mark it that way by using Thread Tools at top right or follow the link in my signature at the bottom of this post if you get lost. Thanks.

For future reference, when posting for support it will help your cause if you clearly state which Ubuntu release and flavour you are using.

---

