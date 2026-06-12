---
title: "Off button [problems]"
date: 2015-09-03
forum: Desktop Environments
---

### Post by lubuntwf on 2015-09-03
In the OS Lubuntu 15.04. When I turn off from one of the buttons (lower left or bottom right of the desktop).
The message appears of close (OK in green). Later the logo of Lubuntu.

But then it stays at that screen and I have to press the off button.
What I have to do to turn off automatically?

Thanks! Regards.

---

### Post by Rex Bouwense on 2015-09-04
The power button has other options than shutdown (reboot, switch user, log out, etc).  That is why it does not proceed immediately to shutdown.  Once you choose shutdown, it will proceed to shutdown.  It may take a few seconds depending upon how many applications that you have open on the desktops.  You should not have to manually press your power button on your computer.

---

### Post by lubuntwf on 2015-09-04
> **Rex Bouwense said:**
> The power button has other options than  shutdown (reboot, switch user, log out, etc).  That is why it does not  proceed immediately to shutdown.  Once you choose shutdown, it will  proceed to shutdown.  It may take a few seconds depending upon how many  applications that you have open on the desktops.  You should not have to  manually press your power button on your computer.
Ok! So I did it again
Press shutdown, I waited several minutes and isn´t turn off.

> **Rex Bouwense said:**
> You should not have  to  manually press your power button on your computer.
Finally for that computer to shutdown I have to press the power button.
What can I do?

Thanks! ):P

---

### Post by howefield on 2015-09-04
> **lubuntwf said:**
> Finally for that computer to shutdown I have to press the power button.

I have the same issue (not every time but certainly most) and not had time to hunt down the cause or fix, might be kinder to the system to shutdown via the terminal with

> shutdown -h now

---

### Post by lubuntwf on 2015-09-04
```
shutdown -h now
```
It happens the same again.
Any solution?

Thanks! ):P

---

### Post by MartyBuntu on 2015-09-04
Is ACPI enabled in your BIOS?

---

### Post by lubuntwf on 2015-09-05
> **MartyBuntu said:**
> Is ACPI enabled in your BIOS?
When installed the OS, I selected:
*x* **acpi=off**
*x* **noapic**

With acpi enabled giving OS installation error.

Thanks! ):P

---

