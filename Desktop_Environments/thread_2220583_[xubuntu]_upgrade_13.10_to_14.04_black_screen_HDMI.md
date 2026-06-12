---
title: "[xubuntu] upgrade 13.10 to 14.04 black screen HDMI/ TV 'No signal'"
date: 2014-04-28
forum: Desktop Environments
---

### Post by Raymond_Uphoff on 2014-04-28
I've updated Xubuntu from 13.10 to 14.04 and it all went well. Reboot the system and login-screen. I filled out my password and voila 14.04 up and running. But now comes the but; The TV switch to No singal after a while and it wouldn't switch back on by mouse or keyboard. I've got a Ivy-Bridge i3 running Intel Graphics connected to a Philips LCD TV by HDMI (HDMI2).

[LIST]
[*]I can access terminal by switch to TTYx switching back to F7 is black again. 
[*]When TV switch itself of after 3 Hours and I switch TV back on, no way it will see a signal from system running Xubuntu. 
[*]Reinstalled Xserver and inteldrivers and set permissions back again. still same problem 'No signal' 
[*]Set kernel parameters 'nomodeset' and 'acpi'_something. doesn't make a difference. TV goes to 'No signal' 
[*]Set Power Managament Monitor to 'Never' same problem and fiddled with other power management settings 
[*]'I read a topic here about Display Manager. so a give the following command a try; ```
sudo services lightdm restart
``` bam. Back in Login-screen so TV switched back on. What the heck! 
[/LIST]

Somebody a clue?

---

### Post by dannyboy79 on 2014-04-28
that command is used to restart your x server. i am assuming your tv isn't sending a signal back to xubuntu so xubuntu thinks it can go to sleep. are you sure you disabled all the power saving options within your xorg? look into DPMS

---

### Post by Raymond_Uphoff on 2014-04-29
Probably you mean my monitor can go to sleep. I set time to system go into sleep to 'never'. I also thicked off settings-->Settings Manager-->Power Manager --> general tab --> uncheck "Monitor power management control". Apparently DPMS is still enabled, see console output. One think I don't understand about my TV is not sending a signal; Why did this setup work with Xubuntu 12.10, 13.04 and 13.10?
```

raymond@htpc:~$ lspci -v | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
raymond@htpc:~$ grep DPMS /var/log/Xorg.0.log
[ 38260.415] Initializing built-in extension DPMS
[ 38260.428] (==) intel(0): DPMS enabled
raymond@htpc:~$ egrep -i " connected" /var/log/Xorg.0.log
raymond@htpc:~$ egrep -i "drivers" /var/log/Xorg.0.log
[ 38260.422] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 38260.423] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 38260.423] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 38260.424] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 38260.425] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
raymond@htpc:~$

```

```

raymond@htpc:~$ sudo Xorg -configure
[sudo] password for raymond:
(EE)
Fatal server error:
(EE) Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.
(EE)
(EE)
Please consult the The X.Org Foundation support
     at http://wiki.x.org
 for help.
(EE)

```

By the way I can't find xorg.conf. it's not in /etc/X11/ and not in /usr/share/X11/

---

### Post by Raymond_Uphoff on 2014-04-30
Anybody?!

---

### Post by dannyboy79 on 2014-04-30
xorg.conf isn't created by the system. if you need to do something non-standard than you would create an xorg.conf file and put it within /etc/X11/

I can not say why it worked in previous ubuntu versions. i just noticed you're using some acpi or other in your kernel boot line, please remove that as well as the nomodeset, did you have either of those in your previous ubuntu installs when you say it was working?

---

### Post by Raymond_Uphoff on 2014-05-01
@dannyboy79 I've tested with these kernel-parameters, but it didn't  work. The behavior was still the same, so I removed these entries. So  you think creating a custom xorg.conf will solve the problem?

---

### Post by Raymond_Uphoff on 2014-05-01
I could dfind how to control my display with xset. Arch Linux Forum give the correct syntax. Now I can switch my TV on and off in cli;
```

root@htpc:~# xset -display :0 dpms force off
root@htpc:~# xset -display :0 dpms force on

```

hmm one step further. 
<Edit>
I've let Xorg generate a xorg.conf file. but first stopped display Manager;
```

sudo Xorg -configure

``` 
The move it from yopur home directory to etc/X11/
Now I've add extra entries in /etc/X11/xorg.conf;
```

Section "ServerFlags"
    Option "blank time"    "0"
    Option "standby time"    "0"
    Option "suspend time"    "0"
    Option "off time"    "0"
    Option "dpms"        "false"
EndSection

```
Let see how this goes!

---

### Post by Raymond_Uphoff on 2014-05-02
The previous settings don't work. This morning I switched on my TV and bamm 'no signal' I've restart Display Manager and know the xset command doesn't work;
```

raymond@htpc:~#sudo xset -display :0 q
Invalid MIT-MAGIC-COOKIE-1 keyxset:  unable to open display ":0"

```

---

### Post by macachuto on 2014-05-02
Hi.
First of all - you shouldn't do anything related to you current screen/user under root. So do not use sudo.
Second:
1. Do you use only one monitor? Or it is a laptop with Monitor/TV connected?
2. To see a user current settings you can execute in xterm: "xset -q". Look for DPMS. Also there is "screen saver" there.
3. Execute in xterm: "xrandr --verbose". It shows other video settings.


P.S.
You know, I remembered that I had the same result one long time ago.
I will try to explain what happened: I turned dpms to ON, and then I turned monitor power off (I was not going to use my comp again soon). After some time I came back and found that I can't woke up my monitor. I thought that video chip disable video output because monitor was turned off. Since then I never turn monitor off - and never had this again.
May be in your case it is some kind of "save energy" function in your TV. You can for example execute "glxgear" in console and live it for a while.

---

### Post by Raymond_Uphoff on 2014-05-02
Hi,

I use one monitor and that's my TV. Xubuntu functions as a htpc.

xset -q will give unable to open display "";
```

raymond@htpc:~$ xset -q
xset:  unable to open display ""

raymond@htpc:~$ xset -display :0.0 q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  20
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x22    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins,/usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 7200    Suspend: 7200    Off: 60000
  DPMS is Disabled

```

xrandr --verbose 
```

raymond@htpc:~$ xrandr --verbose
Can't open display

```

---

### Post by macachuto on 2014-05-02
Then you can: "xrandr -d :0.0 --verbose.

Also please then your TV will disconnect again, change TTYx login with your name and password and type: "xrandr -d :0.0 --verbose". It should show you information about connectors.

---

### Post by Raymond_Uphoff on 2014-05-02
this is what it ouputs;
```

