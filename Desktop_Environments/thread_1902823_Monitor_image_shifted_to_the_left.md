---
title: "Monitor image shifted to the left"
date: 2011-12-31
forum: Desktop Environments
---

### Post by arepisky on 2011-12-31
Hello,

I'm running Kubuntu 11.04, 64-bit on my Toshiba Satellite A300 connected to external monitor. I'd like to use both laptop monitor and the external monitor. I couldn't set it properly in System Settings, so I put the following commands in /etc/kde4/kdm/Xsetup:

```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 "1280x1024_60.00"
xrandr --output LVDS1 --auto
xrandr --output VGA1 --mode "1280x1024_60.00" --left-of LVDS1 
```

Now the resolution of both monitors is OK as well as frequency and configuration (external monitor is primary). The problem is the black vertical strip on the right of the external monitor (see photos). It prevents me from seeing leftmost part of the desktop. How do I get rid of it? I know it's not my monitor settings, cause I don't have that strip in Windows and the width of the strip changes randomly with each boot.

And don't tell me to install 11.10, it's buggy as hell.

---

### Post by dolphin194 on 2012-01-01
Try using a lower resolution on the external monitor (I would recommend 1024x768). The circuits in old CRT monitors can't handle higher resolutions. Even though you can select the higher resolution, it's still possible that your monitor does not support it.

---

### Post by z3nhakr on 2012-01-01
sounds like you need to configure /etc/X11/xorg.conf or it could be that your video card doesn't have the correct drivers. what is the model of your chipset?

---

### Post by arepisky on 2012-01-01
dolphin194: I changed the resolution to 1024x768 and the black strip disappeared. However I'm not comfortable with it, 1280x1024 is the native resolution of the monitor and I use 1280x1024 also in Windows.

z3nhakr:
I get the following description of video card from [FONT="Courier New"]lspci[/FONT]:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```
[FONT="Courier New"]lsmod[/FONT] output:
```
Module                  Size  Used by
rfcomm                 47694  12 
sco                    18187  2 
bnep                   18308  2 
binfmt_misc            17565  1 
l2cap                  53610  16 rfcomm,bnep
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  0 
joydev                 17606  0 
arc4                   12529  2 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
rtl8187                60982  0 
mac80211              294370  1 rtl8187
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178528  2 rtl8187,mac80211
btusb                  18600  2 
eeprom_93cx6           12725  1 rtl8187
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
r852                   18246  0 
v4l2_compat_ioctl32    17078  1 videodev
sm_common              16817  1 r852
nand                   55112  2 r852,sm_common
nand_ids               12723  1 nand
nand_ecc               13230  1 nand
mtd                    27900  2 sm_common,nand
psmouse                73535  0 
sparse_keymap          13898  0 
serio_raw              13166  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
toshiba_bluetooth      12807  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
mmc_block              18053  0 
i915                  515078  4 
drm_kms_helper         42394  1 i915
drm                   227534  5 i915,drm_kms_helper
firewire_ohci          40370  0 
ahci                   25951  6 
libahci                26642  1 ahci
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
r8169                  48022  0 
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
```

---

