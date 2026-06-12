---
title: "can't change system time"
date: 2006-09-17
forum: Desktop Environments
---

### Post by dmizer on 2006-09-17
this is very annoying as during the install i only had the choice of us standard times.  during the install with the alternate cd.  if you choose us english as your local and us keyboard, you are only presented with us time zones.

i'd like to have the correct time displayed but:
```
$ sudo date -s "Mon Sep 18 07:26 JST 2006"
Password:
Sun Sep 17 17:26:00 CDT 2006

```
i can pass the command as many times as i like and i still remain in CDT.

---

### Post by fragos on 2006-09-17
I may be mistaken but I don't see how date sets time zone.  It appears to only display it.  To be honest I always use Gnome to set time and in that case there is a separate funtion for time zone but that does work.

---

### Post by mitch.c on 2006-09-17
> **dmizer said:**
> 
i'd like to have the correct time displayed but:
```
$ sudo date -s "Mon Sep 18 07:26 JST 2006"
Password:
Sun Sep 17 17:26:00 CDT 2006

```
i can pass the command as many times as i like and i still remain in CDT.
I don't think you can change the timezone using date. Time zone is set in /etc/localtime. This can contain tz data itself, or be a symlink to /usr/share/zoneinfo/your/time/zone.

With ubuntu I think what you want is:
```
sudo tzconfig
```

Or, if your using gnome, you could use the GUI:
System -> Administration -> Time and Date

---

### Post by dmizer on 2006-09-18
per man date:
```
-s, --set=STRING
              set time described by STRING

```
cli only.

---

### Post by bigken on 2006-09-18
Try this right click the panel clock select preferences and uncheck use UTC ;)

---

### Post by mitch.c on 2006-09-18
> **dmizer said:**
> per man date:
```
-s, --set=STRING
              set time described by STRING

```
cli only.
Is that persistent? I thought system time would be set back to hwclock and TZ info would be set from /etc/localtime after reboot. At the very least I thought you would need to set time via hwclock.

---

### Post by dmizer on 2006-09-18
actually, i was able to fix it with sudo tzconfig, but it wouldn't have been a problem at all if i had been able to choose the correct time zone when i installed ubuntu in the first place.

i use to use sudo date -s to set system time in breezy all the time. not sure why that's not working anymore either, and yes, it was persistent.

---

### Post by mitch.c on 2006-09-18
> **dmizer said:**
> the bios has no time settings that i can find.

This is where I think you want:
```
# Set system time with date first
sudo hwclock --systohc #sets hardware clock using system time
```

---

### Post by dmizer on 2006-09-18
that's the last piece i needed.  thanks.

---