raymond@htpc:~$ xrandr -d :0.0 --verbose
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
VGA1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x43
    Timestamp:  267226730
    Subpixel:   unknown
    Clones:
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter:
HDMI1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x44
    Timestamp:  267226730
    Subpixel:   unknown
    Clones:
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter:
    Broadcast RGB: Automatic
        supported: Automatic, Full, Limited 16:235
    audio: auto
        supported: force-dvi, off, auto, on
HDMI2 connected (normal left inverted right x axis y axis)
    Identifier: 0x45
    Timestamp:  267226730
    Subpixel:   unknown
    Clones:
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter:
    EDID:
        00ffffffffffff00410c000001010101
        03140103808048780ae692a3544a9926
        0f4a4c2108008bc08180a94001010101
        010101010101023a801871382d40582c
        450000d05200001e023a80d072382d40
        102c458000d05200001e000000fc0050
        68696c697073204654560a20000000fd
        00303e0f4611000a20202020202001c9
        020331f152101f202221051404131203
        1102160715060126091f071507508301
        00006a030c002000382d802e2ee30503
        01011d803e73382d407e2c458000d052
        00001e011d80d0721c1620102c258000
        d05200009e011d00bc52d01e20b82855
        4000d05200001e011d8018711c162058
        2c250000d05200009e00000000000012
    Broadcast RGB: Automatic
        supported: Automatic, Full, Limited 16:235
    audio: auto
        supported: force-dvi, off, auto, on
  1920x1080 (0x4a)  148.5MHz +HSync +VSync +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz
  1920x1080 (0xb0)  148.5MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock   56.2KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   50.0Hz
  1920x1080 (0xb1)  148.4MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.4KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   59.9Hz
  1920x1080i (0xb2)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.8KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   60.1Hz
  1920x1080i (0xb3)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock   28.1KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   50.0Hz
  1920x1080 (0xb4)   74.2MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.8KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   30.0Hz
  1920x1080 (0xb5)   74.2MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock   28.1KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   25.0Hz
  1920x1080 (0xb6)   74.2MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock   27.0KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   24.0Hz
  1920x1080i (0xb7)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.7KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   60.0Hz
  1920x1080 (0xb8)   74.2MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.7KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   30.0Hz
  1920x1080 (0xb9)   74.2MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock   27.0KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   24.0Hz
  1600x1200 (0xba)  162.0MHz +HSync +VSync
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1280x1024 (0xbb)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1360x768 (0xbc)   84.8MHz -HSync +VSync
        h: width  1366 start 1431 end 1567 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1280x720 (0xbd)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1280x720 (0xbe)   74.2MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock   37.5KHz
        v: height  720 start  725 end  730 total  750           clock   50.0Hz
  1280x720 (0xbf)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   59.9Hz
  1440x576i (0xc0)   27.0MHz -HSync -VSync Interlace
        h: width  1440 start 1464 end 1590 total 1728 skew    0 clock   15.6KHz
        v: height  576 start  580 end  586 total  625           clock   50.1Hz
  1024x768 (0xc1)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  1440x480i (0xc2)   27.0MHz -HSync -VSync Interlace
        h: width  1440 start 1478 end 1602 total 1716 skew    0 clock   15.8KHz
        v: height  480 start  488 end  494 total  525           clock   60.1Hz
  1440x480i (0xc3)   27.0MHz -HSync -VSync Interlace
        h: width  1440 start 1478 end 1602 total 1716 skew    0 clock   15.7KHz
        v: height  480 start  488 end  494 total  525           clock   60.1Hz
  800x600 (0xc4)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  720x576 (0xc5)   27.0MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock   31.2KHz
        v: height  576 start  581 end  586 total  625           clock   50.0Hz
  720x480 (0xc6)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   60.0Hz
  720x480 (0xc7)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   59.9Hz
  640x480 (0xc8)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  640x480 (0xc9)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
DP1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x46
    Timestamp:  267226730
    Subpixel:   unknown
    Clones:
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter:
    Broadcast RGB: Automatic
        supported: Automatic, Full, Limited 16:235
    audio: auto
        supported: force-dvi, off, auto, on
DP2 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x47
    Timestamp:  267226730
    Subpixel:   unknown
    Clones:
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter:
    Broadcast RGB: Automatic
        supported: Automatic, Full, Limited 16:235
    audio: auto
        supported: force-dvi, off, auto, on
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x48
    Timestamp:  267226730
    Subpixel:   no subpixels
    Clones:
    CRTCs:      3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter:
raymond@htpc:~$

```

---

### Post by macachuto on 2014-05-02
I think I know where is a problem. This is mine output:
```

HDMI1 connected 1920x1200+0+0 (0x47) normal (normal left inverted right x axis y axis) 518mm x 324mm
        Identifier: 0x42
        Timestamp:  1332087
        Subpixel:   unknown
        Gamma:      1.0:1.1:1.2
        Brightness: 0.70
        Clones:    
        CRTC:       0
        CRTCs:      0 1
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
        EDID: 
                00ffffffffffff004c2d250833363133
                31170103803420782a73a1a4544d9926
                0f5054bfef80714f8100814081809500
                950fa940b300283c80a070b023403020
                360006442100001a000000fd00384b1e
                5111000a202020202020000000fc0053
                4d533234413835300a202020000000ff
                00484c4e444330303038370a202000d6
        Broadcast RGB: Automatic 
                supported: Automatic, Full, Limited 16:235
        audio: auto 
                supported: force-dvi, off, auto, on
  1920x1200 (0x47)  154.0MHz +HSync -VSync *current +preferred
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock   74.0KHz
        v: height 1200 start 1203 end 1209 total 1235           clock   60.0Hz

```
Most important part is:
```
1920x1200 (0x47)  154.0MHz +HSync -VSync *current +preferred
```
Yours doesn't have "*current". This might means that somehow X11 forgets about proper resolution and therefore your TV can't display anything.

Please, type and execute in console under current user:
xrandr -d :0.0 --output HDMI2 --mode 1920x1080
That should make mode "1920x1080" "*current"

---

### Post by Raymond_Uphoff on 2014-05-02
```

