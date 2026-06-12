---
title: "Xorg / system freeze with latest 2.6.10-5-amd64-k8 kernel + NVIDIA"
date: 2005-10-11
forum: Desktop Environments
---

### Post by robot on 2005-10-11
Hi all,


after running a routine apt-get update / apt-get upgrade on my Hoary box yesterday, things go haywire as soon as I start some OpenGL application (e.g. a screensaver, Doom3) and then try to close it and return to the desktop. The screen goes black and the entire box freezes soon thereafter.

I'm on an amd64, Geforce 6800GT with the latest NVIDIA drivers. I remember that the apt-get upgrade two days ago updated the kernel image and headers. It must be some change in there, as everything worked flawlessly before.

Here is a dump from /var/log/messages:

```
Oct 11 20:50:15 pandora kernel: Pid: 5791, comm: Xorg Tainted: P      2.6.10-5-amd64-k8
Oct 11 20:50:15 pandora kernel: RIP: 0010:[clear_page+7/57] <ffffffff801cc937>{clear_page+7}
Oct 11 20:50:15 pandora kernel: RSP: 0000:000001003ae01d70  EFLAGS: 00013246
Oct 11 20:50:15 pandora kernel: RAX: 0000000000000000 RBX: 0000010000000000 RCX: 0000000000000200
Oct 11 20:50:15 pandora kernel: RDX: 000000000002adfd RSI: ffffffff80315538 RDI: 000001002adfd000
Oct 11 20:50:15 pandora kernel: RBP: 0000010001960f58 R08: 0000000000000000 R09: 0000000001c6a000
Oct 11 20:50:15 pandora kernel: R10: 0000000001c6a000 R11: 0000000000000000 R12: 000001002a605350
Oct 11 20:50:15 pandora kernel: R13: 000001003f9d5ec8 R14: 000001003ade5070 R15: 000001003e24f2c0
Oct 11 20:50:15 pandora kernel: FS:  0000002a95e51090(0000) GS:ffffffff803f2540(0000) knlGS:000000005588ab40
Oct 11 20:50:15 pandora kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Oct 11 20:50:15 pandora kernel: CR2: 000001002adfd000 CR3: 0000000000101000 CR4: 00000000000006e0
Oct 11 20:50:15 pandora kernel: Process Xorg (pid: 5791, threadinfo 000001003ae00000, task 000001003e1aa9d0)
Oct 11 20:50:15 pandora kernel: Stack: ffffffff8015ece6 0000000001c6a000 000001003ade5070 000001003f9d5ec8
Oct 11 20:50:15 pandora kernel:        0000000001c6a000 0000000000000001 000001003e24f2c0 0000000000000000
Oct 11 20:50:15 pandora kernel:        ffffffff8015ee36 0000000000000001
Oct 11 20:50:15 pandora kernel: Call Trace:<ffffffff8015ece6>{do_anonymous_page+230} <ffffffff8015ee36>{do_no_page+102}
Oct 11 20:50:15 pandora kernel:        <ffffffff8015f282>{handle_mm_fault+210} <ffffffff8011e1f9>{do_page_fault+473}
Oct 11 20:50:15 pandora kernel:        <ffffffff80161d81>{do_brk+449} <ffffffff8017fb93>{sys_select+1347}
Oct 11 20:50:15 pandora kernel:        <ffffffff802ad896>{schedule+214} <ffffffff8010e9b5>{error_exit+0}
Oct 11 20:50:15 pandora kernel:
Oct 11 20:50:15 pandora kernel:
Oct 11 20:50:15 pandora kernel: Code: f3 48 ab c3 66 66 66 90 66 66 66 90 66 66 66 90 66 66 66 90
Oct 11 20:50:15 pandora kernel:  <1>Unable to handle kernel paging request at 000001003a5b0000 RIP:
Oct 11 20:50:15 pandora kernel: PML4 8063 PGD 9063 PMD 800000003a5b1163 PTE 9248db6d6ec1a163
Oct 11 20:50:15 pandora kernel: CPU 0
Oct 11 20:50:15 pandora kernel: Modules linked in: powernow_k8 proc_intf freq_table cpufreq_userspace cpufreq_ondemand cpufreq_powersave ipt_limit iptable_mangle ipt_LOG ipt_MASQUERADE iptable_nat ipt_TOS ipt_REJECT ip_conntrack_irc ip_conntrack_ftp ipt_state ip_conntrack iptable_filter ip_tables video sony_acpi pcc_acpi button battery container ac ipv6 tsdev sk98lin snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc usbhid ehci_hcd ohci_hcd floppy pcspkr ext2 evdev dm_mod capability commoncap video1394 ohci1394 raw1394 i2c_isa it87 i2c_sensor i2c_core nvidia sbp2 ieee1394 rtc psmouse mousedev parport_pc lp parport ide_generic ide_disk ide_cd amd74xx ide_core ext3 jbd mbcache sr_mod cdrom sd_mod 3w_xxxx sata_nv libata scsi_mod unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
Oct 11 20:50:15 pandora kernel: Pid: 7655, comm: gnome-panel Tainted: P      2.6.10-5-amd64-k8
Oct 11 20:50:15 pandora kernel: RIP: 0010:[copy_page+5/224] <ffffffff801cc975>{copy_page+5}
Oct 11 20:50:15 pandora kernel: RSP: 0000:000001002ea99db0  EFLAGS: 00010206
Oct 11 20:50:15 pandora kernel: RAX: 0000010000000000 RBX: 0000010001da6340 RCX: 0000000000000200
Oct 11 20:50:15 pandora kernel: RDX: 6db6db6db6db6db7 RSI: 000001003e658000 RDI: 000001003a5b0000
Oct 11 20:50:15 pandora kernel: RBP: 00000100341e5a30 R08: 0000000000000000 R09: 000001003248f638
Oct 11 20:50:15 pandora kernel: R10: 0000000000000000 R11: 0000000000000648 R12: 0000002a98fb4000
Oct 11 20:50:15 pandora kernel: R13: 0000000000000001 R14: 000001003e4d51c0 R15: 000001003e58e548
Oct 11 20:50:15 pandora kernel: FS:  0000002a981e4270(0000) GS:ffffffff803f2540(0000) knlGS:00000000563a8bb0
Oct 11 20:50:15 pandora kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Oct 11 20:50:15 pandora kernel: CR2: 000001003a5b0000 CR3: 0000000000101000 CR4: 00000000000006e0
Oct 11 20:50:15 pandora kernel: Process gnome-panel (pid: 7655, threadinfo 000001002ea98000, task 000001002f33c9d0)
Oct 11 20:50:15 pandora kernel: Stack: ffffffff8015ef21 00000000003dd000 0000010001cc3e80 0000000000000000
Oct 11 20:50:15 pandora kernel:        000001003248f638 000000012ea99e50 000001003248f638 0000002a98fb4000
Oct 11 20:50:15 pandora kernel:        000001003e4d51c0 0000000000000001
Oct 11 20:50:15 pandora kernel: Call Trace:<ffffffff8015ef21>{do_no_page+337} <ffffffff8015f282>{handle_mm_fault+210}
Oct 11 20:50:15 pandora kernel:        <ffffffff8011e1f9>{do_page_fault+473} <ffffffff801607fb>{vma_merge+267}
Oct 11 20:50:15 pandora kernel:        <ffffffff80161001>{do_mmap_pgoff+1553} <ffffffff802adcf0>{thread_return+41}
Oct 11 20:50:15 pandora kernel:        <ffffffff8010e9b5>{error_exit+0}
Oct 11 20:50:15 pandora kernel:
Oct 11 20:50:15 pandora kernel: Code: f3 48 a5 c3 89 64 24 08 4c 89 6c 24 10 b9 3b 00 00 00 66 66
```

Any help would be greatly appreciated. I sure hope they update the kernel soon!

Cheers!

---

### Post by jmbarbier on 2005-10-12
It was the same for me.. with a radeon card, and fglrx driver.

I reverted to xorg's ati, and everything worked (i don't need 3D)... so you could try reverting to xorg's nvidia driver, and test... kernel may have been updated, but not third parties modules like fglrx or nvidia. 

by the same way, i've lost sound. Alsa in xmms works, but not in gnome (alsasink fails)...

had no time yet to search the solution...

bye
JM

---

### Post by jmbarbier on 2005-10-12
oops... for the sound, it was my fault... a mistake with /etc/modprobe.d....

but for the freezes, I confirm that reverting to xorg's ati driver makes things OK..

---

