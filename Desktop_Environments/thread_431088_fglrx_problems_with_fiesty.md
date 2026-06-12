---
title: "fglrx problems with fiesty"
date: 2007-05-02
forum: Desktop Environments
---

### Post by darrenc on 2007-05-02
After upgrading to Fiesty today, my system boots up to nothing but blank screens when trying to use fglrx and the current kernel (2.6.20-15).

A few different things are happening after the upgrade.  Here's the basic rundown.

If I try to boot into kernel 2.6.20-15, everything seems normal right up until time to draw the desktop.  The monitors (dual head) power up but are just black.  I can ssh in from another system and everything seems at least superficially normal - the system is up, takes commands, etc., but has no display on any terminal.  Running fglrxinfo from another system via ssh just holds and never gives any info, which is understandable considering the last line of the xorg log.

Dmesg reports the following:
[PHP][   62.563373] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   62.567438] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[   62.568020] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   62.861870] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   62.892906] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   62.892913] apm: disabled - APM is not SMP safe.
[   63.564557] Netfilter messages via NETLINK v0.30.
[   63.591128] nf_conntrack version 0.5.0 (8191 buckets, 65528 max)
[   63.990500] ip_tables: (C) 2000-2006 Netfilter Core Team
[   67.389778] NET: Registered protocol family 10
[   67.390007] lo: Disabled Privacy Extensions
[   67.442383] BUG: unable to handle kernel paging request at virtual address 54f000e8
[   67.442392]  printing eip:
[   67.442394] 54f000e8
[   67.442395] *pde = 00000000
[   67.442399] Oops: 0000 [#1]
[   67.442401] SMP 
[   67.442405] Modules linked in: ipv6 xt_tcpudp nf_conntrack_ipv4 iptable_filter ip_tables ip_queue xt_state nf_conntrack nfnetlink x_tables fglrx(P) ppdev speedstep_lib cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative tc1100_wmi pcc_acpi dev_acpi sony_acpi video sbs i2c_ec dock button battery container ac asus_acpi backlight af_packet fuse lp snd_cmipci gameport snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_opl3_lib snd_hwdep snd_mpu401_uart snd_seq_dummy snd_seq_oss i2c_viapro snd_seq_midi snd_rawmidi i2c_core snd_seq_midi_event via_ircc xpad irda snd_seq snd_timer snd_seq_device pcmcia crc_ccitt pcspkr parport_pc parport via_agp agpgart psmouse serio_raw yenta_socket rsrc_nonstatic snd shpchp pci_hotplug pcmcia_core soundcore evdev tsdev ext3 jbd mbcache ide_cd ide_disk cdrom ata_generic libata scsi_mod usbhid hid via82cxxx 8139too floppy ehci_hcd generic 8139cp mii uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[   67.442508] CPU:    1
[   67.442509] EIP:    0060:[<54f000e8>]    Tainted: P      VLI
[   67.442509] EFLAGS: 00213246   (2.6.20-15-generic #2)
[   67.442516] EIP is at 0x54f000e8
[   67.442518] eax: 00000000   ebx: f78adde4   ecx: 00000004   edx: 00000001
[   67.442520] esi: f6087000   edi: 00000000   ebp: f78addac   esp: f78add80
[   67.442523] ds: 007b   es: 007b   ss: 0068
[   67.442525] Process Xorg (pid: 5334, ti=f78ac000 task=c1beaa90 task.ti=f78ac000)
[   67.442527] Stack: f8c8cbd6 00000000 00000004 00000000 00000100 f8bc4000 00000001 c03a8280 
[   67.442535]        c1beaa90 00000000 f8cc84a0 f78addcc f8c8a189 f6087000 f78adde4 00000018 
[   67.442544]        f8c4b700 c03a8f94 f78adde4 f67fb680 f8c65b80 f6087000 f78adde4 00000030 
[   67.442552] Call Trace:
[   67.442555]  [<f8c8cbd6>] _ZN7ATI_GPS10GPSContext9MapToGartEPK16_GPS_MAP_TO_GART+0x66/0xa0 [fglrx]
[   67.442615]  [<f8c8a189>] Gps_MapToGart+0x39/0x50 [fglrx]
[   67.442646]  [<f8c4b700>] drm_alloc+0xa0/0x140 [fglrx]
[   67.442673]  [<f8c65b80>] firegl_gps_maptogart+0x70/0x90 [fglrx]
[   67.442739]  [<f8c5e6ea>] firegl_bind_pcie+0x1aa/0x3d0 [fglrx]
[   67.442795]  [<f8c598e8>] create_buffer_queue+0x1b8/0x8a0 [fglrx]
[   67.442832]  [<f8c5e446>] firegl_umm_init+0x336/0x430 [fglrx]
[   67.442870]  [<f8c58be1>] firegl_alloc_bufs+0x121/0x5d0 [fglrx]
[   67.442934]  [<f8c580a6>] firegl_get_lockid+0x56/0x80 [fglrx]
[   67.442962]  [<f8c58ac0>] firegl_alloc_bufs+0x0/0x5d0 [fglrx]
[   67.442990]  [<f8c5508e>] firegl_ioctl+0x1ae/0x230 [fglrx]
[   67.443016]  [<c0146440>] get_symbol_offset+0x10/0x40
[   67.443048]  [<c0146440>] get_symbol_offset+0x10/0x40
[   67.443052]  [<f8c494bc>] ip_firegl_ioctl+0x1c/0x30 [fglrx]
[   67.443076]  [<c0146440>] get_symbol_offset+0x10/0x40
[   67.443084]  [<c01826e8>] do_ioctl+0x78/0x90
[   67.443100]  [<c018275c>] vfs_ioctl+0x5c/0x2a0
[   67.443103]  [<c0176280>] do_sync_write+0x0/0x120
[   67.443119]  [<c0182a12>] sys_ioctl+0x72/0x90
[   67.443133]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[   67.443140]  [<c0146440>] get_symbol_offset+0x10/0x40
[   67.443179]  =======================
[   67.443180] Code:  Bad EIP value.
[   67.443183] EIP: [<54f000e8>] 0x54f000e8 SS:ESP 0068:f78add80[/PHP]

And the end of my xorg log reads:
[PHP](II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7362000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-15-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): FIREGL Board Found[/PHP]

And it just ends with that line "FIREGL Board Found" and I'm left with just a black screen.

If I use the failsafe xorg.conf, it will boot, but of course I don't have dual monitors that way.

Now, moving back to older kernels.  If I try to boot using 2.6.17-11, it just doesn't boot at all.  Using recovery mode to see the output, it halts after loading the kernel with the line "waiting for root file system".  Nothing more - that's it for that kernel.

Going back to kernel 2.6.17-10, I can boot with my normal xorg.conf file and get my dual display, but it keeps throwing me back to MESA and won't load the fglrx driver.

As it is now, I'm having to use the last option as dual display is more important to me, but I'd very much like to get it back to normal if possible.

Thanks for any advice any can offer.

---

### Post by ppe on 2007-05-03
Welcome to the club <sigh>. I have been tearing my hair out now for two days trying to get my X1900XT working with the ATI proprietary fglrx drivers on Feisty. Have googled like mad and read forum post after forum post. It seems really weird that there seems to be no common denominator to the problems, some people have no problem whatsoever and then some people with basically exactly the same setup get the black screen of death.

I have tried both methods from

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

tried Envy, also checked all the soft link stuff from [Softlink hell]("http://www.thinkwiki.org/wiki/Problems_with_fglrx#Softlink_hell")

Played around with screen resolutions, refresh rates, etc. No go. Vesa and the open source drivers work, but fglrx 8.36.5 (and 8.35 and 8.34) just hangs every time no matter what I do. Same symptoms every time: none of the X hotkeys ctrl-alt-Fn, ctrl-alt-bkspc, ctrl-alt-+, ctrl-alt-- work and I need to reset the machine.

Yeah, yeah, I know the answer:
1) get a graphics card from another vendor
2) complain loudly to ATI