HDMI2 connected 1920x1080+0+0 (0x4a) normal (normal left inverted right x axis y axis) 1280mm x 720mm
    Identifier: 0x45
    Timestamp:  277775945
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:
    CRTC:       0
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter:
    EDID:
        00ffffffffffff00410c000001010101
        03140103808048780ae692a3544a9926
        0f4a4c2108008bc08180a94001010101
        010101010101023a801871382d40582c
        450000d05200001e023a80d072382d40
        102c458000d05200001e000000fc0050
        68696c697073204654560a20000000fd
        00303e0f4611000a20202020202001c9
        020331f152101f202221051404131203
        1102160715060126091f071507508301
        00006a030c002000382d802e2ee30503
        01011d803e73382d407e2c458000d052
        00001e011d80d0721c1620102c258000
        d05200009e011d00bc52d01e20b82855
        4000d05200001e011d8018711c162058
        2c250000d05200009e00000000000012
    Broadcast RGB: Automatic
        supported: Automatic, Full, Limited 16:235
    audio: auto
        supported: force-dvi, off, auto, on
  1920x1080 (0x4a)  148.5MHz +HSync +VSync *current +preferred

```

yep you're right! It also has the Gamma, Brightness and dimensions entries (mm) in output like you have. Okay and know what? What is a permanent fix? Bye the way I'm still running with the custom xorg.conf in /etc/X11/. If it got no use I'll ditch it.

---

### Post by macachuto on 2014-05-02
Can I see your xorg.conf?

---

### Post by Raymond_Uphoff on 2014-05-03
```

raymond@htpc:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "DRI"                    # <str>
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "VSync"                  # [<bool>]
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "ReprobeOutputs"         # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "VirtualHeads"           # <i>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "ServerFlags"
    Option "blank time"    "0"
    Option "standby time"    "0"
    Option "suspend time"    "0"
    Option "off time"    "0"
    Option "dpms"        "false"
EndSection
raymond@htpc:~$

```

---

### Post by macachuto on 2014-05-03
What I suggest to do next.
Rename xorg.conf to xorg_conf
Make new directory in root console: mkdir /etc/X11/xorg.conf.d
Make new file in root console: touch /etc/X11/xorg.conf.d/10-monitor.conf
And put the follow to 10-monitor.conf as root:
```

Section "Monitor"
    Identifier          "HDMI2"
    Option              "PreferredMode"         "1920x1080"    
EndSection

Section "Device"
    Identifier          "Card0"
    Driver              "intel"
    BusID               "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier          "Screen0"
    Device              "Card0"
    Monitor             "HDMI2"
EndSection

Section "ServerLayout"
    Identifier          "Main Layout"
    Screen             "Screen0"
EndSection

```

Then you have to logout and login. Then execute in user console: "xrandr -d :0.0 --verbose". I hope that you will see "*current" in modeset.
If something will go wrong - change TTY login and rename "10-monitor.conf" to "10-monitor_conf", and then reboot because I do not know how to restart X on different TTY.

---

### Post by Raymond_Uphoff on 2014-05-03
Did that! It's going okay! I see "1920x1080 (0x4a)  148.5MHz +HSync +VSync *current +preferred" Let's hope this works. Muchos thanks!

---

### Post by macachuto on 2014-05-03
> **Raymond_Uphoff said:**
> Did that! It's going okay! I see "1920x1080 (0x4a)  148.5MHz +HSync +VSync *current +preferred" Let's hope this works. Muchos thanks!

De nada.

---

### Post by Raymond_Uphoff on 2014-05-04
@Macachuto, it doesn't work! Big disappointment. *current is gone again! ```
 1920x1080 (0x4a)  148.5MHz +HSync +VSync +preferred
```

---

### Post by macachuto on 2014-05-04
What happened. Can you describe what exactly happened?
Did you just left you machine for a while or what?
What was in /var/log/Xorg.0.log.

Lets play with it - when next time you notice that your screen is out, change TTY and check /var/log/Xorg.0.log.
After this, type "xrandr -d :0.0 --output HDMI2 --mode 1920x1080", then change tty to 7 and check if you can see picture.

Can you please, show us part with " intel(0): Modeline ..." or something like this, you will add it to config.

---

### Post by Raymond_Uphoff on 2014-05-04
Yep I left it on for a while but thisa morning I got the same. I thought "Well okay I didn't reboot but a restart of lightdm". So I gave xubuntu a reboot. When I came back from biking I turned on the TV and bammm again 'No signal'. So then I went out to fiddle something myself. I read in an article [http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/](http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/) you can insert 'Modeline' in Section "Monitor". Modeline is;
```

raymond@htpc:~$ gtf 1920 1080 60

  # 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync

```
I've add that to Section "Monitor" in 10-monitor.conf
So now 10-monitor.conf looks like this;
```

raymond@htpc:~$ cat /etc/X11/xorg.conf.d/10-monitor.conf
Section "Monitor"
    Identifier    "HDMI2"
    #Option        "PreferredMode"        "1920x1080_60.00"
    Modeline     "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection

Section "Device"
    Identifier    "Card0"
    Driver        "intel"
    BusID        "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "HDMI2"
    Monitor        "HDMI2"
    DefaultDepth    24
    SubSection    "Display"
        Depth        24
        Modes        "1920x1080_60.00" "1280x720_60.00"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Main Layout"
    Screen        "Screen0"
EndSection
raymond@htpc:~$

```

I've reboot Xubuntu and got Graphical Interface so that's okay. But don't know if it solves it. Current Xorg.0.log is;
```

raymond@htpc:~$ cat /var/log/Xorg.0.log
[     9.474]
X.Org X Server 1.15.1
Release Date: 2014-04-13
[     9.474] X Protocol Version 11, Revision 0
[     9.474] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[     9.474] Current Operating System: Linux htpc 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64
[     9.474] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=UUID=2a88eb44-bc18-411c-be30-8b67e3f79666 ro nomdmonddf nomdmonisw
[     9.474] Build Date: 16 April 2014  01:36:29PM
[     9.474] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support)
[     9.474] Current version of pixman: 0.30.2
[     9.474]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     9.474] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.474] (==) Log file: "/var/log/Xorg.0.log", Time: Sun May  4 18:35:26 2014
[     9.478] (==) Using config directory: "/etc/X11/xorg.conf.d"
[     9.478] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.478] (==) ServerLayout "Main Layout"
[     9.478] (**) |-->Screen "Screen0" (0)
[     9.478] (**) |   |-->Monitor "HDMI2"
[     9.478] (==) No device specified for screen "Screen0".
    Using the first device section listed.
