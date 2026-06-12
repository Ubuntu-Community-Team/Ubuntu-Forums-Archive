---
title: "Jaunty Upgrade Breaks ACPI"
date: 2009-05-03
forum: General Help
---

### Post by D0ckR0ach on 2009-05-03
Sorry to have to repost this, but my [last post]("http://ubuntuforums.org/showthread.php?t=1143143") didn't get any feedback.

I have reason to believe that the upgrade to 9.04, Jaunty Jackalope, has badly broken ACPI on my system (a Thinkpad X61).  Can anybody help me?

The best documentation I can provide is this powertop output:

```

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (85.8%)         2.41 Ghz    51.8%
C0                0.0ms ( 0.0%)         2.40 Ghz    19.7%
C1 mwait          0.0ms ( 0.0%)         2.00 Ghz    15.7%
C2 mwait          0.0ms ( 0.0%)         1.60 Ghz     9.1%
C3 mwait          0.1ms (14.2%)         1200 Mhz     3.1%

Wakeups-from-idle per second : 970.2    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  95.7% (4637.3)      <kernel IPI> : Rescheduling interrupts 
   2.1% (100.9)       <interrupt> : uhci_hcd:usb6, ohci1394, HDA Intel, wifi0 
   0.8% ( 39.7)       <interrupt> : i915@pci:0000:00:02.0 
   0.4% ( 20.5)           firefox : futex_wait (hrtimer_wakeup) 
   0.2% ( 10.5)       <interrupt> : ata_piix 
   0.2% ( 10.0)         rhythmbox : do_nanosleep (hrtimer_wakeup) 


```Also, booting with noacpi kernel parameter solves the issue.

---

### Post by D0ckR0ach on 2009-05-05
I figured it out, it was something caused by the hugely buggy trackerd.   I fixed it by not starting trackerd *ever*.

---

