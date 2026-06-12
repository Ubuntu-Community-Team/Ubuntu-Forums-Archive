---
title: "i8kfan changes only last a few seconds"
date: 2008-02-13
forum: Dell  Ubuntu Support
---

### Post by Termina on 2008-02-13
I have to load i8k module with "i8k force=1" for some reason.

However, i8kfan does change the speed (i8kfan - 2) on my Vostro 1400 (7.10)

However, after a few seconds it changes the fan speed back to low/off (hard to tell, very quiet).

My CPU isn't very hot (40oC), but the laptop/keyboard get VERY warm (to the point it's uncomfortable for me to use the laptop). 

Does anyone know how to have these changes take affect and stay?

I should mention that this used to work with 7.10 without the "force=1", and the fan would stay at the setting I chose without issue. After a fresh reinstall, this happened (maybe a more recent kernel is causing this problem?)

---

### Post by neptho on 2008-02-14
You will want to load i8kmon as a resident process to keep it going.

[Read here](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Setting_custom_temperature_thresholds_for_your_system_fans).

---

### Post by solitaire on 2008-02-14
Do you use  "i8kmon" ?

That should give you a temp readout and buttons to controll the fans.

---

### Post by Termina on 2008-02-16
i8kmon has the same issue; clicking it to set the fan to "2" only lasts a few seconds. It goes right back to 1.

I tried upgrading the bios to A07, no luck.

---

### Post by neptho on 2008-02-17
Have you created the config file and started i8kmon from an init script?

My /etc/rc.local:
%cat /etc/rc.local
```
#!/bin/sh -e
PATH=/bin:/sbin:/usr/bin:/usr/sbin
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/bin/i8kmon -a -d &
exit 0
```

My /etc/i8kmon:
%cat /etc/i8kmon
```
set config(0) {{- 0} -1 35 -1 40}
set config(1) {{- 1} 30 45 35 50}
set config(2) {{- 2} 40 128 45 128}
```

Adjust as required for your purposes.

---

### Post by Termina on 2008-02-21
Tried your suggestion, and still no go. Fan tries to go to highest setting, and goes back to low after a second or two. :(

---

### Post by trondhuso on 2008-02-24
Can you tell what those numbers in the set means?

-t-

---

### Post by neptho on 2008-02-25
Open a terminal, and type 'man i8kmon', then scroll down to 'Configuration'.

---

### Post by butze on 2008-05-29
> **Termina said:**
> Tried your suggestion, and still no go. Fan tries to go to highest setting, and goes back to low after a second or two. :(

I got the same problem with ubuntu 8.04 on an Inspiron 9400

I have to load i8k with "i8k force=1" and tried to set my fanspeed with the gkrellm i8k plugin and with i8kfan 2 2.
Doesn' t matter how, the fans keep setting themselves back to low after some seconds...

uname -a
Linux delltop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

cat /proc/i8k 
1.0 A09 6LBK49 36 1 1 88320 74130 -1 -22 

it always jumps back to 1 1

The right side of my Inspiron 9400 stays very hot after some time. Somebody an idea?

---

### Post by bubbalouie on 2008-05-29
Try the following configuration:

> 
#file:/etc/i8kmon

# Run as daemon, override with --daemon option
set config(daemon) 1

# Automatic fan control, override with --auto option
set config(auto) 1
set config(timeout) 1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
# These were tested on the I8000. If you have a different Dell laptop model
# you should check the BIOS temperature monitoring and set the appropriate
# thresholds here. In doubt start with low values and gradually rise them
# until the fans are not always on when the cpu is idle.

set config(0) {{- 0} -1 50 -1 50}
set config(1) {{- 1} 45 55 45 55}
set config(2) {{- 2} 50 60 50 60}
set config(3) {{- 2} 60 128 60 128}

# end of file

You will of course need to adjust your thresholds accordingly, also keep in mind this can break things if you let it run hot....

---

