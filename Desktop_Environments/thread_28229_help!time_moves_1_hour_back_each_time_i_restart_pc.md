---
title: "help!time moves 1 hour back each time i restart pc!"
date: 2005-04-19
forum: Desktop Environments
---

### Post by lorap on 2005-04-19
after i've installed hoary i was prompted to open some file,don't remember its name and edit it or i would not be able to get recognized at my geografic location.
thanks.
pavel

---

### Post by Nano on 2005-04-19
[QUOTE=lorap]after i've installed hoary i was prompted to open some file,don't remember its name and edit it or i would not be able to get recognized at my geografic location.
thanks.
pavel[/QUOTE]
 Probably it's not a matter of geographic location. Check in your clock settings if UTC is checked or not.

---

### Post by lorap on 2005-04-19
nope utc is unchecked,i just saw the warning after installation,just donno what i had have changed there.
thanks.
pavel

---

### Post by miklov on 2005-04-19
The first thing to do is to check how the time is stored in BIOS.

Go into setup, and check that the time is set to UTC.

Boot up into Ubuntu and go to System --> Administration --> Time & Date and make sure it is set to the correct time zone.

You can also add ntp (connects to an internet time server to correct time) to startup with the command from any terminal

```
sudo update-rc.d -f ntpdate defaults
```

Hope something here helps

---

