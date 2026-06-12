---
title: "KDE Desktop Effects with OpenGL and 780G chipset"
date: 2011-03-31
forum: Desktop Environments
---

### Post by GraysonPeddie on 2011-03-31
Even with fglrx, I can't enable KDE Desktop Effects with OpenGL. At first before I went with fglrx, I went with whatever the default driver that the xorg uses when it detects my video card. Desktop effects worked in Compiz Fusion (GNOME) and Windows Vista (Aero with a graphics desktop experience of 3.2 or 3.6 out of 5.9).

lspci:

```
grayson@htpc:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
04:06.0 Multimedia audio controller: Creative Labs SB X-Fi
04:07.0 Multimedia controller: Motorola DSP56361 Digital Signal Processor (rev 01)
```

lsmod:

```
grayson@htpc:~$ lsmod
Module                  Size  Used by
snd_seq_dummy           1806  0 
binfmt_misc             7984  1 
radeon                910067  0 
ttm                    68212  1 radeon
drm_kms_helper         32836  1 radeon
drm                   206198  3 radeon,ttm,drm_kms_helper
i2c_algo_bit            6208  1 radeon
parport_pc             30086  0 
ppdev                   6804  0 
snd_echo3g             33233  0 
snd_ctxfi             101537  5 
snd_pcm                89104  4 snd_echo3g,snd_ctxfi
usblp                  12700  0 
snd_seq_midi            5932  0 
snd_rawmidi            22207  2 snd_echo3g,snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
ir_lirc_codec           3888  0 
lirc_dev               11209  1 ir_lirc_codec
fglrx                2523725  31 
snd_seq                57512  9 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
ir_sony_decoder         2381  0 
ir_jvc_decoder          2442  0 
joydev                 11395  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    64181  17 snd_echo3g,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc6_decoder          3018  0 
lp                     10201  0 
soundcore               1240  1 snd
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42030  0 
rc_imon_pad             1729  0 
ir_rc5_decoder          2474  0 
imon                   24845  0 
shpchp                 34910  0 
i2c_piix4              10047  0 
hid                    84710  1 usbhid
edac_core              46822  0 
ir_nec_decoder          2442  0 
ir_core                16906  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_imon_pad,ir_rc5_decoder,imon,ir_nec_decoder
psmouse                62080  0 
edac_mce_amd            9387  0 
k8temp                  4128  0 
serio_raw               4910  0 
snd_page_alloc          8588  3 snd_echo3g,snd_ctxfi,snd_pcm
ahci                   22210  4 
r8169                  42254  0 
pata_jmicron            2771  0 
mii                     5261  1 r8169
libahci                26148  1 ahci
pata_atiixp             4405  0
```

Before fglrx is installed:

```
# NOXORGCONFEXISTED: No X.org configuration file existed when this backup was created.
```

After fglrx (I had to execute aticonfig --initial with the x.org server turned off):

```
grayson@htpc:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
```

So my question is, is it possible that the KDE desktop effects are more GPU intensive than with GNOME for Compiz Fusion or Windows Vista/7? I'm a big fan of KDE and I want to use OpenGL-based desktop effects.

When I do a search in the Internet about KDE Desktop Effects being too slow or cannot enable desktop effects, I've came across a couple of threads with a mention of ATI Radeon X1300 or similar, which were not supported by AMD's new Catalyst drivers, but I don't know about open source drivers...

---

### Post by hazica on 2011-03-31
I'm experiencing somewhat similar issues, though I have progressed further along than you, since I get my desktop effects, but without direct rendering.

Would you mind posting the output of "glxinfo | grep direct"? If it says "yes", you're drivers are installed properly, and you can start looking at the kwinrc config file located in ~/.kde/share/config/kwinrc. (Feel free to post that one here as well)

---

### Post by GraysonPeddie on 2011-03-31
glxinfo | grep direct:

```
direct rendering: Yes
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access,
```

.kde/share/config/kwinrc

