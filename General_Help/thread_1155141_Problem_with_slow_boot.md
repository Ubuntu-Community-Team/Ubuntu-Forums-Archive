---
title: "Problem with slow boot"
date: 2009-05-10
forum: General Help
---

### Post by Jisatsu on 2009-05-10
Hi everyone!

I am experiencing a slow boot with my newly installed Ubuntu Jaunty Jackalope.

Technical:
Acer Aspire 5680
Have both XP and Jaunty Jackalope on same laptop
Tried to reinstall, but to no success.


Windows xp boots faster:confused:
is it bluetooth? (laptops stops "thinking" when the bluetooth LED turns on)
I have tried all that i could figure out, but to no victory.

Below is a bootchart. Any ideas?

---

### Post by Tipped OuT on 2009-05-10
Wow that is a slow boot...3 minutes huh? And on a core..I have a old Pentium 4 and I boot up in 15 seconds..hmm

Does XP Boot up slow too?
Also how much partition space does Ubuntu have?

---

### Post by ibuclaw on 2009-05-10
It may appear that the majority of that bootup time is dedicated towards configuring devices.

If you look, the boot chart, Ubuntu is ready to begin after 15 seconds, but either modprobe or udev is giving an apparent "hang" on the system.

Can you open a terminal and run:
```
dmesg > ~/Desktop/boot.log
```
And either attach the file created, or paste it's contents in a [pastebin]("http://paste.ubuntu.com").

Regards
Iain

---

### Post by Jisatsu on 2009-05-10
Here is the logfile


I had to compress it. 60 kb was too much...
[URL="http://paste.ubuntu.com/169011/"]
http://paste.ubuntu.com/169011/[/URL]

---

### Post by ibuclaw on 2009-05-10
Firstly, in a slight offtopic manner ;)
```
[   13.926901] BUG: unable to handle kernel paging request at fffffff4

```
Are you running the 32bit version of Ubuntu? You may see some benefits using the [64bit version]("http://releases.ubuntu.com/jaunty/ubuntu-9.04-desktop-amd64.iso") instead.

