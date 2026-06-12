---
title: "X error when fullscreen @ 320x240 resolution"
date: 2015-10-09
forum: Gaming &amp; Leisure
---

### Post by Pnumekin on 2015-10-09
Hello
I have a problem with one of my PC running Lubuntu 14.04 x64. The goal of that PC is specific, I want to have a max resolution at 320x240 because it's connected to an old crt screen from an arcade machine.


I have added th two lines needed in 45x11-xrandr to have a 320x240 modeline available, and added a line in Lubuntu autostart to switch to this resolution.
It ok and I have my desktop running at 320x240.

When I use Groovymame (a modified version of MAME emulator), all is running fine. Groovymame automatically switch the resolution for the game resolution (cga resolutions only).

And now my problem, I want to use Supermodel ([http://www.supermodel3.com/](http://www.supermodel3.com/)) and Daphne ([http://www.daphne-emu.com/site3/index_hi.php](http://www.daphne-emu.com/site3/index_hi.php)). I have compiled Supermodel myself from the source, I use Daphne binaries (x86) from the official site.

If I start Supermodel with full screen, I have this error:

```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  152 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x2c4
  Serial number of failed request:  146
  Current serial number in output stream:  148
```

If I start Daphne with full screen, I have this error  :

```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  152 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x2c4
  Serial number of failed request:  167
  Current serial number in output stream:  169
```

If I start these emulators at 320x240 but not fullscreen, they work. If I connect a standard computer screen and switch my resolution to 1024x768 they work (fullscreen or windowed)
I was using the same PC with these emulators, but under win xp and they worked like a charm at 320x240.

Any idea to solve this problem ?

My graphic card :
```
lspci |grep "VGA compatible controller"
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV790 [Radeon HD 4890]
```

My drivers :
```
grep /drivers/ /var/log/Xorg.0.log
[    11.537] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    11.537] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    11.543] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    11.543] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.544] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.544] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    11.544] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    11.544] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.544] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
```

---

