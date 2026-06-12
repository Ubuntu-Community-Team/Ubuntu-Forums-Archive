---
title: "Latitiude D810 fan won't come on, 13.10 saucy, MoBo really warm."
date: 2013-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ventrical on 2013-12-09
I installed the i8kutils package but no icon in gnome-session-flashback. Fan will not come on. MoBoard gets hot. Thing is , during installation of saucy the fan worked great.

Any tips?

Thank in advance.

13.10

I thought I would ask here first.

---

### Post by vitorafsr on 2013-12-10
I understood that your motherboard is hot and you want to cool it down, right?

If so, probably it is solved with 'i8kutils', as you already tried (w/ success).

So, it a matter of configuring properly the installation. Could you please post here your '/etc/default/i8kmon' and '/etc/i8kmon.conf'?

---

### Post by ventrical on 2013-12-10
etc/default/i8kmon

```
# /etc/default/i8kmon

# Change to one to enable i8kmon
ENABLED=0

```

Ok... I'll set that to 1

There is no i8kmon.conf

I do have i8kbuttons

```

# /etc/default/i8kbuttons

# Change to one to enable i8kbuttons
ENABLED=0

# Change these sample commands with your mixer commands!!!
#I8KBUTTONS_UP_CMD="echo up"
#I8KBUTTONS_DOWN_CMD="echo down"
#I8KBUTTONS_MUTE_CMD="echo mute"

# Poll interval (milliseconds)
#I8KBUTTONS_TIMEOUT=100

# Autorepeat interval (milliseconds)
#I8KBUTTONS_REPEAT=0

# Set kernel keycodes (for kernel 2.6.x). Set to "true" to enable.
#I8KBUTTONS_SETKEYCODES=false

# Kernel scancodes and keycodes
#I8K_SCAN_PLAY="e001"; I8K_KEY_PLAY="171"
#I8K_SCAN_STOP="e002"; I8K_KEY_STOP="172"
#I8K_SCAN_PREV="e003"; I8K_KEY_PREV="187"
#I8K_SCAN_NEXT="e004"; I8K_KEY_NEXT="189"
#I8K_SCAN_MUTE="e020"; I8K_KEY_MUTE="113"
#I8K_SCAN_VOLD="e02e"; I8K_KEY_VOLD="114"
#I8K_SCAN_VOLU="e030"; I8K_KEY_VOLU="115"


```

---

### Post by ventrical on 2013-12-10
Nothing happened.

Ok .. after enabling I get false fan reading (fan is not going at all).



```


marg@marg-Latitude-D810:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +65.5°C  (crit = +98.0°C)

i8k-virtual-0
Adapter: Virtual device
Left Fan:    57840 RPM
Right Fan:      0 RPM
CPU:          +65.0°C  

marg@marg-Latitude-D810:~$ 


```

---

### Post by vitorafsr on 2013-12-11
Ok... to function properly, you must have a '/etc/i8kmon.conf' with at least

    'set config(auto) 1'

An complete example of '/etc/i8kmon.conf' is below

# Sample i8kmon configuration file (/etc/i8kmon.conf, ~/.i8kmon).

# Kernel I8K status file
set config(proc_i8k)    /proc/i8k

# Kernel APM status file
set config(proc_apm)    /proc/apm

# Kernel ACPI status file
set config(proc_acpi)    /proc/acpi/ac_adapter/0/status

# External program to control the fans
set config(i8kfan)    /usr/bin/i8kfan

# Applet geometry, override with --geometry option
set config(geometry)    {}

# Run as daemon, override with --daemon option
set config(daemon)    0

# Automatic fan control, override with --auto option
set config(auto)    1

# Report status on stdout, override with --verbose option
set config(verbose)    0

# Status check timeout (seconds), override with --timeout option
set config(timeout)    5

# Temperature display unit (C/F), override with --unit option
set config(unit)    C

# Temperature threshold at which the temperature is displayed in red
set config(t_high)    80

# Minimum expected fan speed
set config(min_speed)    1800

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
# These were tested on the I8000. If you have a different Dell laptop model
# you should check the BIOS temperature monitoring and set the appropriate
# thresholds here. In doubt start with low values and gradually rise them
# until the fans are not always on when the cpu is idle.
set config(0)    {{- 0}  -1  55  -1  55}
set config(1)    {{- 0}  -1  55  -1  55}
set config(2)    {{- 1}  50  65  50  65}
set config(3)    {{- 2}  55 128  55 128}

# end of file

---

### Post by ventrical on 2013-12-11
I copy and pasted verbatim the code you put up and now the fans are working !! :) As soon as tempt gets over 51C ., turbo- left comes on and the right fan also.. then ildes at 1800 and these fans are not noisy at all..

Thanks..

---