[     9.478] (**) |   |-->Device "Card0"
[     9.478] (==) Automatically adding devices
[     9.478] (==) Automatically enabling devices
[     9.478] (==) Automatically adding GPU devices
[     9.478] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.478]     Entry deleted from font path.
[     9.478] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.478]     Entry deleted from font path.
[     9.478] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.478]     Entry deleted from font path.
[     9.479] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.479]     Entry deleted from font path.
[     9.479] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.479]     Entry deleted from font path.
[     9.479] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     9.479] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.479] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.479] (II) Loader magic: 0x7f20b716fd60
[     9.479] (II) Module ABI versions:
[     9.479]     X.Org ANSI C Emulation: 0.4
[     9.479]     X.Org Video Driver: 15.0
[     9.479]     X.Org XInput driver : 20.0
[     9.479]     X.Org Server Extension : 8.0
[     9.479] (II) xfree86: Adding drm device (/dev/dri/card0)
[     9.480] (--) PCI:*(0:0:2:0) 8086:0152:1043:84ca rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[     9.480] Initializing built-in extension Generic Event Extension
[     9.480] Initializing built-in extension SHAPE
[     9.480] Initializing built-in extension MIT-SHM
[     9.480] Initializing built-in extension XInputExtension
[     9.480] Initializing built-in extension XTEST
[     9.480] Initializing built-in extension BIG-REQUESTS
[     9.480] Initializing built-in extension SYNC
[     9.480] Initializing built-in extension XKEYBOARD
[     9.480] Initializing built-in extension XC-MISC
[     9.480] Initializing built-in extension SECURITY
[     9.480] Initializing built-in extension XINERAMA
[     9.480] Initializing built-in extension XFIXES
[     9.480] Initializing built-in extension RENDER
[     9.480] Initializing built-in extension RANDR
[     9.480] Initializing built-in extension COMPOSITE
[     9.480] Initializing built-in extension DAMAGE
[     9.480] Initializing built-in extension MIT-SCREEN-SAVER
[     9.480] Initializing built-in extension DOUBLE-BUFFER
[     9.480] Initializing built-in extension RECORD
[     9.480] Initializing built-in extension DPMS
[     9.480] Initializing built-in extension Present
[     9.480] Initializing built-in extension DRI3
[     9.480] Initializing built-in extension X-Resource
[     9.480] Initializing built-in extension XVideo
[     9.480] Initializing built-in extension XVideo-MotionCompensation
[     9.480] Initializing built-in extension SELinux
[     9.480] Initializing built-in extension XFree86-VidModeExtension
[     9.480] Initializing built-in extension XFree86-DGA
[     9.480] Initializing built-in extension XFree86-DRI
[     9.480] Initializing built-in extension DRI2
[     9.480] (II) LoadModule: "glx"
[     9.481] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     9.499] (II) Module glx: vendor="X.Org Foundation"
[     9.499]     compiled for 1.15.1, module version = 1.0.0
[     9.499]     ABI class: X.Org Server Extension, version 8.0
[     9.499] (==) AIGLX enabled
[     9.499] Loading extension GLX
[     9.499] (II) LoadModule: "intel"
[     9.499] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     9.500] (II) Module intel: vendor="X.Org Foundation"
[     9.500]     compiled for 1.15.0, module version = 2.99.910
[     9.500]     Module class: X.Org Video Driver
[     9.500]     ABI class: X.Org Video Driver, version 15.0
[     9.500] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     9.500] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[     9.500] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[     9.500] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[     9.500] (++) using VT number 7

