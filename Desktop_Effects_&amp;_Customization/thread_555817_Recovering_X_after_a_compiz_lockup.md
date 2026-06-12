---
title: "Recovering X after a compiz lockup"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by mikeym on 2007-09-20
Hi,

Could someone tell me the best way to recover X after compiz locks up the session? (which it does quite a lot) 

So far the best I can manage is the sequesnce

[alt] + [system request] + R (release keayboard from raw mode)
[alt] + [system request] + E (terminate all processes)
[alt] + [system request] + I (kill all processes)
[alt] + [system request] + S (sychronise disks)
[alt] + [system request] + U (remount file system read only)
[alt] + [system request] + B (reboot)

I have also managed to get a small level of control back by typing

[alt] + [system request] + R (to get keyboard)
[ctrl] + [alt] + Backspace (to restart X)
and failing that [alt] + [system request] + F2 to get to the terminal

But once I'm at the terminal I can't get control back from compiz and the best I can do is a 'reboot' command or ''init 6'.

So what is the best way to recover?

---

### Post by ddrichardson on 2007-09-21
What happens with CTRL-ALT-Backspace to kill the X server or using CTRL-ALT-F7 or F2 to switch out of X?

If you can get a terminal then /etc/init.d/gdm stop

---

### Post by mikeym on 2007-09-21
[ctrl]+[alt]+Backspace doesn't work unless you use [alt]+[sysrq]+R first to get keyboard back and sometime not even then [ctrl]+[alt]+F2 works more often but I couldn't get control back.

---

### Post by ddrichardson on 2007-09-21
Is this purely down to Compiz, or is there a power management issue as well? Does it lock up when you disable power saving?

---

