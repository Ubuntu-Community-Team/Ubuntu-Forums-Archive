---
title: "Display sleep on EEE"
date: 2008-12-20
forum: General Help
---

### Post by Krydahl on 2008-12-20
For some reason no matter what I do with the various settings in the power manager, my EEE (901 20gig running xubuntu 8.10 with adamm's kernel) puts the display to sleep after about 30 secs of inactivity when it's on the battery. I'm guessing this is something to do with the way laptop-mode is configured, but I can't see what.

Does anyone have any idea where I can change this timer?

---

### Post by der_joachim on 2008-12-21
I am not a XFCE user, but in Gnome I normally use Preferences >> Power Management to configure screen blanking. The same goes for KDE. So if your XFCE desktop has a power management setting, I'd search there.

Alternatively, array's repository has a tool called eeecontrol. This is a tray applet which configures both ACPI events and Fn-combos. You *may* find some configuration options here, but I recently ditched ubuntu on my EEE, so I cannot double check.

---

### Post by Krydahl on 2008-12-22
Thanks for the reply.

I tried power management. This only seems to happen when I've got it set up to dim the screen when on battery - and the power manager (which is the gnome power manager in XFCE anyway) doesn't seem to have any options to set when the screen will dim or to what degree.

I'll look into eeecontrol, thanks for the tip.

---

