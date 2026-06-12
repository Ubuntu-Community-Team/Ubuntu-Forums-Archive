---
title: "CVS problems with Steam login"
date: 2006-06-04
forum: Gaming &amp; Leisure
---

### Post by ubu-for on 2006-06-04
Everytime I try to login to Steam with CVS ...

```

sh cvscedega 'c:\Programme\Steam\Steam.exe'

```

... I get this error message from Steam ...

"Could not connect to Steam network.
This could be due to a problem with your Internet connection, ..."

... and this terminal messages:

```

err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:keyboard:X11DRV_KEYBOARD_DetectLayout Your keyboard layout was not found!
Using closest match instead (German keyboard layout without dead keys) for scancode mapping.
Please define your layout in windows/x11drv/keyboard.c and submit them
to us for inclusion into future Wine releases.
See the Wine User Guide, chapter "Keyboard" for more information.
err:task:GetThreadQueue16 Breaking 16 bit for tid 2
err:task:GetThreadQueue16 Breaking 16 bit for tid 2
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:wave:ALSA_WaveInit -fixme:wave:ALSA_WaveInit -
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:win32:DEVICE_Open Unknown/unsupported VxD GDPERF. Try --winver nt40 or win31 !
fixme:ver:GetVersionExA OSVERSIONINFOA is too large (possibly OSVERSIONINFOEXA)
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:wininet:ConvertTimeString
wine: Unhandled exception, starting debugger...
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
err:seh:start_debugger Couldn't start debugger ("winedbg --debugmsg -all -- --auto 1 460") (2)
Read the Wine Developers Guide on how to set up winedbg or another debugger
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1
fixme:msimg32:GradientFill stub: 2 vertices 1 gradients mode 1

```

Steam works with Wine 0.9.14 but can't start CSS.

```

WINEDEBUG=-all wine 'c:\Programme\Steam\Steam.exe'
wine: Call from 0x2a00c490 to unimplemented function d3d9.dll.D3DPERF_SetOptions, aborting
wine: Call from 0x7fc0eb30 to unimplemented function dbghelp.dll.SymGetSymFromAddr64, aborting

```

S.O.S. please! ;-)

P.S. CVS profile option "0".

---

### Post by rachii on 2006-06-04
i dont know if this will help you but it worked for me. 
although i didnt use cvs,  i just added wine to my sources and installed via apt, and for the first time everything worked flawlessly.

#edit#
link was not working for some reason, so copy and paste url

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

---

### Post by ubu-for on 2006-06-05
Thank you for your reply!

But it's just a Wine installation howto and because of problems with Wine since months, I've begun to give CVS a try. Without success!

Maybe it's because of the not installed "x-window-system-dev", but apt-get couldn't find it.

P.S. The direct link was working for me.

---

### Post by rachii on 2006-06-05
just a quick thought while im still half asleep...

i've also had issues with wine  where if i wasnt in the directory of the .exe that i wanted to run, it would spit out errors and not work.   so that i could just give it a command and .exe, and not an address for the exe

and did you try that wine debug command it gave you...maybe that would have some more information

winedbg --debugmsg -all -- --auto 1 460

---

### Post by ubu-for on 2006-06-05
[QUOTE=rachii]
winedbg --debugmsg -all -- --auto 1 460
[/QUOTE]

```

winedbg --debugmsg -all -- --auto 1 460 'c:\Programme\Steam\Steam.exe'
Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]

winedbg --debugmsg -all --'c:\Programme\Steam\Steam.exe' --auto 1 460
Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]

winedbg --debugmsg -all --'c:\Programme\Steam\Steam.exe' Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]

winedbg --debugmsg -all 'c:\Programme\Steam\Steam.exe'
Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]

winedbg -debugmsg -all 'c:\Programme\Steam\Steam.exe'
Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]

```

I'm sorry, but I'm new to Linux and don't know how to implement your command correctly.

---

### Post by rachii on 2006-06-05
sorry dont use wine much myself (at least not debugging it), i just copied the  command that your original error output to you....  im sure if you search the forums you can find winedbg help

---

