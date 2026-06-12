---
title: "Disabling IRQ #7?!"
date: 2007-02-05
forum: Desktop Environments
---

### Post by ndove on 2007-02-05
Hey all.

I have a weird issue on my hands.

When I leave my PC idle for about 10 or so minutes, I get a syslogd message in my open terminal window saying "Disabling IRQ #7."

What this actually means is that it's disabling my mouse & keyboard. When I get back to the PC and attempt to use either of them, I get no response. And since I can't use them, I end up having to hard-reboot the system, even though the system is still working fine (responding, I mean. ie. if I push the power button, the log-off/shutdown/etc. window pops up still. And if I leave music playing, the music is still playing when I come back. This merely disables the IRQ controlling the mouse & keyboard.)

This happens *every* time I leave the PC idle for about 10 minutes, without failure (no pun intended.)

Does anybody know what could be causing this? And how I might go about fixing it?

Thanks in advance for any insight.

-Nick

---

### Post by ndove on 2007-02-05
Here's some more information. I tore through the last syslog and found this:

```
Feb  4 20:51:09 divine kernel: [ 2836.305310] irq 7: nobody cared (try booting with the "irqpoll" option)
Feb  4 20:51:09 divine kernel: [ 2836.305315]
Feb  4 20:51:09 divine kernel: [ 2836.305315] Call Trace:
Feb  4 20:51:09 divine kernel: [ 2836.305317]  <IRQ>  [__report_bad_irq+53/144] __report_bad_irq+0x35/0x90
Feb  4 20:51:09 divine kernel: [ 2836.305338]  [note_interrupt+544/640] note_interrupt+0x220/0x280
Feb  4 20:51:09 divine kernel: [ 2836.305354]  [_end+128100805/2130539984] :usbcore:usb_hcd_irq+0x25/0x60
Feb  4 20:51:09 divine kernel: [ 2836.305361]  [handle_level_irq+227/320] handle_level_irq+0xe3/0x140
Feb  4 20:51:09 divine kernel: [ 2836.305364]  [call_softirq+28/40] call_softirq+0x1c/0x28
Feb  4 20:51:09 divine kernel: [ 2836.305370]  [do_IRQ+138/240] do_IRQ+0x8a/0xf0
Feb  4 20:51:09 divine kernel: [ 2836.305373]  [default_idle+0/80] default_idle+0x0/0x50
Feb  4 20:51:09 divine kernel: [ 2836.305377]  [ret_from_intr+0/10] ret_from_intr+0x0/0xa
Feb  4 20:51:09 divine kernel: [ 2836.305379]  <EOI>  [unix_poll+0/160] unix_poll+0x0/0xa0
Feb  4 20:51:09 divine kernel: [ 2836.305388]  [default_idle+41/80] default_idle+0x29/0x50
Feb  4 20:51:09 divine kernel: [ 2836.305393]  [cpu_idle+155/208] cpu_idle+0x9b/0xd0
Feb  4 20:51:09 divine kernel: [ 2836.305397]  [start_secondary+1237/1264] start_secondary+0x4d5/0x4f0
Feb  4 20:51:09 divine kernel: [ 2836.305412]
Feb  4 20:51:09 divine kernel: [ 2836.305413] handlers:
Feb  4 20:51:09 divine kernel: [ 2836.305415] [_end+128100768/2130539984] (usb_hcd_irq+0x0/0x60 [usbcore])
Feb  4 20:51:09 divine kernel: [ 2836.305425] Disabling IRQ #7

```

Any ideas? :(

---

### Post by cheyen on 2007-02-16
I get a similar problem on one of my machines - although I'm slightly more fortunate than you in that the disabled IRQ 7 is assigned to acpi rather than my USB controller.

After a few minutes of inactivity I see:

```

Feb 11 02:01:45 uriel irq 7: nobody cared (try booting with the "irqpoll" option)
Feb 11 02:01:45 uriel [<c01331d4>] __report_bad_irq+0x24/0x80
Feb 11 02:01:45 uriel [<c0133417>] note_interrupt+0x1e7/0x220
Feb 11 02:01:45 uriel [<c0255c3e>] acpi_ev_sci_xrupt_handler+0x12/0x19
Feb 11 02:01:45 uriel [<c0250abd>] acpi_irq+0xb/0x14
Feb 11 02:01:45 uriel [<c0132865>] handle_IRQ_event+0x25/0x50
Feb 11 02:01:45 uriel [<c0133c8f>] handle_level_irq+0x8f/0xc0
Feb 11 02:01:45 uriel [<c0105230>] do_IRQ+0x40/0x80
Feb 11 02:01:45 uriel [<c01035cb>] common_interrupt+0x23/0x28
Feb 11 02:01:45 uriel [<c011a890>] __do_softirq+0x30/0x90
Feb 11 02:01:45 uriel [<c011a917>] do_softirq+0x27/0x30
Feb 11 02:01:45 uriel [<c0105235>] do_IRQ+0x45/0x80
Feb 11 02:01:45 uriel [<c01035cb>] common_interrupt+0x23/0x28
Feb 11 02:01:45 uriel [<c026ec95>] acpi_processor_idle+0x1b0/0x34b
Feb 11 02:01:45 uriel [<c010115c>] cpu_idle+0x3c/0x60
Feb 11 02:01:45 uriel [<c042a703>] start_kernel+0x273/0x300
Feb 11 02:01:45 uriel [<c042a230>] unknown_bootoption+0x0/0x260
Feb 11 02:01:45 uriel =======================
Feb 11 02:01:45 uriel handlers:
Feb 11 02:01:45 uriel [<c0250ab2>] (acpi_irq+0x0/0x14)
Feb 11 02:01:45 uriel Disabling IRQ #7
Feb 11 02:01:45 uriel spurious 8259A interrupt: IRQ7.

```

It seems to relate to the CPU entering an idle state (C1/C2 transition?) and doesn't appear to have a huge effect on the system (on this machine at least). Judging from the CPU temperature it still ramps down when idle even after this. I don't have cpufreq running on this machine (it's an Athlon Thunderbird), but I do have the disconnect bit enabled via athcool.

There seems to be a lot of reports of similar happenings around the net, but no specific cause as of yet.

**As a word of warning though, if I boot with the irqpoll option, as suggested in the error output, I get a kernel panic and hard lock up during boot.**

Not much help to you unfortunately, but you're not alone with this error, so hopefully they'll fix it shortly.

Have you tried looking for some way to change the USB IRQ in the BIOS? Or moving the USB to another PCI slot if possible? It won't stop the error, but it might disable something less important!

---

### Post by ndove on 2007-03-02
Aye!

Disabling the "PNP OS" option in BIOS allowed Ubuntu/Linux to set the hardware/IRQ stuff itself, the result of which was this problem going away. Sincerely strange, but I'm not asking question, heh.

Thanks for the help!

---

### Post by deathshadow on 2007-03-02
IRQ 7 is USUALLY the parallel port - I've had faulty parallel cables trip the printer IRQ and lock up other IRQ handlers. Usually in those cases it's two incompatable devices trying to share the same interrupt - which is why the PNP OS BIOS setting fixes it. 

The 'spurious 8259A' message is the telltale. Something is tripping a 'bad' interrupt that linux doesn't know how to handle. Usually that should just take down the parallel port - so it is most likely you had LPT1 and your USB trying to share that one interrupt.

Which is why I don't trust USB keyboards or Mice, still connecting via Mini-DIN.

---