[     9.500] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>)
[     9.501] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 2500
[     9.501] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[     9.501] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[     9.501] (==) intel(0): RGB weight 888
[     9.501] (==) intel(0): Default visual is TrueColor
[     9.501] (**) intel(0): Framebuffer tiled
[     9.501] (**) intel(0): Pixmaps tiled
[     9.501] (**) intel(0): "Tear free" disabled
[     9.501] (**) intel(0): Forcing per-crtc-pixmaps? no
[     9.501] (II) intel(0): Output VGA1 using monitor section HDMI2
[     9.501] (II) intel(0): Output HDMI1 has no monitor section
[     9.501] (II) intel(0): Output HDMI2 using monitor section HDMI2
[     9.501] (II) intel(0): Output DP1 has no monitor section
[     9.501] (II) intel(0): Output DP2 has no monitor section
[     9.501] (II) intel(0): Output VIRTUAL1 has no monitor section
[     9.502] (II) intel(0): EDID for output VGA1
[     9.502] (II) intel(0): EDID for output HDMI1
[     9.552] (II) intel(0): EDID for output HDMI2
[     9.552] (II) intel(0): Manufacturer: PHL  Model: 0  Serial#: 16843009
[     9.552] (II) intel(0): Year: 2010  Week: 3
[     9.552] (II) intel(0): EDID Version: 1.3
[     9.552] (II) intel(0): Digital Display Input
[     9.552] (II) intel(0): Max Image Size [cm]: horiz.: 128  vert.: 72
[     9.552] (II) intel(0): Gamma: 2.20
[     9.552] (II) intel(0): No DPMS capabilities specified
[     9.552] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[     9.552] (II) intel(0): First detailed timing is preferred mode
[     9.552] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.290 greenY: 0.600
[     9.552] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.289 whiteY: 0.299
[     9.552] (II) intel(0): Supported established timings:
[     9.552] (II) intel(0): 640x480@60Hz
[     9.552] (II) intel(0): 800x600@60Hz
[     9.552] (II) intel(0): 1024x768@60Hz
[     9.552] (II) intel(0): Manufacturer's mask: 0
[     9.552] (II) intel(0): Supported standard timings:
[     9.552] (II) intel(0): #0: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[     9.552] (II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     9.552] (II) intel(0): #2: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[     9.552] (II) intel(0): Supported detailed timing:
[     9.552] (II) intel(0): clock: 148.5 MHz   Image Size:  1280 x 720 mm
[     9.552] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     9.552] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     9.552] (II) intel(0): Supported detailed timing:
[     9.552] (II) intel(0): clock: 148.5 MHz   Image Size:  1280 x 720 mm
[     9.552] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[     9.552] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     9.552] (II) intel(0): Monitor name: Philips FTV
[     9.552] (II) intel(0): Ranges: V min: 48 V max: 62 Hz, H min: 15 H max: 70 kHz, PixClock max 175 MHz
[     9.552] (II) intel(0): Supported detailed timing:
[     9.552] (II) intel(0): clock: 74.2 MHz   Image Size:  1280 x 720 mm
[     9.552] (II) intel(0): h_active: 1920  h_sync: 2558  h_sync_end 2602 h_blank_end 2750 h_border: 0
[     9.552] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     9.552] (II) intel(0): Supported detailed timing:
[     9.552] (II) intel(0): clock: 74.2 MHz   Image Size:  1280 x 720 mm
[     9.552] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[     9.552] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     9.552] (II) intel(0): Supported detailed timing:
[     9.552] (II) intel(0): clock: 74.2 MHz   Image Size:  1280 x 720 mm
[     9.552] (II) intel(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[     9.552] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[     9.552] (II) intel(0): Supported detailed timing:
[     9.552] (II) intel(0): clock: 74.2 MHz   Image Size:  1280 x 720 mm
[     9.552] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     9.552] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     9.553] (II) intel(0): Number of EDID sections to follow: 1
[     9.553] (II) intel(0): EDID (in hex):
[     9.553] (II) intel(0):     00ffffffffffff00410c000001010101
[     9.553] (II) intel(0):     03140103808048780ae692a3544a9926
[     9.553] (II) intel(0):     0f4a4c2108008bc08180a94001010101
[     9.553] (II) intel(0):     010101010101023a801871382d40582c
[     9.553] (II) intel(0):     450000d05200001e023a80d072382d40
[     9.553] (II) intel(0):     102c458000d05200001e000000fc0050
[     9.553] (II) intel(0):     68696c697073204654560a20000000fd
[     9.553] (II) intel(0):     00303e0f4611000a20202020202001c9
[     9.553] (II) intel(0):     020331f152101f202221051404131203
[     9.553] (II) intel(0):     1102160715060126091f071507508301
[     9.553] (II) intel(0):     00006a030c002000382d802e2ee30503
[     9.553] (II) intel(0):     01011d803e73382d407e2c458000d052
[     9.553] (II) intel(0):     00001e011d80d0721c1620102c258000
[     9.553] (II) intel(0):     d05200009e011d00bc52d01e20b82855
[     9.553] (II) intel(0):     4000d05200001e011d8018711c162058
[     9.553] (II) intel(0):     2c250000d05200009e00000000000012
[     9.553] (II) intel(0): Printing probed modes for output HDMI2
[     9.553] (II) intel(0): Modeline "1920x1080_60.00"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz UP)
[     9.553] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     9.553] (II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[     9.553] (II) intel(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[     9.553] (II) intel(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     9.553] (II) intel(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[     9.553] (II) intel(0): Modeline "1920x1080"x30.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[     9.553] (II) intel(0): Modeline "1920x1080"x25.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[     9.553] (II) intel(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     9.553] (II) intel(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[     9.553] (II) intel(0): Modeline "1920x1080"x30.0   74.18  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.7 kHz e)
[     9.553] (II) intel(0): Modeline "1920x1080"x24.0   74.18  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     9.553] (II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[     9.553] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     9.553] (II) intel(0): Modeline "1360x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[     9.553] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     9.553] (II) intel(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     9.553] (II) intel(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     9.553] (II) intel(0): Modeline "1440x576i"x50.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     9.553] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     9.553] (II) intel(0): Modeline "1440x480i"x60.0   27.03  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.8 kHz e)
[     9.553] (II) intel(0): Modeline "1440x480i"x59.9   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     9.553] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     9.553] (II) intel(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     9.553] (II) intel(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     9.553] (II) intel(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     9.553] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     9.553] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     9.553] (II) intel(0): EDID for output DP1
[     9.576] (II) intel(0): EDID for output DP2
[     9.576] (II) intel(0): EDID for output VIRTUAL1
[     9.576] (II) intel(0): Output VGA1 disconnected
[     9.576] (II) intel(0): Output HDMI1 disconnected
[     9.576] (II) intel(0): Output HDMI2 connected
[     9.576] (II) intel(0): Output DP1 disconnected
[     9.576] (II) intel(0): Output DP2 disconnected
[     9.576] (II) intel(0): Output VIRTUAL1 disconnected
[     9.576] (II) intel(0): Using user preference for initial modes
[     9.576] (II) intel(0): Output HDMI2 using initial mode 1920x1080_60.00
[     9.576] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     9.576] (==) intel(0): DPI set to (96, 96)
[     9.576] (II) Loading sub module "dri2"
[     9.576] (II) LoadModule: "dri2"
[     9.576] (II) Module "dri2" already built-in
[     9.576] (==) Depth 24 pixmap format is 32 bpp
[     9.576] (II) intel(0): SNA initialized with Ivybridge (gen7, gt1) backend
[     9.576] (==) intel(0): Backing store enabled
[     9.576] (==) intel(0): Silken mouse enabled
[     9.576] (II) intel(0): HW Cursor enabled
[     9.576] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     9.576] (==) intel(0): DPMS enabled
[     9.576] (II) intel(0): [DRI2] Setup complete
[     9.576] (II) intel(0): [DRI2]   DRI driver: i965
[     9.576] (II) intel(0): [DRI2]   VDPAU driver: i965
[     9.576] (II) intel(0): direct rendering: DRI2 Enabled
[     9.576] (==) intel(0): hotplug detection: "enabled"
[     9.576] (--) RandR disabled
[     9.580] (II) SELinux: Disabled on system
[     9.583] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     9.583] (II) AIGLX: enabled GLX_ARB_create_context
[     9.583] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     9.583] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     9.583] (II) AIGLX: enabled GLX_INTEL_swap_event
[     9.583] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     9.583] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     9.583] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     9.583] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     9.583] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[     9.583] (II) AIGLX: Loaded and initialized i965
[     9.583] (II) GLX: Initialized DRI2 GL provider for screen 0
[     9.585] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 0, position (0, 0), rotation normal, reflection none
[     9.792] (II) intel(0): Setting screen physical size to 508 x 285
[     9.799] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     9.800] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     9.800] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     9.800] (II) LoadModule: "evdev"
[     9.801] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.802] (II) Module evdev: vendor="X.Org Foundation"
[     9.802]     compiled for 1.15.0, module version = 2.8.2
[     9.802]     Module class: X.Org XInput Driver
[     9.802]     ABI class: X.Org XInput driver, version 20.0
[     9.802] (II) Using input driver 'evdev' for 'Power Button'
[     9.802] (**) Power Button: always reports core events
[     9.802] (**) evdev: Power Button: Device: "/dev/input/event1"
[     9.802] (--) evdev: Power Button: Vendor 0 Product 0x1
[     9.802] (--) evdev: Power Button: Found keys
[     9.802] (II) evdev: Power Button: Configuring as keyboard
[     9.802] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     9.802] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     9.802] (**) Option "xkb_rules" "evdev"
[     9.802] (**) Option "xkb_model" "pc105"
[     9.802] (**) Option "xkb_layout" "us"
[     9.802] (**) Option "xkb_variant" "intl"
[     9.803] (II) XKB: reuse xkmfile /var/lib/xkb/server-A5431D4A34463C892C9E905E2E421B30A3CC30DD.xkm
[     9.804] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[     9.804] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     9.804] (II) Using input driver 'evdev' for 'Video Bus'
[     9.804] (**) Video Bus: always reports core events
[     9.804] (**) evdev: Video Bus: Device: "/dev/input/event6"
[     9.804] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     9.804] (--) evdev: Video Bus: Found keys
[     9.804] (II) evdev: Video Bus: Configuring as keyboard
[     9.804] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9/event6"
[     9.804] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     9.804] (**) Option "xkb_rules" "evdev"
[     9.804] (**) Option "xkb_model" "pc105"
[     9.804] (**) Option "xkb_layout" "us"
[     9.804] (**) Option "xkb_variant" "intl"
[     9.804] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     9.804] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     9.804] (II) Using input driver 'evdev' for 'Power Button'
[     9.804] (**) Power Button: always reports core events
[     9.804] (**) evdev: Power Button: Device: "/dev/input/event0"
[     9.804] (--) evdev: Power Button: Vendor 0 Product 0x1
[     9.804] (--) evdev: Power Button: Found keys
[     9.804] (II) evdev: Power Button: Configuring as keyboard
[     9.804] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     9.804] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     9.804] (**) Option "xkb_rules" "evdev"
[     9.804] (**) Option "xkb_model" "pc105"
[     9.804] (**) Option "xkb_layout" "us"
[     9.804] (**) Option "xkb_variant" "intl"
[     9.805] (II) config/udev: Adding drm device (/dev/dri/card0)
[     9.805] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     9.805] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[     9.805] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[     9.805] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[     9.805] (**) Logitech USB Receiver: always reports core events
[     9.805] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event2"
[     9.805] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc521
[     9.805] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[     9.805] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[     9.805] (--) evdev: Logitech USB Receiver: Found relative axes
[     9.805] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[     9.805] (II) evdev: Logitech USB Receiver: Configuring as mouse
[     9.805] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[     9.805] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[     9.805] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     9.805] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input4/event2"
[     9.805] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 9)
[     9.805] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[     9.805] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[     9.805] (**) Logitech USB Receiver: (accel) acceleration profile 0
[     9.805] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[     9.805] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[     9.805] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[     9.805] (II) No input driver specified, ignoring this device.
[     9.805] (II) This device may have been added with another device file.
[     9.806] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[     9.806] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[     9.806] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[     9.806] (**) Logitech USB Receiver: always reports core events
[     9.806] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event3"
[     9.806] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc521
[     9.806] (--) evdev: Logitech USB Receiver: Found 1 mouse buttons
[     9.806] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[     9.806] (--) evdev: Logitech USB Receiver: Found relative axes
[     9.806] (II) evdev: Logitech USB Receiver: Forcing relative x/y axes to exist.
[     9.806] (--) evdev: Logitech USB Receiver: Found absolute axes
[     9.806] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[     9.806] (--) evdev: Logitech USB Receiver: Found keys
[     9.806] (II) evdev: Logitech USB Receiver: Configuring as mouse
[     9.806] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[     9.806] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[     9.806] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[     9.806] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     9.806] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.1/input/input6/event3"
[     9.806] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 10)
[     9.806] (**) Option "xkb_rules" "evdev"
[     9.806] (**) Option "xkb_model" "pc105"
[     9.806] (**) Option "xkb_layout" "us"
[     9.806] (**) Option "xkb_variant" "intl"
[     9.806] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[     9.806] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[     9.806] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[     9.806] (**) Logitech USB Receiver: (accel) acceleration profile 0
[     9.806] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[     9.806] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[     9.806] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:400d (/dev/input/event4)
[     9.806] (**) Logitech Unifying Device. Wireless PID:400d: Applying InputClass "evdev keyboard catchall"
[     9.806] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:400d'
[     9.806] (**) Logitech Unifying Device. Wireless PID:400d: always reports core events
[     9.806] (**) evdev: Logitech Unifying Device. Wireless PID:400d: Device: "/dev/input/event4"
[     9.806] (--) evdev: Logitech Unifying Device. Wireless PID:400d: Vendor 0x46d Product 0xc52b
[     9.806] (--) evdev: Logitech Unifying Device. Wireless PID:400d: Found 1 mouse buttons
[     9.806] (--) evdev: Logitech Unifying Device. Wireless PID:400d: Found scroll wheel(s)
[     9.806] (--) evdev: Logitech Unifying Device. Wireless PID:400d: Found relative axes
[     9.806] (II) evdev: Logitech Unifying Device. Wireless PID:400d: Forcing relative x/y axes to exist.
[     9.806] (--) evdev: Logitech Unifying Device. Wireless PID:400d: Found absolute axes
[     9.806] (II) evdev: Logitech Unifying Device. Wireless PID:400d: Forcing absolute x/y axes to exist.
[     9.806] (--) evdev: Logitech Unifying Device. Wireless PID:400d: Found keys
[     9.806] (II) evdev: Logitech Unifying Device. Wireless PID:400d: Configuring as mouse
[     9.806] (II) evdev: Logitech Unifying Device. Wireless PID:400d: Configuring as keyboard
[     9.806] (II) evdev: Logitech Unifying Device. Wireless PID:400d: Adding scrollwheel support
[     9.806] (**) evdev: Logitech Unifying Device. Wireless PID:400d: YAxisMapping: buttons 4 and 5
[     9.806] (**) evdev: Logitech Unifying Device. Wireless PID:400d: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     9.806] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:046D:C52B.0005/input/input5/event4"
[     9.806] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:400d" (type: KEYBOARD, id 11)
[     9.806] (**) Option "xkb_rules" "evdev"
[     9.806] (**) Option "xkb_model" "pc105"
[     9.806] (**) Option "xkb_layout" "us"
[     9.806] (**) Option "xkb_variant" "intl"
[     9.806] (II) evdev: Logitech Unifying Device. Wireless PID:400d: initialized for relative axes.
[     9.806] (WW) evdev: Logitech Unifying Device. Wireless PID:400d: ignoring absolute axes.
[     9.807] (**) Logitech Unifying Device. Wireless PID:400d: (accel) keeping acceleration scheme 1
[     9.807] (**) Logitech Unifying Device. Wireless PID:400d: (accel) acceleration profile 0
[     9.807] (**) Logitech Unifying Device. Wireless PID:400d: (accel) acceleration factor: 2.000
[     9.807] (**) Logitech Unifying Device. Wireless PID:400d: (accel) acceleration threshold: 4
[     9.807] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event12)
[     9.807] (II) No input driver specified, ignoring this device.
[     9.807] (II) This device may have been added with another device file.
[     9.807] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event11)
[     9.807] (II) No input driver specified, ignoring this device.
[     9.807] (II) This device may have been added with another device file.
[     9.807] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event10)
[     9.807] (II) No input driver specified, ignoring this device.
[     9.807] (II) This device may have been added with another device file.
[     9.807] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event9)
[     9.807] (II) No input driver specified, ignoring this device.
[     9.807] (II) This device may have been added with another device file.
[     9.807] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event8)
[     9.807] (II) No input driver specified, ignoring this device.
[     9.807] (II) This device may have been added with another device file.
[     9.808] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event7)
[     9.808] (II) No input driver specified, ignoring this device.
[     9.808] (II) This device may have been added with another device file.
[     9.808] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event5)
[     9.808] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     9.808] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     9.808] (**) Eee PC WMI hotkeys: always reports core events
[     9.808] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event5"
[     9.808] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     9.808] (--) evdev: Eee PC WMI hotkeys: Found keys
[     9.808] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     9.808] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input8/event5"
[     9.808] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 12)
[     9.808] (**) Option "xkb_rules" "evdev"
[     9.808] (**) Option "xkb_model" "pc105"
[     9.808] (**) Option "xkb_layout" "us"
[     9.808] (**) Option "xkb_variant" "intl"
[    22.734] (II) XKB: reuse xkmfile /var/lib/xkb/server-A5431D4A34463C892C9E905E2E421B30A3CC30DD.xkm
[    38.208] (II) XKB: reuse xkmfile /var/lib/xkb/server-C0F758F08C29987D1606E9D1EDAAA10FCB3B1818.xkm

