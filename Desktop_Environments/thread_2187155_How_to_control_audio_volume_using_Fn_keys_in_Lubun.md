---
title: "How to control audio volume using Fn keys in Lubuntu 13.10?"
date: 2013-11-11
forum: Desktop Environments
---

### Post by Remten on 2013-11-11
ASUS N550JV laptop
lubuntu 13.10  3.11.0-13-generic

pulseaudio, pavucontrol
(also nvidia-319, nvidia-prime, xfce4 & xfce4-goodies metapackages)

**I don't know how to control the sound volume for the built-in speakers using the keyboard.**

This Asus laptop has a row of function keys across the top of the keyboard. I have been able to get F1-F6 working the way I want them, partly from using xbindkeys to map scripts for controlling the keyboard backlight and screen backlight.

F10-F12 are a problem. The F11 key has an icon for lowering the volume; F12 for raising the volume; and I think the icon on F10 is supposed to represent a toggle for Mute. But none of these functions work in Lubuntu.

[COLOR=#0000cd]This seems to be a lubuntu or lxde-specific issue because when I run xfce sessions, the F10-F12 function keys DO control the volume[/COLOR] (and pressing the keys even calls up a volume level graphical display).

(My tests are from monitoring the sound volume using youtube videos.)

F10 - opens a browser File menu  (eg New Tab, New Window, Open File options)
F11 - toggles fullscreen mode for whatever window is active
F12 - pulls up a browser debugging window
Fn + F10 - does nothing
Fn + F11 - does nothing
Fn + F12 - does nothing
Fn + right arrow - does nothing
Fn + left arrow - does nothing

possibly relevant /etc/default/grub.conf:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\""
GRUB_CMDLINE_LINUX=""
```
(I used the !Windows 2012 setting because it enabled the wireless card radio control via Fn + F2)

```
Remten@XXXX:~$ cat /proc/asound/card0/codec* | grep Codec
Codec: Intel Haswell HDMI
Remten@XXXX:~$ cat /proc/asound/card1/codec* | grep Codec
Codec: Realtek ALC668
Remten@XXXX:~$ 
```

lspci shows this (edited):
```
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
    Subsystem: Intel Corporation Device 2010
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at f7a14000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel
. . .

00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 11cd
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at f7a10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: snd_hda_intel
```

info from xev scans:

Fn - nothing
F10 - keycode 76 = (keysym 0xffc7, F10), state = 0x0
F11 - (switches to fullscreen mode; no keypress code displayed)
F12 - keycode 96 = (keysym 0xffc9, F12), state = 0x0
Fn + F10 - nothing
Fn + F11 - nothing
Fn + F12 - nothing
Fn + right arrow - keycode 171 = (keysym 0x1008ff17, XF86AudioNext), state = 0x0
Fn + left arrow - keycode 173 = (keysym 0x1008ff16, XF86AudioPrev), state = 0x0

acpi_listen scans:

F9 - [[20~
F10 - (opens the File menu; nothing shows up in terminal for the keypress codes)
F11 - (switches to fullscreen mode; no keypress code displayed)
F12 - ^[[24~
Fn + F9 - nothing
Fn + F10 - nothing
Fn + F11 - nothing
Fn + F12 - nothing
Fn + right arrow - nothing

xbindkeys-config "get key" scans:
F10 - F10 | m:0x0 + c:76
F11 - (switches to fullscreen mode; no keypress code displayed)
F12 - F12 | m:0x0 + c:96
Fn + F10 - nothing
Fn + F11 - nothing
Fn + F12 - nothing
Fn + right arrow - XF86AudioNext | m:0x0 + c:171
Fn + left arrow - XF86AudioPrev | m:0x0 + c:173

I have pulseaudio and pavucontrol installed.

The GUI for Audio Mixer shows:
Sound Card:  Playback:  Built-in Audio Digital Stereo (HDMI)  (PulseAudio Mixer)
Playback[INDENT]Master[/INDENT]
and under Select Controls, Master is checked

The GUI for PulseAudio Volume Control shows
System Sounds[INDENT]Mono  - set at 100% (0dB)
[/INDENT]
Playback[INDENT]ALSA plug-in [Firefox]:  ALSA playback on  (Built-in Audio Analog Stereo)
set at 100% (0dB)[/INDENT]

Output Devices[INDENT]Built-in Audio Digital Stereo (HDMI)[/INDENT]
[INDENT=2]Port:  (HDMI / DisplayPort)
front left & front right both set at 100% (0dB)
[/INDENT]
[INDENT]Built-in Audio Analog Stereo[/INDENT]
[INDENT=2]Port: (Speakers)
front left & front right both set at 100% (0dB)
[/INDENT]
Configuration[INDENT]Built-in Audio[/INDENT]
[INDENT=2]Profile: (Digital Stereo (HDMI) Output)[/INDENT]
[INDENT]Built-in Audio
[/INDENT]
[INDENT=2]Profile: (Analog Stereo Duplex)[/INDENT]

other thought: before installing pavucontrol, I tried
```
Remten@XXXX:~$ amixer sset Master 10%
amixer: Unable to find simple control 'Master',0
```

---

### Post by Remten on 2013-11-11
I figured out a couple of things:
[LIST]
[*]the card that is controlling audio volume during youtube playback is the Realtek ALC668 analog 
[*]the audio volume can be changed in the pavucontrol GUI by making adjustments to the Built-in Audio Analog Stero / Speakers front-left & front-right slider bars under the "Output Devices" tab 
[/LIST]

Can someone explain what the equivalent console commands would be for raising or lowering those pulseaudio settings?

If I find that, I guess I should be able to map it with xbindkeys.

---

### Post by Remten on 2013-11-11
Ok, I have found a script that makes it possible to use pulse audio to control the volume from the command line.
[http://blog.waan.name/pulseaudio-setting-volume-from-command-line/](http://blog.waan.name/pulseaudio-setting-volume-from-command-line/)

So I can map this function to keypresses using xbindkeys.

But I would still like to use specifically the F11 & F12 function keys for this.
The only remaining problem is that those keys don't seem to be controllable.
F11 immediately switches to fullscreen mode and doesn't show any codes in xev, acpi_listen, or xbindkeys. Fn + F11 doesn't seem to do anything and doesn't register any codes at all.

Can someone help?

---

### Post by Remten on 2013-11-12
Finally figured out how to do this.

First, it is necessary to modify the openbox configuration file
/home/yourname/.config/openbox/lubuntu-rc.xml file
which seems to take precendence over other keyboard drivers (or whatever the correct term is), like xbindkeys.

There is a section within lubuntu-rc.xml that assigns F11 to toggle the fullscreen display.
I took that assignment out.

Then I used xbindkeys to make the following assignments using the script mentioned in the previous post
F11 calls "pa-vol.sh minus"
F12 calls "pa-vol.sh plus"
F10 calls "pa-vol.sh mute"

(I had to change the SINK_NAME definition line in the script back to how it had been in an older version of the script code:
```
SINK_NAME="alsa_output.pci-0000_00_1b.0.analog-stereo"
```

because the newer version, namely
```
[COLOR=#007800]SINK_NAME[/COLOR]=$[COLOR=#7a0874]**(**[/COLOR]pactl [COLOR=#c20cb9]**stat**[/COLOR] [COLOR=#000000]**|**[/COLOR] [COLOR=#c20cb9]**grep**[/COLOR] [COLOR=#ff0000]"alsa_output"[/COLOR] [COLOR=#000000]**|**[/COLOR] [COLOR=#c20cb9]**perl**[/COLOR] [COLOR=#660033]-a[/COLOR] [COLOR=#660033]-n[/COLOR] [COLOR=#660033]-e[/COLOR] [COLOR=#ff0000]'print $F[2]'[/COLOR][COLOR=#7a0874]**)**[/COLOR]
```did not work for me)

---

### Post by QIII on 2013-11-12
*Moved to **Desktop Environments **by OP request.*

---

