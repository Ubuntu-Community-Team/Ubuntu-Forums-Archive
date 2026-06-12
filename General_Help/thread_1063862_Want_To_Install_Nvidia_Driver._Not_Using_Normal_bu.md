---
title: "Want To Install Nvidia Driver. Not Using Normal *buntu"
date: 2009-02-08
forum: General Help
---

### Post by Mark76 on 2009-02-08
So I don't have the handy GUI thing that you get when you first install Ubuntu.

Can someone tell me what it is so I install it from the repository?

---

### Post by taurus on 2009-02-08
You mean you installed the server version (prompt) and now want to install a window manager or desktop environment like Gnome?

---

### Post by Mark76 on 2009-02-08
No. I just want to install the driver for my Nvidia Geforce 6150 graphics card.

I thought I had, but I don't see the Nvidia splash screen just before the login window.

---

### Post by taurus on 2009-02-08
Look in System -> Administration -> Hardware Drivers to see if your graphic card is enable.  And maybe the reason you don't see nVidia splash screen is because you have it off in /etc/X11/xorg.conf.

Applications -> Accessories -> Terminal
```
cat /etc/X11/xorg.conf
```

---

### Post by Mark76 on 2009-02-08
How does this look?

> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection

---

### Post by taurus on 2009-02-08
> 
Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
**[COLOR="Blue"]Option	"NoLogo"	"False"[/COLOR]**
EndSection 
You can edit your /etc/X11/xorg.conf and add the Option line to it and see if the nVidia logo displays before the GUI login screen comes up.

---

### Post by Mark76 on 2009-02-08
Okay. I did that, rebooted and no Nvidia logo.

So I obviously don't have it installed.

What's the next step?

---

### Post by taurus on 2009-02-08
> 
Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
Disable "dri2"
EndSection

Section "Device"
Identifier "Configured Video Device"
**[COLOR="Red"]Driver "nvidia"[/COLOR]**
EndSection 

You are using nvidia driver for your graphic card.

Look at the output of this command and see if nvidia is on the list.

```
lsmod
```

Maybe change the NoLogo to Logo and False back to True in /etc/X11/xorg.conf.  You don't have to reboot.  You just need to restart X server with <Ctrl><Alt>Backspace.

---

### Post by Mark76 on 2009-02-08
The nearest I can se is nv

> libusual               35752  1 usb_storage
pata_amd               22020  0 
sata_nv                35336  4 
ata_generic            14212  0 
pata_acpi              13568  0 
ehci_hcd               49548  0 
forcedeth              68112  0 
ohci_hcd               35100  0 
ohci1394               41524  0 
libata                201312  4 pata_amd,sata_**nv**,ata_generic,pata_acpi
scsi_mod              183160  6 sbp2,sr_mod,sd_mod,sg,usb_storage,libata
dock                   18464  1 libata
ieee1394              110592  2 sbp2,ohci1394
usbcore               175888  6 isp1760,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                27424  0 
processor              47800  1 thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  1 


---

### Post by taurus on 2009-02-08
> 
libata 201312 4 pata_amd,**sata_nv**,ata_generic,pata_acpi

That is a driver for your SATA.  Has nothing to do with the graphic card driver.

The output should be much more than that.

---

### Post by Mark76 on 2009-02-08
> Module                  Size  Used by
aes_x86_64             16384  1 
aes_generic            36392  1 aes_x86_64
ecb                    11520  1 
crypto_blkcipher       27780  1 ecb
ecryptfs              107376  1 
ppdev                  16904  0 
wmi                    15808  0 
battery                21128  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
container              12288  0 
pci_slot               13704  0 
video                  29204  0 
output                 11776  1 video
ipv6                  314312  14 
af_packet              29568  2 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
sbp2                   32652  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
loop                   26380  0 
psmouse                51612  0 
pcspkr                 11136  0 
evdev                  20512  6 
k8temp                 13568  0 
serio_raw              14596  0 
nvidia               7815240  26 
snd_hda_intel         492336  1 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 42140  0 
pci_hotplug            39216  1 shpchp
i2c_nforce2            15752  0 
snd                    79432  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
button                 15904  0 
isp1760                29200  0 
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
i2c_core               36128  2 nvidia,i2c_nforce2
ext3                  150544  1 
jbd                    66856  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
sg                     45408  2 
usb_storage            94784  0 
libusual               35752  1 usb_storage
pata_amd               22020  0 
sata_nv                35336  4 
ata_generic            14212  0 
pata_acpi              13568  0 
ehci_hcd               49548  0 
forcedeth              68112  0 
ohci_hcd               35100  0 
ohci1394               41524  0 
libata                201312  4 pata_amd,sata_nv,ata_generic,pata_acpi
scsi_mod              183160  6 sbp2,sr_mod,sd_mod,sg,usb_storage,libata
dock                   18464  1 libata
ieee1394              110592  2 sbp2,ohci1394
usbcore               175888  6 isp1760,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                27424  0 
processor              47800  1 thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  1 


Does that look right?

---

### Post by taurus on 2009-02-08
> 
i2c_core 36128 2 **[COLOR="Blue"]nvidia[/COLOR]**,i2c_nforce2

There you go.  Are you able to run compiz or any app that requires 3D because nv driver only provides you with 2D capability?

---

### Post by Mark76 on 2009-02-08
Is there a test that doesn't involve compiz?

---

### Post by taurus on 2009-02-08
```
glxinfo
```
You should see something like these at the top.

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video, 
    GLX_NV_multisample_coverage
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: unknown board/AGP/SSE2
OpenGL version string: 2.1.2 NVIDIA 177.82
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler

```

---

### Post by Mark76 on 2009-02-08
Yep. Got it.

So it's not the video card driver that's responsible for the less than stellar rendering of xcompmgr :lol:

Thanks anyway

---

