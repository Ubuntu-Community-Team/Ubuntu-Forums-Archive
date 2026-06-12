---
title: "Ceate Notifications"
date: 2012-06-07
forum: Desktop Environments
---

### Post by dexter197 on 2012-06-07
Hello, I'm using Ubuntu 12.04 and I want to create a notification (I think it's called gwibber) that tells me when my battery is fully charged. If anyone can tell me how to do it or a knows a video tutorial it would be very helpful. I tried the terminal command "notify-send text" but i don't know how to make that notification to pop out automatically.

Thanks in advanced :)

---

### Post by Cheesehead on 2012-06-07
There are a couple ways to detect the current battery state, which is provided by the 'upower' subsystem.

One way is to look in /proc:
```
$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      4233 mAh
present voltage:         12465 mV
```

Another way is to query DBus:
```
$ dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower/devices/battery_BAT1 org.freedesktop.DBus.Properties.Get string:org.freedesktop.UPower string:State
method return sender=:1.20 -> dest=:1.1541 reply_serial=2
   variant       uint32 4

```
Explanation: The first line is the command-line query.
The second line is metadata about the the query and response. Generally, you can safely ignore it.
The third line is the actual response. 'unint32' means the result is an integer. The actual result is '4' which means fully charged. (The codes are at [http://upower.freedesktop.org/docs/Device.html](http://upower.freedesktop.org/docs/Device.html) )

For the script you wish to write, I think the second method is probably easier. DBus isn't the easiest tool to work with, but I think it's worth learning.

---