```

---

### Post by macachuto on 2014-05-04
No. You should take modeline from Xorg.0.log:
Modeline "1920x1080"   148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync

So, monitor section will be:

Section "Monitor"     
        Identifier        "HDMI2"
        Modeline         "1920x1080_m"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync    
        Option               "PreferredMode"                "1920x1080_m"
EndSection

---

### Post by Raymond_Uphoff on 2014-05-04
I didn't. I got it from output of command 'gtf 1920 1080 60' see first dumped code-snippet in my previous post. Strange is Xorg.0.log has entries all with '+hsync' for 1920x1080. gtf says '-hsync' So modeline-entry is manual adding a resolution-setting.
Edit;
I've add the PrefferedMode option again and after a reboot it's current profile is the Modeline-entry. I kept the one that was dumped with gtf;
```

  1920x1080_M (0x4a)  172.8MHz -HSync +VSync *current +preferred
        h: width  1920 start 2040 end 2248 total 2576 skew    0 clock   67.1KHz
        v: height 1080 start 1081 end 1084 total 1118           clock   60.0Hz

```

---

### Post by macachuto on 2014-05-04
OK.
It has to be tested.

Tell, if it helps.

---

### Post by Raymond_Uphoff on 2014-05-05
Nope it doesn't! Same behaviour! '*current' is gone again for 1920x1080_M. Switching to TV or PS3 attached to resp. HDMI1 and HDMI3 give signal.

---

### Post by lulaz on 2014-05-05
I had a similar problem and i fixed it this way: (its just a workaround, not actual fix)

```
$ cat /etc/udev/rules.d/hdmi.rules 
KERNEL=="card0", ACTION=="change", RUN+="/home/.../fix.sh"
```

and the script:

```
$ cat /home/.../fix.sh 
#!/bin/bash
export XAUTHORITY="/home/.../.Xauthority"
export DISPLAY=":0.0"
xrandr --output HDMI1 --mode "1920x1080_60.00"
```

Of course you need to change ***card0***, ***HDMI1*** and ***"1920x1080_60.00"*** to match your setup.

---

### Post by Raymond_Uphoff on 2014-05-05
Okay done! Let's check if that works. I'll keep you posted!

---

### Post by macachuto on 2014-05-05
If this helps, that you have to fill a bug - because it is a bug and devs must fix it.

---

### Post by Raymond_Uphoff on 2014-05-06
Script doesn't work. I figured out how to check if system sees HDMI-port is connected or not. I physically removed HDMI-cable and system gives right output;
```

