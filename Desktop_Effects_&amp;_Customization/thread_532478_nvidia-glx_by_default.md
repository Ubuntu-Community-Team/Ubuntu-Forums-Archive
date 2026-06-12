---
title: "nvidia-glx by default"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by mevets on 2007-08-22
Hey, I have a friend thats wants to try out Ubuntu using the Live CD. I wanted to show him compiz and so on. The problem is that he has a nvidia card so it needs to load 'nvidia-glx' as the driver. After loading this driver one must restart. This makes it impossible to load compiz off the Live CD, cause once we restart, there goes all our work of loading the driver.

so my question is, is there a way to circumvent rebooting or otherwise get compiz to work under the live cd? Or are there any distrobustions that load 'nvidia-glx' by default during the live cd?

---

### Post by FuturePilot on 2007-08-22
This isn't possible to do with Ubuntu, but you might want to look into Sabayon which does this. But I think right now, Sabayon still uses Beryl.

---

### Post by Jucato on 2007-08-22
Er... actually you don't need to restart the computer for the nvidia driver to take effect. You just need to restart the X Server. After you have installed, configured, and loaded the nvidia driver, you just need to logout, then press Ctrl+Alt+Backspace to restart the X server. This will make the changes take effect without restarting the computer.

---

### Post by FuturePilot on 2007-08-22
I've tried that, but when you go to install the driver it also wants to install the kernel as well.
And the Restricted Manager won't work unless you have the latest kernel installed.

---

### Post by mevets on 2007-08-22
Ok cool, I'll try both tommarrow

Aye does anyone know if beryl is on sabayon's miniEdition?

---

### Post by sterilegenie on 2007-08-23
> **mevets said:**
> Ok cool, I'll try both tommarrow

Aye does anyone know if beryl is on sabayon's miniEdition?

Sabayon's mini edition is just that, no beryl, no sled menu, etc.

---

