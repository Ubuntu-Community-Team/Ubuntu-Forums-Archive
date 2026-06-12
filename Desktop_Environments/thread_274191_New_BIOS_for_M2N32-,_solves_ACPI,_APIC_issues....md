---
title: "New BIOS for M2N32-*, solves ACPI, APIC issues..."
date: 2006-10-09
forum: Desktop Environments
---

### Post by CRCarl on 2006-10-09
All - 
   On 10/6/06 Asus posted BIOS version 703, the relese notes read - "Fixed Linux compatibility issue". I've been running the new BIOS for 3 days now, it's like a new computer. 

My old boot line was - 
/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda1 ro verbose no_timer_check noacpi acpi=off noapci nolapci

My current boot line is - 
/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda1 ro verbose

Before the BIOS update USB would die after a couple of hours with these errors - 

Sep 28 02:03:06 linux-desktop -- MARK --
Sep 28 02:23:07 linux-desktop -- MARK --
Sep 28 02:37:27 linux-desktop kernel: [10508.415278] 
Sep 28 02:37:27 linux-desktop kernel: [10508.415278] Call Trace:<ffffffff80168c95>{__report_bad_irq+53} <ffffffff80168f0a>{note_interrupt+538}
Sep 28 02:37:27 linux-desktop kernel: [10508.415302]        <ffffffff880a188a>{:usbcore:usb_hcd_irq+42} <ffffffff801685f7>{__do_IRQ+215}
Sep 28 02:37:27 linux-desktop kernel: [10508.415329]        <ffffffff8011302f>{do_IRQ+47} <ffffffff80110460>{ret_from_intr+0}
Sep 28 02:37:27 linux-desktop kernel: [10508.415340]        

No more problems at all. Strongly suggested to anyone running these ASUS motherboards. 

Craig

---

