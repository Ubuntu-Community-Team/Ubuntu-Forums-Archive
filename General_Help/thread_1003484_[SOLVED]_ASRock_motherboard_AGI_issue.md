---
title: "[SOLVED] ASRock motherboard AGI issue"
date: 2008-12-06
forum: General Help
---

### Post by ppm on 2008-12-06
Hi

(K)Ubuntu seems have problems with these motherboards when AGP card (at least nvidia) is used instead of the integrated one (Confirmed for ASRock p4i65gv). I could not even boot the system with live-cd (either 8.04 or 8.10). Some people seem to be able to install the system with "Alternative installer".

Luckily, I had a working installation of 8.10 on my hard disk and could boot the system once in a while (random success). Blacklisting **intel_agp module** did the trick for me as for this poster (thank you):
[http://ubuntuforums.org/showthread.php?t=399362&highlight=intel_agp+asrock]("http://ubuntuforums.org/showthread.php?t=399362&highlight=intel_agp+asrock")
):P

I do not know whether this is a kernel bug or ignorance from ASRock's side by not providing a decent specification of their products. I did some googling on this and found out that this issue has been around since Ubuntu 6.06 was released. I hope this issue will be resolved in the next release of Ubuntu either by kernel developers or with a work-around from Ubuntu team.

As for AGI:
[http://en.wikipedia.org/wiki/Asrock_Graphics_Interface]("http://en.wikipedia.org/wiki/Asrock_Graphics_Interface")

A brief extract of dmesg

> 
[  142.048372] Oops: 0003 [#32] SMP
[  142.048535] Modules linked in: dm_crypt dm_mod ac snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm nvidia(P) psmouse serio_raw i2c_core snd_seq_dummy snd_seq_oss snd_seq_midi_event snd_seq snd_timer snd_seq_device iTCO_wdt snd button evdev soundcore iTCO_vendor_support shpchp pci_hotplug snd_page_alloc pcspkr intel_agp agpgart ext3 jbd mbcache sg sr_mod sd_mod cdrom pata_acpi 8139too ata_piix 8139cp mii ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  142.051638]
[  142.051701] Pid: 3783, comm: savelog Tainted: P      D (2.6.24-21-generic #1)
[  142.051769] EIP: 0060:[<c032033f>] EFLAGS: 00010246 CPU: 0
[  142.051840] EIP is at iret_exc+0x5fa/0x89f
[  142.051904] EAX: 00000000 EBX: df9a79b4 ECX: 00000012 EDX: e9f14000
[  142.051970] ESI: e9f14000 EDI: ff867fea EBP: 00000000 ESP: f3001f38
[  142.052036]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[  142.052102] Process savelog (pid: 3783, ti=f3000000 task=df8b5140 task.ti=f3000000)
[  142.052168] Stack: 0000000c 00000012 bfffffea 00000012 c01959fc df9a7900 c17fc680 ff867000
[  142.052692]        bffff000 00000012 00000fea c17fc680 e9f14000 f3000000 c0000000 e9f14000
[  142.053216]        00000080 c0195a71 df9a7900 df88c000 c01976cd 08060724 08060718 e9f14000
[  142.053739] Call Trace:
[  142.053863]  [<c01959fc>] copy_strings+0x13c/0x190
[  142.053989]  [<c0195a71>] copy_strings_kernel+0x21/0x40
[  142.054108]  [<c01976cd>] do_execve+0x13d/0x1d0
[  142.054227]  [<c0102aef>] sys_execve+0x2f/0x80
[  142.054346]  [<c01043b2>] sysenter_past_esp+0x6b/0xa9
[  142.054469]  [<c0310000>] unix_destruct_fds+0x40/0x50
[  142.054592]  =======================
[  142.054654] Code: f2 ff ff ff e9 69 9d ef ff 8d 0c 88 e9 60 a3 ef ff 01 c1 e9 b4 a3 ef ff 8d 0c 88 e9 ac a3 ef ff 01 c1 eb 03 8d 0c 88 51 50 31 c0 <f3> aa 58 59 e9 08 a4 ef ff 8d 0c 88 51 50 31 c0 f3 aa 58 59 e9


---

### Post by ppm on 2010-05-01
I just did a clean KUbuntu 10.04 installation and I was sad to notice that the problem persists... :(

---