raymond@htpc:~$ cat /sys/class/drm/card0/card0-HDMI-A-2/status
connected
raymond@htpc:~$ cat /sys/class/drm/card0/card0-HDMI-A-2/status
disconnected
raymond@htpc:~$ cat /sys/class/drm/card0/card0-HDMI-A-2/status
connected

```

Now I'm trying to figure out how I can test if script is even running.

---

### Post by debdiesel on 2014-05-06
This thread and Raymond's experience is exactly, even to the point of what has not worked, is what I have been struggling with also.  I just wanted to make note of this that it is not an isolated Raymond-only type of issue.  I am using xubuntu as an htpc as well, upgraded to 14.04, and have to restart my display manager to get my X back...again, exactly like Raymond.

---

### Post by Raymond_Uphoff on 2014-05-06
Nice somebody with same issue. And that's why there are fora:D

[EDIT] Script works! the piped command ts in shell-script underneath will add timestamp to entries in logfile. 
```

raymond@htpc:~$ cat /etc/udev/rules.d/hdmi.rules
KERNEL=="card0", SUBSYSTEM=="drm", ACTION=="change", RUN+="/home/raymond/Scripts/hdmi_workaround.sh"
raymond@htpc:~$ cat Scripts/hdmi_workaround.sh
#!/bin/bash
#
export XAUTHORITY="/home/raymond/.Xauthority"
export DISPLAY=":0.0"
LOGFILE=/var/log/hdmi_workaround.log
#
xrandr --output HDMI2 --mode "1920x1080"
xrandr | grep "HDMI2 connected" 2>&1 | ts | tee --append $LOGFILE &

