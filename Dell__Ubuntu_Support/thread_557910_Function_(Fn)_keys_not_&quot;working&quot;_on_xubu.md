---
title: "Function (Fn) keys not &quot;working&quot; on xubuntu 7.04..."
date: 2007-09-23
forum: Dell  Ubuntu Support
---

### Post by sp00ki on 2007-09-23
I recently installed xubuntu 7.04 (replacing gnome ubuntu which was running since ver. 6) on a Dell Latitude X1 laptop. 
I've managed to get everything working ok, but i've been unable to find any packages relating to Fn (Function) key support (ie, Fn+Page Up=volume up, Fn+F10=Eject CD, etc).
I was able to find a package called i810switch for crt/lcd switching, but haven't yet been able to try it.
Does anyone know what the name or names of the package(s) gnome ubuntu contains to allow the user access to this functionality?

---

### Post by aldenhg on 2007-09-23
I'm having the exact same problem on my Vostro 1400. It just started after it worked for a month and a half. Weird.

---

### Post by sp00ki on 2007-10-02
Anyone?

---

### Post by NotoriousTF on 2007-10-08
I've just got this problem too. The Function keys on my laptop worked straight out of the box with Feisty, but since last week they just decided to stop working. Anyone out there have any ideas what could be happening?

---

### Post by jpittack on 2007-10-10
The issue is BIOS related for me.  If i use 1.7 on my 1501, I gain brightness keys.  Anything else and all I have is the wireless on/off.

What would be the name of the fn key if we tried to set up keyboard shortcuts?  Mabye we can put it all in manually?

---

### Post by dacap06 on 2007-10-28
Dell fn keys work partly under Linux.  They are handled by software in the i8kutils package in Ubuntu and Kubuntu.  This package scans and responds to your volume control, mute, and brightness keys.  This package also allows you to monitor CPU temperature and fan speed.

This package conflicts with the i8kfan package but provides its functionality.  Adept_manager and Synaptic should remove  i8kfan, if it is loaded, when you install i8utils.  Once installed, you can read about the i8k utilities in /usr/share/doc/i8kutils/README.i8kutils.gz

Good luck!

---

### Post by firmit on 2008-03-26
Same problem under Xubuntu 8.04beta
But after installing the suggested package, and choosing correct keyboard layout (Dell Latitude for me) under Settings->Keyboard->layout, everything worked fine.

---

