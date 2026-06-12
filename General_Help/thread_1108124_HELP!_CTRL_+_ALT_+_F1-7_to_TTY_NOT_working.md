---
title: "HELP! CTRL + ALT + F1-7 to TTY NOT working"
date: 2009-03-27
forum: General Help
---

### Post by VastOne on 2009-03-27
Upgrading nvidia drivers I suddenly find no access to TTY as I have always been able to do

CTRL ALT Backspace kills X but I need to get to tty1 or tty2 to stop gdm and I cannot open a tty

Is there a way to a tty other than the CTRL ALT method?

---

### Post by VastOne on 2009-03-27
> **VastOne said:**
> Upgrading nvidia drivers I suddenly find no access to TTY as I have always been able to do

CTRL ALT Backspace kills X but I need to get to tty1 or tty2 to stop gdm and I cannot open a tty

Is there a way to a tty other than the CTRL ALT method?

bump

---

### Post by hyperdude111 on 2009-03-27
check your xorg.conf and see if you have accidentally disaled the ALT-Ctrl-F1-7 commands

---

### Post by VastOne on 2009-03-27
> **hyperdude111 said:**
> check your xorg.conf and see if you have accidentally disaled the ALT-Ctrl-F1-7 commands

Nothing in the xorg.conf at all about ALT-CTRL-F1-7

Any where else I can try?

sudo start tty1 or tty2 tells me that the job is not changed

Thank you

---

### Post by VastOne on 2009-03-27
> **VastOne said:**
> Nothing in the xorg.conf at all about ALT-CTRL-F1-7

Any where else I can try?

sudo start tty1 or tty2 tells me that the job is not changed

Thank you

I figured it out...Never before seen or obviously used on my keyboard is an F Lock key that one of my cats MUST have stepped on  ....

(Grinning sheepishly)

I can now TTY

Thank you!

Needs marked as solved

---