```
[$Version]
update_info=kwin_focus1.upd:kwin_focus1,kwin3_plugin.upd:kde3.2,kwin_focus2.upd:kwin_focus2,kwin.upd:kde3.0r1,kwin.upd:kde3.2Xinerama,kwin_blacklist.upd:Blacklist-4.5,kwin_on_off.upd:kwin_on_off

[Blacklist][Blur]
Advanced Micro Devices=DRI R600:-:7.8.1,DRI R600:-:7.8.2
Ati=Radeon HD 3650:-:3.3.9901
NVIDIA=GeForce 6150/PCI/SSE2:-:195

[Blacklist][Lanczos]
Advanced Micro Devices=DRI R600:-:7.8.1,DRI R600:-:7.8.2
Intel=GM45 Express Chipset GEM 20100328:-:7.8.2,GM45 Express Chipset GEM 20091221:-:7.7.1,965GM GEM 20100328 2010Q1:-:7.8.2,965GM GEM 20091221 2009Q4:-:7.7.1,Ironlake Mobile GEM 20100328:-:7.8.2

[Compositing]
AnimationSpeed=3
Backend=XRender
DisableChecks=false
Enabled=true
GLDirect=false
GLMode=TFP
GLTextureFilter=1
GLVSync=false
HiddenPreviews=5
OpenGLIsUnsafe=true
XRenderSmoothScale=false

[Desktops]
Name_1=
Name_2=

[Effect-BoxSwitch]
TabBox=false

[Effect-FlipSwitch]
TabBox=false

[Effect-PresentWindows]
TabBox=false

[Plugins]
kwin4_effect_blurEnabled=true
kwin4_effect_boxswitchEnabled=true
kwin4_effect_coverswitchEnabled=true
kwin4_effect_cubeEnabled=true
kwin4_effect_cubeslideEnabled=false
kwin4_effect_desktopgridEnabled=true
kwin4_effect_dialogparentEnabled=true
kwin4_effect_diminactiveEnabled=false
kwin4_effect_dimscreenEnabled=false
kwin4_effect_explosionEnabled=false
kwin4_effect_fadeEnabled=true
kwin4_effect_fadedesktopEnabled=false
kwin4_effect_fallapartEnabled=false
kwin4_effect_flipswitchEnabled=false
kwin4_effect_glideEnabled=false
kwin4_effect_highlightwindowEnabled=true
kwin4_effect_invertEnabled=false
kwin4_effect_loginEnabled=true
kwin4_effect_logoutEnabled=true
kwin4_effect_lookingglassEnabled=false
kwin4_effect_magiclampEnabled=false
kwin4_effect_magnifierEnabled=false
kwin4_effect_minimizeanimationEnabled=true
kwin4_effect_mousemarkEnabled=false
kwin4_effect_presentwindowsEnabled=true
kwin4_effect_resizeEnabled=false
kwin4_effect_scaleinEnabled=false
kwin4_effect_shadowEnabled=true
kwin4_effect_sharpenEnabled=false
kwin4_effect_sheetEnabled=false
kwin4_effect_showfpsEnabled=false
kwin4_effect_showpaintEnabled=false
kwin4_effect_slideEnabled=true
kwin4_effect_slidebackEnabled=false
kwin4_effect_slidingpopupsEnabled=true
kwin4_effect_snaphelperEnabled=false
kwin4_effect_snowEnabled=false
kwin4_effect_taskbarthumbnailEnabled=true
kwin4_effect_thumbnailasideEnabled=false
kwin4_effect_trackmouseEnabled=false
kwin4_effect_translucencyEnabled=true
kwin4_effect_wobblywindowsEnabled=false
kwin4_effect_zoomEnabled=true

[Style]
BorderSize=2
ButtonsOnLeft=MS
ButtonsOnRight=HIAX
CustomButtonPositions=false
PluginLib=kwin3_aurorae
ShowToolTips=true

[TabBox]
ListMode=0
ShowTabBox=true

[Windows]
IgnoreFocusStealingClasses=kio_uiserver
```

Is it really possible to get the most out of OpenGL desktop effects while still maintaining performance? I really don't like going back to GNOME with Compiz, because I love search and launch (it's nice to break away from the "Start(TM)" menu of Windows and the Kickoff menu of KDE and think about new ways of how I access my desktop computer :) ) and I really love the fact that I can see the applications behind the transparent panel (pardon me for bragging, though).