Secondly, and to the point where I think it is going wrong:
```

[   13.926923] Oops: 0000 [#1] SMP
[   13.926926] last sysfs file: /sys/module/videodev/initstate
[   13.926930] Dumping ftrace buffer:
[   13.926933]    (ftrace buffer empty)
[   13.926935] Modules linked in: tuner_xc2028 tuner snd_hda_intel(+) snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss pcmcia(+) arc4            snd_seq_midi ecb snd_rawmidi saa7134(+) gspca_vc032x snd_seq_midi_event snd_seq iTCO_wdt iwl3945 ir_common gspca_main yenta_socket snd_timer snd_seq_device hid_a4tech iTCO_vendor_support acer_wmi psmouse sdhci_pci mac80211 compat_ioctl32 videodev rsrc_nonstatic pcmcia_core snd joydev pcspkr serio_raw sdhci     led_class v4l2_common videobuf_dma_sg videobuf_core tveeprom v4l1_compat nvidia(P) soundcore snd_page_alloc usbhid cfg80211 intel_agp agpgart video output  ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
[   13.926991]
[   13.926995] Pid: 1682, comm: modprobe Tainted: P           (2.6.28-11-generic #42-Ubuntu) Aspire 5680
[   13.926998] EIP: 0060:[<f7f8b2c0>] EFLAGS: 00010292 CPU: 0
[   13.927006] EIP is at saa7134_board_init2+0x140/0x710 [saa7134]
[   13.927008] EAX: 00000000 EBX: 00000000 ECX: 00000000 EDX: 00000000
[   13.927011] ESI: 00000000 EDI: 00000000 EBP: 00000000 ESP: f6177c54
[   13.927013]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[   13.927016] Process modprobe (pid: 1682, ti=f6176000 task=f62957f0 task.ti=f6176000)
[   13.927018] Stack:
[   13.927020]  00000303 f6177c58 f6177c58 f62a7000 f6fb7c00 f62a7000 f6177cd0 c014ade7
[   13.927027]  000000d0 f7f8d889 656e7574 00000072 000000f0 f62a74b0 00000000 f62a7140
[   13.927034]  f7f97490 f62a74b0 f6177cd0 f7f8d94d 65626f72 642d7000 006d6561 00000692
[   13.927042] Call Trace:
[   13.927044]  [<c014ade7>] ? request_module+0x97/0xf0
[   13.927050]  [<f7f8d889>] ? saa7134_i2c_eeprom+0xe9/0x110 [saa7134]
[   13.927064]  [<f7f8d94d>] ? saa7134_i2c_register+0x9d/0x120 [saa7134]
[   13.927074]  [<f7f965fc>] ? saa7134_initdev+0x3cc/0x8d5 [saa7134]
[   13.927089]  [<c02dc3fe>] ? pci_device_probe+0x5e/0x80
[   13.927096]  [<c034f004>] ? really_probe+0x54/0x180
[   13.927101]  [<c02dbc2e>] ? pci_match_device+0xbe/0xd0
[   13.927105]  [<c05021e4>] ? __down+0x64/0x90
[   13.927114]  [<c034f16e>] ? driver_probe_device+0x3e/0x50
[   13.927119]  [<c034f209>] ? __driver_attach+0x89/0x90
[   13.927124]  [<c034e943>] ? bus_for_each_dev+0x53/0x80
[   13.927127]  [<c02dc340>] ? pci_device_remove+0x0/0x40
[   13.927131]  [<c034eec9>] ? driver_attach+0x19/0x20
[   13.927134]  [<c034f180>] ? __driver_attach+0x0/0x90
[   13.927138]  [<c034e317>] ? bus_add_driver+0x1c7/0x240
[   13.927143]  [<c02dc340>] ? pci_device_remove+0x0/0x40
[   13.927147]  [<c034f3a9>] ? driver_register+0x69/0x140
[   13.927153]  [<f7f8d240>] ? saa7134_init+0x0/0x60 [saa7134]
[   13.927164]  [<c02dc65a>] ? __pci_register_driver+0x4a/0x90
[   13.927168]  [<f7f8d240>] ? saa7134_init+0x0/0x60 [saa7134]
[   13.927178]  [<f7f8d292>] ? saa7134_init+0x52/0x60 [saa7134]
[   13.927190]  [<c010111e>] ? _stext+0x2e/0x170
[   13.927194]  [<c020c015>] ? sysfs_addrm_finish+0x15/0xf0
[   13.927198]  [<c020b7e3>] ? sysfs_add_one+0x13/0x50
[   13.927201]  [<c020b85f>] ? sysfs_addrm_start+0x3f/0xa0
[   13.927205]  [<c01a908c>] ? __vunmap+0x9c/0xe0
[   13.927210]  [<c01a908c>] ? __vunmap+0x9c/0xe0
[   13.927214]  [<c0127c8d>] ? update_curr+0x8d/0x1e0
[   13.927218]  [<c012c6fc>] ? enqueue_entity+0x13c/0x360
[   13.927222]  [<c0128206>] ? wakeup_preempt_entity+0x76/0xb0
[   13.927226]  [<c0133b74>] ? try_to_wake_up+0x104/0x290
[   13.927235]  [<c0163fc8>] ? sys_init_module+0x88/0x1b0
[   13.927240]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
[   13.927243]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[   13.927248] Code: 15 58 57 c8 8b 55 90 8b 82 2c 01 00 00 89 5c 24 04 c7 04 24 b8 83 f9 f7 89 44 24 08 e8 f8 57 57 c8 66 90 8b 45 90 e8 40 fd ff ff <8b>  5d f4 31 c0 8b 75 f8 8b 7d fc 89 ec 5d c3 90 8b 4d 90 8b 71
[   13.927291] EIP: [<f7f8b2c0>] saa7134_board_init2+0x140/0x710 [saa7134] SS:ESP 0068:f6177c54
[   13.927303] ---[ end trace ed3970c99facbd63 ]---

```
The saa7134 driver seems to crash on loading, and could be the cause of the hang.
This is used for v4l (video4linux), and provides the ability to use the TV tuner in Linux. If you don't use this feature, you could try disabling it.

Run in a terminal
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
And add to the bottom line:
```
blacklist saa7134
```
Save and quit, then run:
```
sudo update-initramfs -u
```
And reboot.

Let us know if this helps, if not, revert the changes and we'll look into what else could be causing this.

Regards
Iain

---

### Post by Jisatsu on 2009-05-11
whooza!

That's more like it!
Thanx a bunch man!

That TV tuner didn't work anyways.:guitar:
______________________________________

I don't suppose you know how to kill/blacklist Bluetooth too? 
(never use that option either)

And what of that 64bit you mentioned? 
Sure that would work fine on my centrino DUO/dual core 2? 
Would it be possible to take a backup of files and settings?

Sorry if i ask too many questions.

---

