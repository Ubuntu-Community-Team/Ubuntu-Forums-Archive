---
title: "Duelling Desktops -- (Lubuntu-Desktop on Kubuntu 11.10)"
date: 2012-01-12
forum: Desktop Environments
---

### Post by scubscub on 2012-01-12
Hi all, I installed lubuntu-desktop on my Kubuntu 11.10 system because I was under the impression that it would be easy to switch between environments from the login screen.

It is, but there does seem to be interference between the two.  For one thing, my KDE system settings (monitor, desktop settings, mouse controls) etc are there in lubuntu (but overridden by the LXDE controls?).  Synaptic crashes when I try to open it in lubuntu.  KDE's Muon is listed in the System Tools menu, but I'm hesitant to use it since I don't know how it interacts with LXDE.

Bottom line, is there a way to get these two to play nicely on the same system, or do I have to make a choice and uninstall one or the other?

---

### Post by LinuxFan999 on 2012-01-12
If you want both LXDE and KDE, then remove lubuntu-desktop and install the regular (non-lubuntu) LXDE desktop environment. Installing lubuntu-desktop on Kubuntu is not recommended because lubuntu-desktop and kubuntu-desktop can conflict with each other and cause problems.

---

### Post by scubscub on 2012-01-13
I see.  If I uninstall kubuntu-desktop would this also resolve the conflict?

---

### Post by LinuxFan999 on 2012-01-19
> **scubscub said:**
> I see.  If I uninstall kubuntu-desktop would this also resolve the conflict?
Yes, it should, but only if you do it through the terminal.

---