One thing is interesting though, I don't get any of the nice debug output in my logs that you do. Are there some debug options somewhere that I can set to get fglrx driver to be more verbose about any problems it encounters?

---

### Post by darrenc on 2007-05-03
> **ppe said:**
> One thing is interesting though, I don't get any of the nice debug output in my logs that you do. Are there some debug options somewhere that I can set to get fglrx driver to be more verbose about any problems it encounters?

All the info I have there comes from 2 standard outputs - you should have them too.  If you look in the folder /var/log you'll find files called dmesg and dmesg.0.  These are the current and prior logs created at boot.  You can also see the current one by typing dmesg in a terminal or just the last 10 lines of the current one by typing dmesg | tail

The xorg logs are found in the same directory - /var/log, and are named Xorg.0.log and Xorg.0.log.old, also for the last 2 boots.

The Xorg log, in particular, can sometimes be very useful in tracking down problems.  If you check the top of the log, you'll see the key for the different line prefixes - (WW), (EE), etc.

Of course, it's not helping me at all with my current problem. :(

---

### Post by Owlman on 2007-05-12
I've had a similar problem. Happily running 6.10, and saw the recommendation to upgrade to 7.04 that appeared at the top of the Update Manager that pops up every few days. So I hit the button, wandered off for a cup of tea, and came back when the upgrade was complete. Same problem, booted up, and nothing but black screens. Rebooted and selected the previous kernel from the list in Grub. No problem, everything worked as per normal, including both monitors. My first thought was that the xorg.conf must have been modified, but then I figured that the same one must have been used by both kernels, so why would it work for one kernel but not the other? I'm not a guru so that's as far as I got.  And anyway I have a working system and no desperate requirement to upgrade.

