---
title: "Xrandr bad modes"
date: 2008-05-17
forum: Desktop Environments
---

### Post by Wavicle on 2008-05-17
Hi, I'm trying to get some games working with wine, and everything is going fine except the video modes. For some reason there is a bad mode being selected - specifically 800x600 @ 73Hz. I have no idea why the system thinks that is an acceptable setting, but it does.

```
joe@roadrunner:~$ xrandr --verbose -q
Screen 0: minimum 320 x 240, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 (0x1ad) normal (normal) 0mm x 0mm
...snip...
  800x600 (0x1c4)   35.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   43.8KHz
        v: height  600 start    0 end    0 total  600           clock   **73.0Hz**
...snip...
joe@roadrunner:~$ 

```

Any other rate but 73 works fine. But for the life of me, I cannot get RandR to remove that refresh rate from the available list and my monitor, an Acer AL2223W, cannot display that. Part of the problem is that Xrandr has major ambiguities in its documentation. I'm using the nv driver with a GeForce 7600GS.

If it helps, nvidia-setting gives this as the monitor EDID:

```
joe@roadrunner:~$ hexdump -C edid.bin 
00000000  00 ff ff ff ff ff ff 00  04 72 84 ad bb 47 30 71  |.........r...G0q|
00000010  0d 11 01 03 08 2f 1e 78  2e 93 45 a3 55 4a 98 27  |...../.x..E.UJ.'|
00000020  15 50 54 bf ef 00 b3 00  a9 40 95 0f 95 00 81 c0  |.PT......@......|
00000030  81 40 49 4f 81 80 21 39  90 30 62 1a 27 40 68 b0  |.@IO..!9.0b.'@h.|
00000040  36 00 da 28 11 00 00 1c  00 00 00 fd 00 38 4b 1f  |6..(.........8K.|
00000050  51 11 00 0a 20 20 20 20  20 20 00 00 00 fc 00 41  |Q...      .....A|
00000060  4c 32 32 32 33 57 0a 20  20 20 20 20 00 00 00 ff  |L2223W.     ....|
00000070  00 4c 38 34 30 42 30 31  38 33 39 32 30 20 00 a7  |.L840B0183920 ..|

```

---

### Post by sdennie on 2008-05-17
Are you using the nv (open source) or nvidia (closed source) driver?

---

### Post by Wavicle on 2008-05-17
> **vor said:**
> Are you using the nv (open source) or nvidia (closed source) driver?

Apparently I got it backwards. I am using the nvidia (closed source, restricted) driver. Not nv.

---

### Post by AmyRose on 2009-08-01
I have the same problem. I can't get xrandr to remove any of the refresh rates for 800x600 either.

---