Oh, and I tried out the Newspaper activity when I was in 4.6.1 by using kubuntu-ppa/backports but then when I get it the way I want by filling up all the widgets in the screen (desktop, task manager, multimedia widget, digital clock, a timer, calendar, an RSS reader, and maybe a couple of them which all came up to be about 12 widgets or so wrapped in three columns that fit very nicely on my screen without scrolling, and when I click in the icon in the desktop widget (Radio365-Desktop from Live365, for example), all of my widgets just went out of whack and crazy with the horizontal scrollbar displayed. Then after a reboot, the vertical scrollbar displayed and it's like I can't control the widget's size! The performance of my desktop in OpenGL mode went like unresponsive and when I try to switch to another activity, the plasma-desktop just went into cycle of inifinate loop: segmentation fault. I once reported a [bug](https://bugs.kde.org/show_bug.cgi?id=269751) about what happened. My first bug, though not related to my second [bug](https://bugs.kde.org/show_bug.cgi?id=269428), was filed when I was in Gentoo with 4.6.1 (the portage repository came with 4.5.5, but then I wouldn't discuss it further since the part about my experience (some positive, some negative, when it comes to portage not having all the latest versions of the packages -- not even the latest snapshots, which is strange for me) is beyond the scope of my thread and I've already made this paragraph too long for making it too hard to read.

Well, I just went back to 4.5.1 by reinstalling Kubuntu with no backports (except for MythTV, which I need 0.24 in order for it to work with my backend server, even though my backend server runs Ubuntu Server 10.04 LTS, but then that and my previous paragraph is another story (even though my previous paragraph is related to performance problems with OpenGL), and I also cleaned out .kde before I log in to my clean desktop.

I do apologize if I'm going off-topic here, but sometimes, it helps to talk about my previous experiences, especially about my problems with getting the OpenGL desktop effects to work. Oh yes, speaking of Gentoo, I have had some good experiences compiling packages, but they're just a mixed bag for me and it does help to keep in mind that I can never have too much patience for just one day getting my Gentoo system up and running, even though I'm trying to get the most out of performance for music creation by optimizing for one specific CPU while still keeping the desktop effects on (I thought it'd be nice to let the GPU handle all the desktop effects while I'm creating music just for fun).

Do you really think that a desktop effects engine using OpenGL can *really* take away CPU processing time? I would think I don't need to disable Aero in Windows Vista or 7 if I were doing music creation under Windows.

Anyway, I'm going to need to get back in topic. :)

---

### Post by RobbieThe1st on 2011-03-31
Just install compiz? It works fine with KDE, you know.

---

### Post by GraysonPeddie on 2011-03-31
> **RobbieThe1st said:**
> Just install compiz? It works fine with KDE, you know.

I think I'll prefer KWin instead of Compiz, but thanks for your suggestion.

> I used to use compiz quite a bit with kde 3.5, not I don't see any need to even install it when using kde 4. As I see it compiz will provide the innovative edge for those interested in all of what's possible in terms of desktop effects and compositing, while Kwin takes a step back and carefully implements those features that make for the best general user experience.

[http://forum.kde.org/viewtopic.php?f=15&t=85444](http://forum.kde.org/viewtopic.php?f=15&t=85444)

EDIT: However, I might try out [Compiz](http://ubuntuforums.org/showthread.php?t=1529029) with KWin Desktop Effects disabled

---

### Post by hazica on 2011-03-31
Hi, just got back. F**kin traffic. Try setting the parameter OpenGLIsUnsafe=true to false in kwinrc. Restart KDE, check out if it works. 

Sorry for the delay.

---

### Post by GraysonPeddie on 2011-03-31
Unsafe? Why is that keyword there?

Well, I'll give it a try then. Thanks.

EDIT: LOL, I guess setting the texture mode to shared memory makes my Radeon HD unsafe for OpenGL. Oh killjoy I'm going to be laughing at the variable OpenGLIsUnsafe now... Can someone please shed some light in this on why I cannot use shared memory even though my HD 3200 uses either 256MB or 512MB of shared system RAM? How does "texture from pixmap" work? If I select "fallback" in OpenGL mode, what does it do?

Edit 2: When I upgrade to Kubuntu 11.04, I have started to get almost smooth performance using OpenGL. Setting the OpenGL Mode to Shared Memory caused artifacts on the screen, so I set it back to texture from pixmap.

I must have configured something in the BIOS to improve performance of my desktop and I think it's something to do with gauged/ungauged mode or something (Auto/Always). The motherboard that I currently use is ECS A780GM-A Ultra. It oculd be related to DCT, but I'm not sure.

---