Then I noticed that some things seemed to be different. K3B looks different, the buttons are much nicer and it now has a nice colourful background, not the drab grey one it had before, so it seems it's been upgraded, and presumably lots of other stuff too. Exactly what I have no idea. So now I don't know what I'm running. Edgy Fawn? Feisty Eft?

Not sure if this helps, if it does, great. If I can give you any other information you think might help I'm happy to provide it. I'm not a guru, but not a total noob either. I tend to use Ubuntu to do things I need to do rather than get down and dirty in the bowels of the OS, but I have a CLI and I'm not afraid to use it.

Brief system details: amd64 Athlon x2 3600+, Gigabyte mobo, radeon x1600 pro graphics card, 512Mb memory, anything else you need to know?

Cheers,
Ian

---

### Post by helliewm on 2007-05-13
I had the same problem typing all these instructions in this thread even though Feisty was installed by upgrading to Edgy.

[http://ubuntuforums.org/showthread.php?t=399913](http://ubuntuforums.org/showthread.php?t=399913)

I just pressed Esc at the Grub menu to get into the Console and then typed in ALL these commands. I even got Beryl working into the bargain!

Helen

---

### Post by gauss on 2007-05-23
I'm having fglrx/Feisty problems also. Here's part of my Xorg.0.log:
```
...
(EE) fglrx(0): GART is not initialized, disabling DRI
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
...
(II) fglrx(0): Direct rendering disabled
...
```
Xorg works and seems to be using fglrx rather than RADEON (as it did before I installed fglrx) but something is going wrong with GART/DRI.

fglrxinfo yields:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```
That would seem to indicate it's *not* using fglrx. :(

Does anyone have any hints as to what might be going on?

SOLVED:
I installed fglrx from ATI using the [Wiki HOWTO]("http://https://help.ubuntu.com/community/BinaryDriverHowto/ATI") and all is well. I have a vanilla 2.6.21 kernel patched for my Microsoft Ergonomic Keyboard 4000 so the posted fglrx package didn't work.

---

