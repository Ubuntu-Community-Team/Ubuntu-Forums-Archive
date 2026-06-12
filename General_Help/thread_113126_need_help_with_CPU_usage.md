---
title: "need help with CPU usage"
date: 2006-01-05
forum: General Help
---

### Post by cooldudejz on 2006-01-05
i have a AMD 1.05 processor. i have recently downloaded a few new mac os themes and icons, along with a new GDM and splash screen, i have also just begun using gdesklets. when i restart my computer everything is fine, but after about 2 hours or more my cpu usage goes to 100% and stays there. my computer almost becomes unusable. does anyone know what might be wrong. thanx

---

### Post by 23meg on 2006-01-05
Can you paste the output of the "top" command when this happens?

---

### Post by cooldudejz on 2006-01-05
ya i will, but it becomes almost so unstable that clicking on something takes forever and i think if i were to try to paste something onto a website it would crash. when the cpu usage goes to 100%, i try to go to system monitor to see whats up and it freezes, everything including the mouse, no commands work (ctrl+alt+backspace) and the LED on the computer case stays on. my only option really is to hit the restart button.

---

### Post by Mattj on 2006-01-05
can i suggest just trying to turn ACPI off? as incorrect ACPI configs (sometimes the default ones) on some systems have caused me loads of trouble.

At boot add ```
acpi=off
``` to the boot line (May haveto press 'e' in grub to get to the edit screen, then press enter to save, and 'b' to boot.

Just an idea, See how you get on.

-Matt

---

### Post by cooldudejz on 2006-01-17
hey i know what it is now i typed in top and i see my Xorg is going crazy. it is getting stuck at around 95% for no reason. do i need the nvidia drivers. i had these before and they seemed no make my computer randomly freeze, this was in 5.04. any help. thanx

---

