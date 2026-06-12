---
title: "acpi=off"
date: 2006-02-24
forum: Desktop Environments
---

### Post by Digidiz on 2006-02-24
i installed linux with that option, what does it mean?? i can only get linux to hibernate and not go to standby

if acpi needs to be installed how do i do it??

---

### Post by art on 2006-02-24
ACPI stands for Advanced Configuration and Power Interface, it is needed for things like hibernate and battery monitoring, and generally these are needed for laptops. If yours is a laptop, I would recommend enabling it. I don't know what you mean by "i installed linux with that option", you mean you put that in /grub/menu.lst?

---

### Post by Digidiz on 2006-02-24
i installed linux with the option LINUX acpi=off, because my computer kept on hanging on installation, once it came to a particular moment. i do know what acpi stands for, as its a windows function. no, its not a laptop, its a desktop computer

---

### Post by az on 2006-02-24
[QUOTE=Digidiz]i installed linux with the option LINUX acpi=off, because my computer kept on hanging on installation, once it came to a particular moment. i do know what acpi stands for, as its a windows function. no, its not a laptop, its a desktop computer[/QUOTE]
What power management options can you set in the bios?

Without acpi, you can still use apm.  It all depends on what your motherboard is set  to use.

If acpi is off, and Ubuntu-desktop is installed, it is autodetected at boot and apm is enabled.

What happend if you type

sudo apm -s
(save your data first...)

---

### Post by art on 2006-02-24
Yeah, you don't really need ACPI on a desktop, I wouldn't worry. APM will do the job.

---

### Post by az on 2006-02-24
Standby and hibernate are really useful for a desktop, too....

---

### Post by Digidiz on 2006-02-25
yea but i havent got the option for standby just hibernate

---

### Post by scifi on 2006-02-25
APM or ACPI are mainboard/BIOS functions, so you will have to alter these settings in the BIOS. Then your OS can make use of it, or not.

---

