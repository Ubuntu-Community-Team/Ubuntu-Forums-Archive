---
title: "i810 possible to run 1152x864?"
date: 2007-02-28
forum: Desktop Environments
---

### Post by monkman on 2007-02-28
hi!

even with modelines i can't convince X(KDE) to run in 1152x864 resolution. isn't this mode support by the onboard graphics? i got the intel865 chipset.

kubuntu 6.10

thx!

---

### Post by veloce on 2007-02-28
Do you have 915resolution installed?

---

### Post by monkman on 2007-03-21
yes, but it doesn't show me the preferred resolution. so it looks like it wouldn't be supported. but in win_xp it's no problem....

---

### Post by wieman01 on 2007-03-21
> **monkman said:**
> yes, but it doesn't show me the preferred resolution. so it looks like it wouldn't be supported. but in win_xp it's no problem....
Have you updated your xorg.conf accordingly?

---

### Post by monkman on 2007-03-21
you mean adding the resolution "1152x864" in the correct place? yes i did...

---

### Post by veloce on 2007-03-23
> **monkman said:**
> yes, but it doesn't show me the preferred resolution. so it looks like it wouldn't be supported. but in win_xp it's no problem....

If 915resolution doesn't recognise the resolution automatically, then you need to set the resolution manually.  You do this by editing the file /etc/default/915resolution.  Here's mine

```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=5c
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1400
YRESO=1050
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32

```

you don't need to specify the mode or bit, but I suggest you use the XRESO and YRESO lines.

---

### Post by monkman on 2007-04-12
so i installed 915resolution and edited the file. 
```

# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=auto
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1152
YRESO=864
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=

```


```
monkman@ubuntu:~$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 865G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

```

is 915resolution in the startup, or is there something i have to make the changes happen?
still i can choose 1280*X or 1024*X but not 1152*X

thanks!

---

