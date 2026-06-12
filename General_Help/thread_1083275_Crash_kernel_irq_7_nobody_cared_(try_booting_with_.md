---
title: "Crash: kernel: irq 7: nobody cared (try booting with the &quot;irqpoll&quot; option)"
date: 2009-02-28
forum: General Help
---

### Post by hyunkell on 2009-02-28
Hello,

I recently aquired a dedicated server (at a hosting company) in order to host a few webpages / teamspeak and so on.

It is running Ubuntu Server 8.04 (since Ubuntu is the only linux distro I'm kind of familiar with)

Here's the problem:
It crashes randomly, and I need to do a hard reboot to bring it back up (thankfully I can do that using a web interface)

I found the cause of the crash in the syslog:

> Feb 28 23:13:17 cyberia kernel: irq 7: nobody cared (try booting with the "irqpoll" option)
Feb 28 23:13:17 cyberia kernel: Pid: 0, comm: swapper Not tainted 2.6.28.2 #1
Feb 28 23:13:17 cyberia kernel: Call Trace:
Feb 28 23:13:17 cyberia kernel:  [<c024c8b4>] __report_bad_irq+0x24/0x90
Feb 28 23:13:17 cyberia kernel:  [<c024ca89>] note_interrupt+0x169/0x1b0
Feb 28 23:13:17 cyberia kernel:  [<c024b705>] handle_IRQ_event+0x25/0x60
Feb 28 23:13:17 cyberia kernel:  [<c024d68b>] handle_level_irq+0xab/0xd0
Feb 28 23:13:17 cyberia kernel:  [<c0205f0d>] do_IRQ+0x4d/0x90
Feb 28 23:13:17 cyberia kernel:  [<c0204303>] common_interrupt+0x23/0x30
Feb 28 23:13:17 cyberia kernel:  [<c0209f2e>] default_idle+0x2e/0x40
Feb 28 23:13:17 cyberia kernel:  [<c020a0e9>] c1e_idle+0x69/0xf0
Feb 28 23:13:17 cyberia kernel:  [<c024e170>] rcu_pending+0x40/0x50
Feb 28 23:13:17 cyberia kernel:  [<c0201c2b>] cpu_idle+0x4b/0xa0
Feb 28 23:13:17 cyberia kernel: handlers:
Feb 28 23:13:17 cyberia kernel: [<c0611730>] (usb_hcd_irq+0x0/0x70)
Feb 28 23:13:17 cyberia kernel: [<c0611730>] (usb_hcd_irq+0x0/0x70)
Feb 28 23:13:17 cyberia kernel: Disabling IRQ #7

After this, the server is gone.


Now I know, there's quite alot of results on google about that, but everyone seems to have a completely different problem.

I was wondering if you could suggest a few things, how to fix the machine.
The obvious thing to do would be to add "irqpoll", but I've seen reports that this causes kernel panic on boot (which would be seriously bad, since it's a dedicated machine, and I'd have to ask the company to reinstall ubuntu)

I'm also not sure how to figure out what exactly IRQ 7 is.
Are there any commands to list all the IRQs and what they do?

Thanks,
Hyu

---

### Post by geraldm on 2009-02-28
To look at the interrupts in use look under /proc (which is for all processes)
cat /proc/interrupts

Gerald

---

### Post by hyunkell on 2009-02-28
hey geraldm, thanks for showing me how to see the interrupts.

```
           CPU0       CPU1
  0:         60          0    XT-PIC-XT        timer
  1:          2          0    XT-PIC-XT        i8042
  2:          0          0    XT-PIC-XT        cascade
  7:     101011     945344    XT-PIC-XT        ohci_hcd:usb1, ohci_hcd:usb2
 10:     899238      98010    XT-PIC-XT        ohci_hcd:usb3, ohci_hcd:usb4, ohci_hcd:usb5, eth0
 11:      45624       1949    XT-PIC-XT        ahci
NMI:          0          0   Non-maskable interrupts
LOC:    2353741    2353698   Local timer interrupts
RES:      19799      33399   Rescheduling interrupts
CAL:         85         60   Function call interrupts
TLB:        202        401   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:       2650
MIS:          0

```

so, #7 seems to be onboard usb.
not too sure what I should think of that, I don't know if the usb ports are in use, I doubt they are though.

Is it normal for so many things to share the same interrupts? I thought it was one interrupt per piece of hardware.
Then again, I don't know much about interrupts at all.

Any ideas how I could fix the crashing issue?

---

### Post by dcstar on 2009-02-28
> **hyunkell said:**
> hey geraldm, thanks for showing me how to see the interrupts.

```
           CPU0       CPU1
  0:         60          0    XT-PIC-XT        timer
  1:          2          0    XT-PIC-XT        i8042
  2:          0          0    XT-PIC-XT        cascade
  7:     101011     945344    XT-PIC-XT        ohci_hcd:usb1, ohci_hcd:usb2
 10:     899238      98010    XT-PIC-XT        ohci_hcd:usb3, ohci_hcd:usb4, ohci_hcd:usb5, eth0
 11:      45624       1949    XT-PIC-XT        ahci
NMI:          0          0   Non-maskable interrupts
LOC:    2353741    2353698   Local timer interrupts
RES:      19799      33399   Rescheduling interrupts
CAL:         85         60   Function call interrupts
TLB:        202        401   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:       2650
MIS:          0

```

so, #7 seems to be onboard usb.
not too sure what I should think of that, I don't know if the usb ports are in use, I doubt they are though.

Is it normal for so many things to share the same interrupts? I thought it was one interrupt per piece of hardware.
Then again, I don't know much about interrupts at all.

Any ideas how I could fix the crashing issue?

IRQ7 can also be assigned to Parallel Ports, you may want to go into the BIOS and disable anything that uses that IRQ.

I would be concerned that there is an underlying hardware problem that is just manifesting itself with that particular error - you could waste a lot of time mucking around with things and not make it any more reliable.

---

### Post by hyunkell on 2009-03-01
I understand that this may be related to hardware problem, but before I ask the hosting company about changing hardware, I want to make sure that there is nothing on my side I can do to fix this problem.

I guess I'll rent a kvm over ip, and have a look at the bios, thanks.

---

### Post by gyterpena on 2010-03-26
Hi I had the same problem on all Ubuntu releases since 7.10 with via-rhine driver. Kernel oopses straight away after you plug the Ethernet cable. Fix that works for me is to boot with irqfixup this makes ethernet more stable but introduces new problem   "NETDEV WATCHDOG: eth3 (via-rhine): transmit queue 0 timed out" this can be fixed with noapic option in my case network card is in pci slot so I use pci=noapic. Try to boot with irqfixup and if you'll have more problems try both options.

---

### Post by yp2 on 2010-05-10
Try booting with kernel option noirqdebug (add to grub). This may help.

---

