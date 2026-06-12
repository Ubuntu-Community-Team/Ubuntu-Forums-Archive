---
title: "get wine/cvscedega to run games HELP"
date: 2006-07-26
forum: Gaming &amp; Leisure
---

### Post by bunnny on 2006-07-26
I have (I think) at last sucseded with the installation of wine and cvscedega, but I can't get any games to work.

I first tried to install battlefield 1 but it crash when it should ask my about the serial key. (both wine and cvscedega)

Then I tried to install Shogo (old school), the installation went flawless, and I could start the "start controll" and I got sound WOW! but when it should start the screen just flash ones and the game died.

The error:
```
sudo cvscedega .wine/drive_c/Games/Shogo/Shogo.exe
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:wave:ALSA_WaveInit -fixme:wave:ALSA_WaveInit -
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
err:x11drv:error_handler BadImplementation (server does not implement operation) error (17) for X request 129 minor 5 serial 3539 from thread 0x00000002
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  129 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3539
  Current serial number in output stream:  3557
err:wave:wodOpen Rate doesn't match (requested 22050 Hz, got 48000 Hz)
err:wave:wodOpen Rate doesn't match (requested 22050 Hz, got 48000 Hz)
err:wave:wodOpen unable to set required format: Invalid argument
err:wave:wodOpen unable to set required channels: Invalid argument
err:wave:wodOpen unable to set required channels: Invalid argument
fixme:msacm:wodWrite Not all src buffer has been written, expect bogus sound
fixme:module:CreateProcessA (D:\.wine\drive_c\Games\Shogo\Client.exe,...): CREATE_NEW_PROCESS_GROUP ignored
fixme:module:CreateProcessA (D:\.wine\drive_c\Games\Shogo\Client.exe,...): CREATE_DEFAULT_ERROR_MODE ignored
/usr/lib/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804c9dc)
err:x11drv:error_handler BadPixmap (invalid Pixmap parameter) error (4) for X request 54 minor 0 serial 4349 from thread 0x00000002
X Error of failed request:  BadPixmap (invalid Pixmap parameter)
  Major opcode of failed request:  54 (X_FreePixmap)
  Resource id in failed request:  0x2600351
  Serial number of failed request:  4349
  Current serial number in output stream:  4352
darkvillage@theone:~$ err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:wave:ALSA_WaveInit -fixme:wave:ALSA_WaveInit -
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
err:module:BUILTIN_LoadModule loaded .so but dll joystick.drv still not found
err:module:BUILTIN_LoadModule loaded .so but dll joystick.drv still not found
err:module:BUILTIN_LoadModule loaded .so but dll joystick.drv still not found
err:module:BUILTIN_LoadModule loaded .so but dll joystick.drv still not found
fixme:ddraw:DirectDrawEnumerateExA no non-display devices supported.
fixme:ddraw:DirectDrawEnumerateExA no detached secondary devices supported.
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0xb7af8b34)->(00030025,00000011)
err:x11drv:error_handler BadImplementation (server does not implement operation) error (17) for X request 129 minor 5 serial 208 from thread 0x00000005
X Error of failed request:  BadImplementation (server does not implement operation)
  Major opcode of failed request:  129 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  208
  Current serial number in output stream:  210
err:x11drv:error_handler BadDrawable (invalid Pixmap or Window parameter) error (9) for X request 55 minor 0 serial 215 from thread 0x00000005
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x260002f
  Serial number of failed request:  215
  Current serial number in output stream:  220

```

I would realy be happy if I could get this to work, I have tried wine and cvscedega many times now, but newer got it to work.

(excuse my bad english)

---

### Post by nw15062 on 2006-08-31
I know what your problem is, I have the same issue, your config file has its font path pointed to a directory that does not exist, that is why cvscedega crashes cause it dos not know where to find the font, ofcourse I would be able to find a solution if I know where the truetype fonts were located in ubuntu, I fail to understand why Linux likes to put fonts all over the place all the time.

---

### Post by justin whitaker on 2006-09-01
Doesn't Shogo have a native linux installer? I seem to recall that there was an effort to put one together a while back....but that doesn't help you one bit, does it?

Ok, common fixes for games with WINE cedega:

1. get the fonts, put them in your fake windows drive.
2. install mozcontrol (works for more recent games)
3. copy the game cds to a folder in /Home, and use wine to install from there.

---

