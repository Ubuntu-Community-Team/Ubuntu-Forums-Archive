---
title: "Daily crashes"
date: 2006-04-12
forum: Desktop Environments
---

### Post by wvelez on 2006-04-12
Hi guys,

I´m running Breezy Badger happily on a laptop and have NOT had any problems for the last 4 months.  On the other hand I installed Breezy on my desktop and lately I have to deal with a daily freeze/lockup.  When it happens I can ssh into the computer but X is completely unresponsive.  It seems to happen randomly and cannot figure out what it is.  Below I´m attaching the section of the problem from syslog.  Any help will be greatly appreciated!!!

Thank you.

Apr 12 20:02:01 localhost kernel: [4307379.208000] Unable to handle kernel paging request at virtual address 80000004
Apr 12 20:02:01 localhost kernel: [4307379.208000]  printing eip:
Apr 12 20:02:01 localhost kernel: [4307379.208000] c0158b39
Apr 12 20:02:02 localhost kernel: [4307379.208000] *pde = 00000000
Apr 12 20:02:02 localhost kernel: [4307379.208000] Oops: 0002 [#1]
Apr 12 20:02:02 localhost kernel: [4307379.208000] Modules linked in: vmnet vmmon binfmt_misc speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative fglrx ipv6 irtty_sir sir_dev irda crc_ccitt floppy pcspkr rtc bt878 tuner tvaudio bttv video_buf firmware_class i2c_algo_bit v4l2_common btcx_risc tveeprom i2c_core videodev snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc tpm_atmel tpm_nsc tpm shpchp pci_hotplug intel_agp agpgart dm_mod tsdev evdev snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore psmouse mousedev parport_pc lp parport md ext3 jbd thermal processor fan 8139too 8139cp mii ehci_hcd uhci_hcd usbcore ide_cd cdrom ide_disk ide_generic ata_piix libata scsi_mod piix ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
Apr 12 20:02:02 localhost kernel: [4307379.208000] CPU:    0
Apr 12 20:02:02 localhost kernel: [4307379.208000] EIP:    0060:[prune_icache+230/392]    Tainted: P      VLI
Apr 12 20:02:02 localhost kernel: [4307379.208000] EFLAGS: 00010286   (2.6.12-10-386)
Apr 12 20:02:02 localhost kernel: [4307379.208000] EIP is at prune_icache+0xe6/0x188
Apr 12 20:02:02 localhost kernel: [4307379.208000] eax: 80000000   ebx: eb2b2644   ecx: eb2b2644   edx: c18d2630
Apr 12 20:02:02 localhost kernel: [4307379.208000] esi: eb2b264c   edi: 00000002   ebp: 0000007a   esp: dfecbeb8
Apr 12 20:02:02 localhost kernel: [4307379.208000] ds: 007b   es: 007b   ss: 0068
Apr 12 20:02:02 localhost kernel: [4307379.208000] Process kswapd0 (pid: 133, threadinfo=dfeca000 task=dfe6aa20)
Apr 12 20:02:02 localhost kernel: [4307379.208000] Stack: 0000007a eb2b2824 eb6e3e2c 00000000 00000080 00000000 dfffe9e0 c0158bf3
Apr 12 20:02:02 localhost kernel: [4307379.208000]        00000080 c013630b 00000080 000000d0 0003e800 c0132fc1 0003e800 00000000
Apr 12 20:02:02 localhost kernel: [4307379.208000]        dfecbf04 00000001 00000000 c02a05c0 00000000 00000002 0000000c c01372b4
Apr 12 20:02:02 localhost kernel: [4307379.208000] Call Trace:
Apr 12 20:02:02 localhost kernel: [4307379.208000]  [shrink_icache_memory+24/48] shrink_icache_memory+0x18/0x30
Apr 12 20:02:02 localhost kernel: [4307379.208000]  [shrink_slab+241/306] shrink_slab+0xf1/0x132
Apr 12 20:02:02 localhost kernel: [4307379.208000]  [throttle_vm_writeout+27/84] throttle_vm_writeout+0x1b/0x54
Apr 12 20:02:02 localhost kernel: [4307379.208000]  [balance_pgdat+494/789] balance_pgdat+0x1ee/0x315
Apr 12 20:02:02 localhost kernel: [4307379.208000]  [kswapd+226/231] kswapd+0xe2/0xe7
Apr 12 20:02:02 localhost kernel: [4307379.208000]  [autoremove_wake_function+0/58] autoremove_wake_function+0x0/0x3a
Apr 12 20:02:02 localhost kernel: [4307379.208000]  [autoremove_wake_function+0/58] autoremove_wake_function+0x0/0x3a
Apr 12 20:02:02 localhost kernel: [4307379.208000]  [kswapd+0/231] kswapd+0x0/0xe7
Apr 12 20:02:02 localhost kernel: [4307379.208000]  [kernel_thread_helper+5/11] kernel_thread_helper+0x5/0xb
Apr 12 20:02:02 localhost kernel: [4307379.208000] Code: 73 09 00 00 58 a1 2c 1a 2a c0 83 e8 08 39 c3 75 6b 53 e8 fa fe ff ff 85 c0 5e 74 60 8b 53 04 85 d2 74 18 8b 03 85 c0 89 02 74 03 <89> 50 04 c7 03 00 00 00 00 c7 43 04 00 00 00 00 8d 43 10 8b 53

---

### Post by apjone on 2006-04-12
check your ACPI settings

---

### Post by wvelez on 2006-04-12
Thanks Anthony,

I´m not running either: ACPI-SUPPORT nor ACPID.  Should I turn that off on BIOS?

Regards,
-will

---

### Post by apjone on 2006-04-12
yeah , give it a try

---

### Post by er-ku on 2006-04-12
Just to be sure - try to run memtest (it's available in the boot menu). Maybe your RAM is defective, or so...

---

### Post by psyko-lefse on 2006-04-12
I've had the same problem since I installed 5.10 on my laptop, it freezes occasionaly.
Will be following this thread.

---

### Post by amunimanghi on 2006-04-12
my computer was crashing/freezing but it was because one of my fans were turned off.

---

### Post by wvelez on 2006-04-13
Hi guys,

I ran memtest overnight and I do have bad RAM.  Unfortunately, the picture I took came out blurry but fairly legible.  I have 2 512Mb RAM chips, is it possible to determine which one is bad from the screenshot?

Thanks a bunch,
-will

---

### Post by Sef on 2006-04-13
In your situation will, I would buy a new 512 chip and replace one chip.  If the problem cleared up, great. If not, then I would replace the other chip.

---

### Post by psyko-lefse on 2006-04-13
DAMN! I just ran a memtest on my laptop, it passed. And when booting up in Ubuntu, it froze again, this time with a uptime of only 10 min.

This problem makes Ubuntu pretty much useless for school-work, and about everything else. 

Does anybody have a clue too whats going one?
I do get an error during boot-up, it fails to mount local filesystem, can this be the problem?

---

### Post by Sef on 2006-04-13
> I do get an error during boot-up, it fails to mount local filesystem, can this be the problem?

Yes that could be the problem.  I had the same problem and it kept crashing.  Finally had to reinstall and that fixed the problem.  I think my problem was going into the update manager and updating the kernel.  Haven't done it and all is well.

---

### Post by psyko-lefse on 2006-04-13
There has to be a way to fix this without reinstall, right? 
I mean, its linux :p

---

### Post by wvelez on 2006-04-13
psyko,

Reboot, press ESC the minute Ubuntu starts booting, it'll give you that option but you only have 5 seconds.  Go into safe mode, provide your password and once you're in a prompt type:

umount /
fsck -yf

Once it's done it'll tell you if fsck fixed any problems with your file system.

Good luck,
-will

---