```

---

### Post by debdiesel on 2014-05-07
Raymond:

I found the following bug on launchpad: 

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105)

I know that this refers specifically to nvidia cards so it may or may not apply to you, but I wanted to mention that the last comment on this ticket states stopping xfsettingsd as a workaround.  This did indeed work for me.

---

### Post by Raymond_Uphoff on 2014-05-08
Hi debdiesel,

Do you every time this happens manually stop xfsettingsd or do you have some kind of script? Did you file a bug-report?

---

### Post by debdiesel on 2014-05-09
Raymond:

I just unchecked xfsettingsd from starting in the XFCE sessions dialog.  This will prevent xfsettingsd from starting when xfce first starts.

---

### Post by debdiesel on 2014-05-09
...and no, I did not submit a bug report as there is already one that I referenced earlier in this thread.

---

### Post by itlarson2 on 2014-06-04
I have this exact problem in Mythbuntu 14.04.  At first I thought the screensaver wasn't waking, but it turns out all I have to do to recreate the problem is turn the TV off then on again.  I will try the script when I have time to make sure I understand it.

---

### Post by nsummers on 2014-06-14
> **itlarson2 said:**
> I have this exact problem in Mythbuntu 14.04.  At first I thought the screensaver wasn't waking, but it turns out all I have to do to recreate the problem is turn the TV off then on again.  I will try the script when I have time to make sure I understand it.

I have the same problem too. xubuntu 14.04 installed as upgrade from 13.10. Monitor is connected via HDMI. Everytime I power off the monitor and turn it back on again, the screen does not wake up.

Thanks for the help, I have installed the scripts and the bash script works to modify with xrandr when I run the script, but putting the new rule in /etc/udev/rules.d/hdmi.rules does not seem to do it automatically. So I can only recover the monitor if I happen to have terminal open and can run the bash script sight unseen. Any ideas why adding the hdmi.rules to /etc/udev/rules.d/ is not automatically fixing the problem, when the current setting is dropped.

I have tried killing xfsettingsd, and this does fix it, but I would rather not have this not running as my desktop is then very ugly!

Edit: Trying to figure out what is going wrong.

Here is my rules
```
$ cat /etc/udev/rules.d/hdmi.rules 
KERNEL=="card0", SUBSYSTEM=="drm", ACTION=="change", RUN+="/home/neil/bin/hdmi_workaround.sh"

```

here is what happens when I monitor what happens when I switch off the monitor
```
$ sudo udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[7106.206266] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
UDEV  [7106.231214] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
```

So the kernel is registering the change, and I can run the script /home/neil/bin/hdmi_workaround.sh and it works to bring the monitor back, but it does not seem to happen automatically.

---

### Post by Raymond_Uphoff on 2014-06-21
First you should check to which device your machine is connected. The script is an example. configure it according to your hardware.

EDIT: @nsummers; who is the owner of hdmi.rules? Make it root when it isn't.

---

### Post by nsummers on 2014-06-21
> **Raymond_Uphoff said:**
> First you should check to which device your machine is connected. The script is an example. configure it according to your hardware.

EDIT: @nsummers; who is the owner of hdmi.rules? Make it root when it isn't.

I have configured the script to my hardware. I know it works as I can run the script in a terminal when the screen is blank and get the hdmi to work again. Permissions and ownership seem ok.
$ ls -l /etc/udev/rules.d/
-rw-r--r-- 1 root root   94 Jun 14 17:23 hdmi.rules

EDIT:
It is very strange, now it works, but not the first time. What I mean is that the screen is blank when I turn on the monitor, but if I turn it off and on again a second time it come back (but if I check xrandr it does not report the *current settings properly, but it still comes back).

What I do have now is that I started xfsettingsd in a terminal, and when I get this error I get the report

The program 'xfsettingsd' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRRCrtc (invalid Crtc parameter)'.
  (Details: serial 1021 error_code 148 request_code 140 minor_code 21)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I could do all of this and get the backtrace, but does anyone have a link to the a bug report for xfsettingsd?

---

### Post by obm2 on 2014-07-14
Not sure if this is the same problem, but I had a "No Signal" on my Onkyo amp (HDMI) and a blank screen (obviously) after power cycling the screen/amp..

This is what worked for me..
(about disabling HotplugEvents worked for me!)...

I edited /etc/X11/xorg.conf and added the line: [COLOR=#000000][FONT=Verdana]Option "UseHotplugEvents" "false"  to the Device section [/FONT][/COLOR]

> 
The tip from here: [http://www.gossamer-threads.com/lists/mythtv/users/570769](http://www.gossamer-threads.com/lists/mythtv/users/570769)
[COLOR=#000000][FONT=Verdana]
create a configuration with nvidia-xconfig if you haven't done so [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]then add to the "Device" section: [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Option "UseHotplugEvents" "false" 
[/FONT][/COLOR]

For what it's worth: I'm using this as a HTPC, so I'm running the latest mythbuntu with lightdm, on an AsRock ION-3D.. I uninstalled the ubuntu nvidia drivers, and ran the latest proprietary nvidia driver install. I have also disabled all screensavers, and display power management. 

So for me, 14.04 is running well now!

---

### Post by kzq-luaas-x8o on 2014-09-05
> **Raymond_Uphoff said:**
> I've updated Xubuntu from 13.10 to 14.04 and it all went well. Reboot the system and login-screen. I filled out my password and voila 14.04 up and running. But now comes the but; The TV switch to No singal after a while and it wouldn't switch back on by mouse or keyboard. I've got a Ivy-Bridge i3 running Intel Graphics connected to a Philips LCD TV by HDMI 

I had same issuses with a HDMI-Switcher. I solved this by creating a xorg.conf and added  ' Option "Hotplug" "false" ' in the device section. I'm also using the Intel driver.

Yours, Klaus

---

### Post by stanton on 2014-11-08
> **obm2 said:**
> Not sure if this is the same problem, but I had a "No Signal" on my Onkyo amp (HDMI) and a blank screen (obviously) after power cycling the screen/amp..

This is what worked for me..
(about disabling HotplugEvents worked for me!)...

I edited /etc/X11/xorg.conf and added the line: [COLOR=#000000][FONT=Verdana]Option "UseHotplugEvents" "false"  to the Device section [/FONT][/COLOR]

For what it's worth: I'm using this as a HTPC, so I'm running the latest mythbuntu with lightdm, on an AsRock ION-3D.. I uninstalled the ubuntu nvidia drivers, and ran the latest proprietary nvidia driver install. I have also disabled all screensavers, and display power management. 

So for me, 14.04 is running well now!

This worked for me too!  I have been searching for a week for a solution to this frustrating 'feature' in 14.04.

---

### Post by jakommo on 2014-11-23
> **stanton said:**
> This worked for me too!  I have been searching for a week for a solution to this frustrating 'feature' in 14.04.

It could also be caused by this bug: [https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1313539](https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1313539)
Following comment #7 and downgrading xfce4-settings to saucy's package fixed it on my mythbuntu 14.04 machine without touching xorg.conf.

---

