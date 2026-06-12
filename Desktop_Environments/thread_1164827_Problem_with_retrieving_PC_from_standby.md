---
title: "Problem with retrieving PC from standby"
date: 2009-05-20
forum: Desktop Environments
---

### Post by falconium on 2009-05-20
Hi,

My PC goes to standby, but when I want to switch it on again the following happens:

1st try: Cursor blinks at top left corner.

2nd try: I pressed the Enter, then I saw some crash report and the GUI came back. I found the following in /var/log/messages:


May 20 00:00:51 Blackhawk kernel: [   59.816045] ------------[ cut here ]------------
May 20 00:00:51 Blackhawk kernel: [   59.816047] WARNING: at /build/buildd/linux-2.6.28/arch/x86/kernel/setup.c:719 check_for_bios_corruption+0xc8/0xd0()
May 20 00:00:51 Blackhawk kernel: [   59.816051] Modules linked in: aes_i586 aes_generic isofs udf binfmt_misc ppdev bridge stp bnep video output input_polld
ev lp parport arc4 ecb snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_util_mem snd_hda_intel snd_
hwdep snd_pcm_oss snd_mixer_oss snd_seq_dummy snd_seq_oss snd_seq_midi snd_pcm snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device rt73usb crc_it
u_t snd rt2x00usb rt2x00lib emu10k1_gp psmouse hid_dell led_class iTCO_wdt iTCO_vendor_support gameport nvidia(P) soundcore pcspkr usblp snd_page_alloc intel
_agp serio_raw mac80211 usbhid cfg80211 agpgart usb_storage r8169 mii fbcon tileblit font bitblit softcursor
May 20 00:00:51 Blackhawk kernel: [   59.816088] Pid: 0, comm: swapper Tainted: P           2.6.28-11-generic #42-Ubuntu
May 20 00:00:51 Blackhawk kernel: [   59.816090] Call Trace:
May 20 00:00:51 Blackhawk kernel: [   59.816094]  [<c0139ab0>] warn_slowpath+0x60/0x80
May 20 00:00:51 Blackhawk kernel: [   59.816097]  [<c01537fa>] ? down_trylock+0x2a/0x40
May 20 00:00:51 Blackhawk kernel: [   59.816100]  [<c013a10d>] ? try_acquire_console_sem+0xd/0x30
May 20 00:00:51 Blackhawk kernel: [   59.816103]  [<c0154955>] ? sched_clock_cpu+0xd5/0x170
May 20 00:00:51 Blackhawk kernel: [   59.816106]  [<c0500ac6>] ? printk+0x18/0x1a
May 20 00:00:51 Blackhawk kernel: [   59.816109]  [<c01079c8>] check_for_bios_corruption+0xc8/0xd0
May 20 00:00:51 Blackhawk kernel: [   59.816112]  [<c01079d8>] periodic_check_for_corruption+0x8/0x30
May 20 00:00:51 Blackhawk kernel: [   59.816114]  [<c0143b00>] run_timer_softirq+0x130/0x200
May 20 00:00:51 Blackhawk kernel: [   59.816117]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
May 20 00:00:51 Blackhawk kernel: [   59.816120]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
May 20 00:00:51 Blackhawk kernel: [   59.816123]  [<c013f197>] __do_softirq+0x97/0x170
May 20 00:00:51 Blackhawk kernel: [   59.816125]  [<c0152ca6>] ? hrtimer_interrupt+0x186/0x1b0
May 20 00:00:51 Blackhawk kernel: [   59.816128]  [<c013f2cd>] do_softirq+0x5d/0x60
May 20 00:00:51 Blackhawk kernel: [   59.816130]  [<c013f445>] irq_exit+0x55/0x90
May 20 00:00:51 Blackhawk kernel: [   59.816133]  [<c011a07b>] smp_apic_timer_interrupt+0x5b/0x90
May 20 00:00:51 Blackhawk kernel: [   59.816135]  [<c050104a>] ? schedule+0x41a/0x710
May 20 00:00:51 Blackhawk kernel: [   59.816138]  [<c0105318>] apic_timer_interrupt+0x28/0x30
May 20 00:00:51 Blackhawk kernel: [   59.816140]  [<c010b012>] ? mwait_idle+0x42/0x50
May 20 00:00:51 Blackhawk kernel: [   59.816143]  [<c010285d>] cpu_idle+0x6d/0xd0
May 20 00:00:51 Blackhawk kernel: [   59.816145]  [<c04f110e>] rest_init+0x4e/0x60
May 20 00:00:51 Blackhawk kernel: [   59.816147] ---[ end trace a01ba4689a40f14d ]---
May 20 00:00:51 Blackhawk kernel: [   60.088021] usb 6-1: reset low speed USB device using uhci_hcd and address 2
May 20 00:00:51 Blackhawk kernel: [   60.512018] usb 7-1: reset full speed USB device using uhci_hcd and address 2
May 20 00:00:51 Blackhawk kernel: [   60.928018] usb 8-1: reset low speed USB device using uhci_hcd and address 2
May 20 00:00:51 Blackhawk kernel: [   61.238499] PM: resume devices took 11.256 seconds
May 20 00:00:51 Blackhawk kernel: [   61.238502] ------------[ cut here ]------------


Do you happen to know how to solve it?

Motherboard: Gigabyte GA-P35-DS4 rev2.0
[home page]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2624")
Galaxy 9800GT 256MB video card
4GB RAM
USB mouse+keyboard
External USB DVD writer

Thank you!

---

### Post by falconium on 2009-05-20
Sorry, I forgot to mention that at 2nd try when the GUI came back, there was no WIFI for example.
Its type is Asus WL-167G (specially chosen for linux by me).

---

### Post by Minsky on 2009-05-20
I've read somewhere that the standby\hibernation modes in operating systems sometimes conflict with the same funcion in the motherboard BIOS. Try disabling standby and hibernation in the BIOS, if the settings allow it, so that the operating system controls these functions, and see if that works. Other than that I can't help you I'm afraid

---

