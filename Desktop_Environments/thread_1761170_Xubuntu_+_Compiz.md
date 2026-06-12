---
title: "Xubuntu + Compiz"
date: 2011-05-17
forum: Desktop Environments
---

### Post by riramar on 2011-05-17
I'm not sure that here is the right place, but lets go there. :D
I’ve just did a xubuntu 11.04 fresh install and try to install compiz  following this post ([http://askubuntu.com/questions/8270/how-do-i-install-compiz-in-xubuntu](http://askubuntu.com/questions/8270/how-do-i-install-compiz-in-xubuntu)). Everything is OK until I tried to run “compiz  –replace”. Anyone can help me? Please find below the command output. It's look like a Emerald problem but it didn't get much information.

```
ricardo@optimus:~$ compiz –replace
 Checking if settings need to be migrated …no
Checking if internal files need to be migrated …no
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options…done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options…done
Initializing detection options…done
Initializing composite options…done
Initializing opengl options…done
Initializing decor options…done
Initializing mousepoll options…done
Initializing vpswitch options…done
Initializing animation options…done
Initializing snap options…done
Initializing expo options…done
Initializing move options…done
Initializing place options…done
Initializing grid options…done
Initializing gnomecompat options…done
Initializing wall options…done
Initializing ezoom options…done
Initializing workarounds options…done
Initializing staticswitcher options…done
Initializing resize options…done
Initializing fade options…done
Initializing scale options…done
Initializing session options…done
Window 0x2a00284 created on ReparentNotify, map state isViewable? 0
Window 0x32001d2 created on ReparentNotify, map state isViewable? 0
Window 0x1a00330 created on ReparentNotify, map state isViewable? 0
Window 0x2a00336 created on ReparentNotify, map state isViewable? 0
Window 0x320025a created on ReparentNotify, map state isViewable? 0
Window 0x1a00379 created on ReparentNotify, map state isViewable? 0
Couldn’t find a perfect decorator match; trying all decorators
Starting emerald
Segmentation fault

```

---

### Post by hhh on 2011-05-17
Do you even know if your computer has a video card that will run Compiz? See this page...
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Also, which method on that page you linked did you use?

---

### Post by riramar on 2011-05-18
I didn't know about this script. Thanks for the tip! I run the script and got these messages:

```

ricardo@optimus:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 11.04
 Desktop environment:   Xfce
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) 

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) 
ricardo@optimus:~$ 

```Then the script opened the Additional Drivers window that I could see only extra drivers for my wifi network interface, take a look:

[IMG]http://oi53.tinypic.com/33xbsja.jpg[/IMG]

I'm quite sure that I'm using the driver for my interface graphic interface called "i915". Take a look in my lsmod output:

```

ricardo@optimus:~$ lsmod 
Module                  Size  Used by
michael_mic            12540  8 
arc4                   12473  4 
parport_pc             32111  0 
ppdev                  12849  0 
rfcomm                 38125  12 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
btusb                  18160  2 
snd_hda_codec_idt      60537  1 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
joydev                 17322  0 
snd_hda_intel          24140  3 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
dell_laptop            13515  0 
snd_timer              28659  2 snd_pcm,snd_seq
i915                  450944  2 
dell_wmi               12601  0 
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
sparse_keymap          13666  1 dell_wmi
lib80211_crypt_tkip    17203  0 
drm                   180037  3 i915,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14054  1 dell_laptop
wl                   2642531  0 
videodev               75143  1 uvcvideo
snd                    55295  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
uas                    17676  0 
ahci                   21591  3 
libahci                25548  1 ahci
sky2                   49172  0 
ricardo@optimus:~$

```Talking about the method I've just run these three commands below to install and start compiz.

```

compiz is not installed on xubuntu for reasons of lightness but it can be installed[INDENT]   sudo apt-get install compiz-core   compiz-plugins   compiz-fusion-plugins-main   compiz-fusion-plugins-extra
 [/INDENT]change to compiz :[INDENT]   compiz--replace
 [/INDENT]install compiz setting manager too :[INDENT]   sudo install compizconfig-settings-manager
 [/INDENT]you can find **compizconfig-settings-manager** in **System -> Preference** 
 

```Thanks a lot for your help!
Ricardo

---

### Post by hhh on 2011-05-19
I'm away for the weekend so sorry for the delay...> The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. Looks like you can't run compiz. :( One last chance, what's your graphics card?

---

### Post by riramar on 2011-05-19
Don't worry about the delay, you are help me and I don't have to pay anything. :D

I have a dell inspiron laptop with intel graphic board, take a look to the model:

```

ricardo@optimus:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
ricardo@optimus:~$ 

```

Before I install Xubuntu I used Ubuntu 10.04 with compiz and there wasn't problems. So I upgraded to 11.04 (Unity) but I really didn't like then I decided to use Xubuntu.
I'm attaching the X logs and conf files just to see with helps you to help me. The X conf file I've just generated using the command "X -configure" and move to /etc/X11/.

/var/log/Xorg.0.log
```

[    11.238] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    11.238] X Protocol Version 11, Revision 0
[    11.238] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    11.238] Current Operating System: Linux optimus 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    11.238] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=ed578dd4-4ffb-45cf-b461-a6499085e8a7 ro quiet splash vt.handoff=7
[    11.238] Build Date: 19 April 2011  03:33:17PM
[    11.238] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    11.238] Current version of pixman: 0.20.2
[    11.238]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    11.238] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.239] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 19 20:33:19 2011
[    11.239] (==) Using config file: "/etc/X11/xorg.conf"
[    11.239] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.239] (==) ServerLayout "X.org Configured"
[    11.239] (**) |-->Screen "Screen0" (0)
[    11.239] (**) |   |-->Monitor "Monitor0"
[    11.239] (**) |   |-->Device "Card0"
[    11.239] (**) |-->Screen "Screen1" (1)
[    11.239] (**) |   |-->Monitor "Monitor1"
[    11.240] (**) |   |-->Device "Card1"
[    11.240] (**) |-->Screen "Screen2" (2)
[    11.240] (**) |   |-->Monitor "Monitor2"
[    11.240] (**) |   |-->Device "Card2"
[    11.240] (**) |-->Input Device "Mouse0"
[    11.240] (**) |-->Input Device "Keyboard0"
[    11.240] (==) Automatically adding devices
[    11.240] (==) Automatically enabling devices
[    11.240] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.240]     Entry deleted from font path.
[    11.240] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.240]     Entry deleted from font path.
[    11.240] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.240]     Entry deleted from font path.
[    11.240] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.240]     Entry deleted from font path.
[    11.240] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.240]     Entry deleted from font path.
[    11.240] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.240]     Entry deleted from font path.
[    11.240] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.240]     Entry deleted from font path.
[    11.240] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.240]     Entry deleted from font path.
[    11.240] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.240]     Entry deleted from font path.
[    11.240] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.240]     Entry deleted from font path.
[    11.241] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    11.241] (**) ModulePath set to "/usr/lib/xorg/modules"
[    11.241] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    11.241] (WW) Disabling Mouse0
[    11.241] (WW) Disabling Keyboard0
[    11.241] (II) Loader magic: 0x81ffde0
[    11.241] (II) Module ABI versions:
[    11.241]     X.Org ANSI C Emulation: 0.4
[    11.241]     X.Org Video Driver: 10.0
[    11.241]     X.Org XInput driver : 12.3
[    11.241]     X.Org Server Extension : 5.0
[    11.242] (--) PCI:*(0:0:2:0) 8086:2a42:1028:02aa rev 7, Mem @ 0xf6c00000/4194304, 0xe0000000/268435456, I/O @ 0x0000efe8/8
[    11.242] (--) PCI: (0:0:2:1) 8086:2a43:1028:02aa rev 7, Mem @ 0xf6b00000/1048576
[    11.242] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.242] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    11.242] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    11.242] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    11.242] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    11.242] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    11.242] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    11.242] (II) LoadModule: "record"
[    11.316] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.316] (II) Module record: vendor="X.Org Foundation"
[    11.316]     compiled for 1.10.1, module version = 1.13.0
[    11.316]     Module class: X.Org Server Extension
[    11.316]     ABI class: X.Org Server Extension, version 5.0
[    11.316] (II) Loading extension RECORD
[    11.316] (II) LoadModule: "extmod"
[    11.316] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.316] (II) Module extmod: vendor="X.Org Foundation"
[    11.316]     compiled for 1.10.1, module version = 1.0.0
[    11.316]     Module class: X.Org Server Extension
[    11.316]     ABI class: X.Org Server Extension, version 5.0
[    11.316] (II) Loading extension MIT-SCREEN-SAVER
[    11.316] (II) Loading extension XFree86-VidModeExtension
[    11.316] (II) Loading extension XFree86-DGA
[    11.316] (II) Loading extension DPMS
[    11.316] (II) Loading extension XVideo
[    11.316] (II) Loading extension XVideo-MotionCompensation
[    11.316] (II) Loading extension X-Resource
[    11.316] (II) LoadModule: "dbe"
[    11.317] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.317] (II) Module dbe: vendor="X.Org Foundation"
[    11.317]     compiled for 1.10.1, module version = 1.0.0
[    11.317]     Module class: X.Org Server Extension
[    11.317]     ABI class: X.Org Server Extension, version 5.0
[    11.317] (II) Loading extension DOUBLE-BUFFER
[    11.317] (II) LoadModule: "glx"
[    11.317] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.318] (II) Module glx: vendor="X.Org Foundation"
[    11.318]     compiled for 1.10.1, module version = 1.0.0
[    11.318]     ABI class: X.Org Server Extension, version 5.0
[    11.318] (==) AIGLX enabled
[    11.318] (II) Loading extension GLX
[    11.318] (II) LoadModule: "dri"
[    11.318] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.318] (II) Module dri: vendor="X.Org Foundation"
[    11.318]     compiled for 1.10.1, module version = 1.0.0
[    11.318]     ABI class: X.Org Server Extension, version 5.0
[    11.318] (II) Loading extension XFree86-DRI
[    11.318] (II) LoadModule: "dri2"
[    11.319] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.319] (II) Module dri2: vendor="X.Org Foundation"
[    11.319]     compiled for 1.10.1, module version = 1.2.0
[    11.319]     ABI class: X.Org Server Extension, version 5.0
[    11.319] (II) Loading extension DRI2
[    11.319] (II) LoadModule: "intel"
[    11.319] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    11.319] (II) Module intel: vendor="X.Org Foundation"
[    11.319]     compiled for 1.10.1, module version = 2.14.0
[    11.319]     Module class: X.Org Video Driver
[    11.319]     ABI class: X.Org Video Driver, version 10.0
[    11.319] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    11.320] (++) using VT number 7

[    11.322] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    11.322] drmOpenDevice: node name is /dev/dri/card0
[    11.322] drmOpenDevice: open result is 9, (OK)
[    11.322] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    11.322] drmOpenDevice: node name is /dev/dri/card0
[    11.322] drmOpenDevice: open result is 9, (OK)
[    11.322] drmOpenByBusid: drmOpenMinor returns 9
[    11.322] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    11.322] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    11.322] (==) intel(0): RGB weight 888
[    11.322] (==) intel(0): Default visual is TrueColor
[    11.322] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    11.322] (--) intel(0): Chipset: "GM45"
[    11.322] (**) intel(0): Relaxed fencing enabled
[    11.322] (**) intel(0): Tiling enabled
[    11.323] (**) intel(0): SwapBuffers wait enabled
[    11.323] (==) intel(0): video overlay key set to 0x101fe
[    11.323] (II) intel(0): Output LVDS1 using monitor section Monitor0
[    11.325] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    11.344] (II) intel(0): Output VGA1 has no monitor section
[    11.345] (II) intel(0): Output DP1 has no monitor section
[    11.345] (II) intel(0): EDID for output LVDS1
[    11.345] (II) intel(0): Manufacturer: AUO  Model: 12ec  Serial#: 0
[    11.345] (II) intel(0): Year: 2008  Week: 1
[    11.345] (II) intel(0): EDID Version: 1.3
[    11.345] (II) intel(0): Digital Display Input
[    11.345] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    11.345] (II) intel(0): Gamma: 2.20
[    11.345] (II) intel(0): No DPMS capabilities specified
[    11.345] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    11.345] (II) intel(0): First detailed timing is preferred mode
[    11.345] (II) intel(0): redX: 0.640 redY: 0.342   greenX: 0.310 greenY: 0.580
[    11.345] (II) intel(0): blueX: 0.150 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    11.345] (II) intel(0): Manufacturer's mask: 0
[    11.345] (II) intel(0): Supported detailed timing:
[    11.345] (II) intel(0): clock: 72.0 MHz   Image Size:  344 x 193 mm
[    11.345] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1486 h_border: 0
[    11.345] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 806 v_border: 0
[    11.345] (II) intel(0): Supported detailed timing:
[    11.345] (II) intel(0): clock: 72.0 MHz   Image Size:  344 x 193 mm
[    11.345] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1486 h_border: 0
[    11.345] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 806 v_border: 0
[    11.345] (II) intel(0):  H597H€B156XW1
[    11.345] (II) intel(0): Unknown vendor-specific block 0
[    11.345] (II) intel(0): EDID (in hex):
[    11.345] (II) intel(0):     00ffffffffffff0006afec1200000000
[    11.345] (II) intel(0):     01120103902213780ae6b5a3574f9426
[    11.345] (II) intel(0):     1e505400000001010101010101010101
[    11.345] (II) intel(0):     010101010101201c5678500026303020
[    11.345] (II) intel(0):     340058c11000001a201c567850002630
[    11.345] (II) intel(0):     3020340058c11000001a000000fe0048
[    11.345] (II) intel(0):     35393748804231353658573100000000
[    11.345] (II) intel(0):     00000000000000000001010a202000da
[    11.345] (II) intel(0): EDID vendor "AUO", prod id 4844
[    11.345] (II) intel(0): Printing DDC gathered Modelines:
[    11.345] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    11.346] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    11.346] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    11.346] (II) intel(0): Printing probed modes for output LVDS1
[    11.346] (II) intel(0): Modeline "1366x768"x60.1   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    11.346] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    11.346] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    11.346] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    11.346] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    11.346] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    11.346] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    11.368] (II) intel(0): EDID for output VGA1
[    11.369] (II) intel(0): EDID for output DP1
[    11.369] (II) intel(0): Output LVDS1 connected
[    11.369] (II) intel(0): Output VGA1 disconnected
[    11.369] (II) intel(0): Output DP1 disconnected
[    11.369] (II) intel(0): Using exact sizes for initial modes
[    11.369] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    11.369] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    11.369] (II) intel(0): Kernel page flipping support detected, enabling
[    11.369] (**) intel(0): Display dimensions: (340, 190) mm
[    11.369] (**) intel(0): DPI set to (102, 102)
[    11.369] (II) Loading sub module "fb"
[    11.369] (II) LoadModule: "fb"
[    11.369] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.370] (II) Module fb: vendor="X.Org Foundation"
[    11.370]     compiled for 1.10.1, module version = 1.0.0
[    11.370]     ABI class: X.Org ANSI C Emulation, version 0.4
[    11.370] (==) Depth 24 pixmap format is 32 bpp
[    11.370] (==) intel(0): VideoRam: 262144 KB
[    11.370] (II) intel(0): [DRI2] Setup complete
[    11.370] (II) intel(0): [DRI2]   DRI driver: i965
[    11.370] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    11.383] (II) UXA(0): Driver registered support for the following operations:
[    11.383] (II)         solid
[    11.383] (II)         copy
[    11.383] (II)         composite (RENDER acceleration)
[    11.383] (II)         put_image
[    11.383] (II)         get_image
[    11.384] (==) intel(0): Backing store disabled
[    11.384] (==) intel(0): Silken mouse enabled
[    11.384] (II) intel(0): Initializing HW Cursor
[    11.416] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    11.423] (==) intel(0): DPMS enabled
[    11.423] (==) intel(0): Intel XvMC decoder enabled
[    11.423] (II) intel(0): Set up textured video
[    11.423] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    11.423] (II) intel(0): direct rendering: DRI2 Enabled
[    11.423] (==) intel(0): hotplug detection: "enabled"
[    11.423] (--) RandR disabled
[    11.423] (II) Initializing built-in extension Generic Event Extension
[    11.423] (II) Initializing built-in extension SHAPE
[    11.423] (II) Initializing built-in extension MIT-SHM
[    11.423] (II) Initializing built-in extension XInputExtension
[    11.423] (II) Initializing built-in extension XTEST
[    11.423] (II) Initializing built-in extension BIG-REQUESTS
[    11.423] (II) Initializing built-in extension SYNC
[    11.423] (II) Initializing built-in extension XKEYBOARD
[    11.423] (II) Initializing built-in extension XC-MISC
[    11.423] (II) Initializing built-in extension SECURITY
[    11.423] (II) Initializing built-in extension XINERAMA
[    11.423] (II) Initializing built-in extension XFIXES
[    11.423] (II) Initializing built-in extension RENDER
[    11.423] (II) Initializing built-in extension RANDR
[    11.423] (II) Initializing built-in extension COMPOSITE
[    11.423] (II) Initializing built-in extension DAMAGE
[    11.423] (II) Initializing built-in extension GESTURE
[    11.435] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[    11.567] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    11.567] (II) AIGLX: enabled GLX_INTEL_swap_event
[    11.567] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    11.567] (II) AIGLX: enabled GLX_SGI_make_current_read
[    11.567] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    11.568] (II) AIGLX: Loaded and initialized i965
[    11.568] (II) GLX: Initialized DRI2 GL provider for screen 0
[    11.568] (II) intel(0): Setting screen physical size to 361 x 203
[    11.585] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    11.599] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    11.599] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    11.599] (II) LoadModule: "evdev"
[    11.600] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.600] (II) Module evdev: vendor="X.Org Foundation"
[    11.600]     compiled for 1.10.0.902, module version = 2.6.0
[    11.600]     Module class: X.Org XInput Driver
[    11.600]     ABI class: X.Org XInput driver, version 12.3
[    11.600] (II) Using input driver 'evdev' for 'Video Bus'
[    11.600] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.600] (**) Video Bus: always reports core events
[    11.600] (**) Video Bus: Device: "/dev/input/event11"
[    11.600] (--) Video Bus: Found keys
[    11.600] (II) Video Bus: Configuring as keyboard
[    11.601] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input12/event11"
[    11.601] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    11.601] (**) Option "xkb_rules" "evdev"
[    11.601] (**) Option "xkb_model" "abnt2"
[    11.601] (**) Option "xkb_layout" "br"
[    11.603] (II) XKB: reuse xkmfile /var/lib/xkb/server-20278E27F1DC9FDDFD591DABFB86C7D7989CFCCF.xkm
[    11.618] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    11.618] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.618] (II) Using input driver 'evdev' for 'Power Button'
[    11.618] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.618] (**) Power Button: always reports core events
[    11.618] (**) Power Button: Device: "/dev/input/event1"
[    11.618] (--) Power Button: Found keys
[    11.618] (II) Power Button: Configuring as keyboard
[    11.618] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    11.618] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    11.618] (**) Option "xkb_rules" "evdev"
[    11.618] (**) Option "xkb_model" "abnt2"
[    11.618] (**) Option "xkb_layout" "br"
[    11.619] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    11.619] (II) No input driver/identifier specified (ignoring)
[    11.619] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    11.619] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    11.619] (II) Using input driver 'evdev' for 'Sleep Button'
[    11.619] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.619] (**) Sleep Button: always reports core events
[    11.619] (**) Sleep Button: Device: "/dev/input/event2"
[    11.620] (--) Sleep Button: Found keys
[    11.620] (II) Sleep Button: Configuring as keyboard
[    11.620] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    11.620] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    11.620] (**) Option "xkb_rules" "evdev"
[    11.620] (**) Option "xkb_model" "abnt2"
[    11.620] (**) Option "xkb_layout" "br"
[    11.622] (II) config/udev: Adding input device HID 413c:8161 (/dev/input/event4)
[    11.622] (**) HID 413c:8161: Applying InputClass "evdev keyboard catchall"
[    11.622] (II) Using input driver 'evdev' for 'HID 413c:8161'
[    11.622] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.622] (**) HID 413c:8161: always reports core events
[    11.622] (**) HID 413c:8161: Device: "/dev/input/event4"
[    11.623] (--) HID 413c:8161: Found keys
[    11.623] (II) HID 413c:8161: Configuring as keyboard
[    11.623] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input4/event4"
[    11.623] (II) XINPUT: Adding extended input device "HID 413c:8161" (type: KEYBOARD)
[    11.623] (**) Option "xkb_rules" "evdev"
[    11.623] (**) Option "xkb_model" "abnt2"
[    11.623] (**) Option "xkb_layout" "br"
[    11.626] (II) config/udev: Adding input device Integrated_Webcam_1.3M (/dev/input/event8)
[    11.626] (**) Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
[    11.626] (II) Using input driver 'evdev' for 'Integrated_Webcam_1.3M'
[    11.626] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.626] (**) Integrated_Webcam_1.3M: always reports core events
[    11.626] (**) Integrated_Webcam_1.3M: Device: "/dev/input/event8"
[    11.626] (--) Integrated_Webcam_1.3M: Found keys
[    11.626] (II) Integrated_Webcam_1.3M: Configuring as keyboard
[    11.626] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input8/event8"
[    11.626] (II) XINPUT: Adding extended input device "Integrated_Webcam_1.3M" (type: KEYBOARD)
[    11.626] (**) Option "xkb_rules" "evdev"
[    11.626] (**) Option "xkb_model" "abnt2"
[    11.626] (**) Option "xkb_layout" "br"
[    11.627] (II) config/udev: Adding input device HDA Intel Mic at Ext Right Jack (/dev/input/event12)
[    11.627] (II) No input driver/identifier specified (ignoring)
[    11.628] (II) config/udev: Adding input device HDA Intel HP Out at Ext Right Jack (/dev/input/event13)
[    11.628] (II) No input driver/identifier specified (ignoring)
[    11.631] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event5)
[    11.631] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[    11.631] (II) Using input driver 'evdev' for 'Microsft Microsoft Wireless Desktop Receiver 3.1'
[    11.631] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.631] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[    11.631] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event5"
[    11.631] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[    11.631] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[    11.631] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.2/2-3.2:1.0/input/input5/event5"
[    11.631] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
[    11.631] (**) Option "xkb_rules" "evdev"
[    11.631] (**) Option "xkb_model" "abnt2"
[    11.631] (**) Option "xkb_layout" "br"
[    11.632] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event6)
[    11.632] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev pointer catchall"
[    11.632] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[    11.632] (II) Using input driver 'evdev' for 'Microsft Microsoft Wireless Desktop Receiver 3.1'
[    11.632] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.632] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[    11.632] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event6"
[    11.632] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found 9 mouse buttons
[    11.632] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found scroll wheel(s)
[    11.632] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found relative axes
[    11.632] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found x and y relative axes
[    11.632] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found absolute axes
[    11.633] (II) evdev-grail: failed to open grail, no gesture support
[    11.633] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[    11.633] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as mouse
[    11.633] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[    11.633] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Adding scrollwheel support
[    11.633] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: YAxisMapping: buttons 4 and 5
[    11.633] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    11.633] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.2/2-3.2:1.1/input/input6/event6"
[    11.633] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
[    11.633] (**) Option "xkb_rules" "evdev"
[    11.633] (**) Option "xkb_model" "abnt2"
[    11.633] (**) Option "xkb_layout" "br"
[    11.633] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: initialized for relative axes.
[    11.633] (WW) Microsft Microsoft Wireless Desktop Receiver 3.1: ignoring absolute axes.
[    11.633] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) keeping acceleration scheme 1
[    11.633] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration profile 0
[    11.633] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration factor: 2.000
[    11.633] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration threshold: 4
[    11.634] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/mouse0)
[    11.634] (II) No input driver/identifier specified (ignoring)
[    11.638] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    11.638] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    11.638] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    11.638] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.638] (**) AT Translated Set 2 keyboard: always reports core events
[    11.638] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    11.638] (--) AT Translated Set 2 keyboard: Found keys
[    11.638] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    11.638] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    11.638] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    11.638] (**) Option "xkb_rules" "evdev"
[    11.638] (**) Option "xkb_model" "abnt2"
[    11.638] (**) Option "xkb_layout" "br"
[    11.639] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event9)
[    11.639] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    11.639] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    11.639] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.639] (**) PS/2 Mouse: always reports core events
[    11.639] (**) PS/2 Mouse: Device: "/dev/input/event9"
[    11.639] (--) PS/2 Mouse: Found 3 mouse buttons
[    11.639] (--) PS/2 Mouse: Found relative axes
[    11.639] (--) PS/2 Mouse: Found x and y relative axes
[    11.639] (II) PS/2 Mouse: Configuring as mouse
[    11.639] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    11.639] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    11.639] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event9"
[    11.639] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    11.639] (II) PS/2 Mouse: initialized for relative axes.
[    11.640] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    11.640] (**) PS/2 Mouse: (accel) acceleration profile 0
[    11.640] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    11.640] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    11.640] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[    11.640] (II) No input driver/identifier specified (ignoring)
[    11.640] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event10)
[    11.640] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    11.640] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    11.640] (II) LoadModule: "synaptics"
[    11.641] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    11.641] (II) Module synaptics: vendor="X.Org Foundation"
[    11.641]     compiled for 1.10.0.902, module version = 1.3.99
[    11.641]     Module class: X.Org XInput Driver
[    11.641]     ABI class: X.Org XInput driver, version 12.3
[    11.641] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    11.641] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    11.641] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    11.641] (**) Option "Device" "/dev/input/event10"
[    11.652] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    11.652] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    11.652] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    11.652] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    11.652] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    11.660] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    11.660] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    11.664] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input11/event10"
[    11.664] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    11.664] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    11.664] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    11.664] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    11.664] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    11.664] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    11.664] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    11.664] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    11.672] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    11.672] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    11.672] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    11.672] (II) No input driver/identifier specified (ignoring)
[    11.679] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[    11.679] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    11.679] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    11.679] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.679] (**) Dell WMI hotkeys: always reports core events
[    11.679] (**) Dell WMI hotkeys: Device: "/dev/input/event7"
[    11.679] (--) Dell WMI hotkeys: Found keys
[    11.679] (II) Dell WMI hotkeys: Configuring as keyboard
[    11.679] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event7"
[    11.679] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    11.679] (**) Option "xkb_rules" "evdev"
[    11.679] (**) Option "xkb_model" "abnt2"
[    11.679] (**) Option "xkb_layout" "br"
[    12.399] (II) intel(0): EDID vendor "AUO", prod id 4844
[    12.399] (II) intel(0): Printing DDC gathered Modelines:
[    12.399] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    12.422] (II) intel(0): EDID vendor "AUO", prod id 4844
[    12.422] (II) intel(0): Printing DDC gathered Modelines:
[    12.422] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    12.446] (II) intel(0): EDID vendor "AUO", prod id 4844
[    12.446] (II) intel(0): Printing DDC gathered Modelines:
[    12.446] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    12.470] (II) intel(0): EDID vendor "AUO", prod id 4844
[    12.470] (II) intel(0): Printing DDC gathered Modelines:
[    12.470] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    78.961] (II) intel(0): EDID vendor "AUO", prod id 4844
[    78.961] (II) intel(0): Printing DDC gathered Modelines:
[    78.961] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    78.985] (II) intel(0): EDID vendor "AUO", prod id 4844
[    78.985] (II) intel(0): Printing DDC gathered Modelines:
[    78.985] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    80.909] (II) intel(0): EDID vendor "AUO", prod id 4844
[    80.909] (II) intel(0): Printing DDC gathered Modelines:
[    80.909] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    82.979] (II) intel(0): EDID vendor "AUO", prod id 4844
[    82.979] (II) intel(0): Printing DDC gathered Modelines:
[    82.979] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    83.008] (II) intel(0): EDID vendor "AUO", prod id 4844
[    83.008] (II) intel(0): Printing DDC gathered Modelines:
[    83.008] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    83.026] (II) intel(0): EDID vendor "AUO", prod id 4844
[    83.026] (II) intel(0): Printing DDC gathered Modelines:
[    83.026] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)
[    83.050] (II) intel(0): EDID vendor "AUO", prod id 4844
[    83.050] (II) intel(0): Printing DDC gathered Modelines:
[    83.050] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 +hsync -vsync (48.5 kHz)

```

/etc/X11/xorg.conf
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
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
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "extmod"
    Load  "dbe"
    Load  "glx"
    Load  "dri"
    Load  "dri2"
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

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card2"
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

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
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

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
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

```

---

