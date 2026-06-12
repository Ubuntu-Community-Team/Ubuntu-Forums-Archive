---
title: "Blanking on login screen  How to stop?"
date: 2024-01-30
forum: Desktop Environments
---

### Post by vidtek on 2024-01-30
I have googled and searched and been unable to find any fix for this.

I want the login screen to stay on permanently and not blank at all.

All display managers have this annoying trait, I've tried them all.

---

### Post by MAFoElffen on 2024-01-30
The login screen is in the console before the desktop... Add "consoleblank=0" to the GRUB_CMDLINE_LINUX_DEFAUTL line in /etc/default/grub file and pick up the chang using update-grub.

---

### Post by vidtek on 2024-01-31
> **MAFoElffen said:**
> The login screen is in the console before the desktop... Add "consoleblank=0" to the GRUB_CMDLINE_LINUX_DEFAUTL line in /etc/default/grub file and pick up the chang using update-grub.


Thank you for your reply.   Unfortunately that doesn't work, tried on Jammy kubuntu and Victoria XFCE mint.  That was one of the very first things I tried.

Cheers Tony.

---

