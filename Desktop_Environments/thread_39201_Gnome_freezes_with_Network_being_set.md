---
title: "Gnome freezes with Network being set"
date: 2005-06-03
forum: Desktop Environments
---

### Post by moment on 2005-06-03
Hello all,

I have a very strange problem (looks like a kernel or X problem). The Gnome freezes in my Ubuntu Hoary if my network is being configured by DHCP during the boot process. The mouse works but I get a standstill wallpaper. Then I have to do Alt+Ctrl+F1 and logon to my home account and ifdown my metwork and kill gdm. Then on everything works again. Is anybody experiencing the same issue and if yes how I can get around it? Thanks in advance.

Hamid

---

### Post by ola on 2005-06-03
Hi

Can you localize if the problem is network related or GDM related?

One thing you can try is to remove the line that says "auto eth0" (or eth1 or similar) in the file "/etc/network/interfaces" which should disable network setup at boot time.. I am not totaly sure it will work, but it can be worth a try..

Hope it helps

---

### Post by moment on 2005-06-03
To be honest I don't know really if the problem is with GDM or network but if I just cancel the network configuration during booting by hitting Ctrl+c then I can log on perfectly to GDM and everything is ok. The annoying thing is that although I have commented out the auto eth1 and the hotplug lines in /etc/network/interfaces I still have network configuring in the boot process (and 3 minutes waiting if not cancel it) and I have to unplug the Ethernet and disable the Wireless everytime I boot  my laptop.

I have to add that after the boot I can see the log on page of Gnome but after typing my username and password I see my harddisk working for a short while and then Gnome freezes. Mouse still works though.

---

### Post by tdjokic on 2005-06-03
[QUOTE=moment]To be honest I don't know really if the problem is with GDM or network but if I just cancel the network configuration during booting by hitting Ctrl+c then I can log on perfectly to GDM and everything is ok. The annoying thing is that although I have commented out the auto eth1 and the hotplug lines in /etc/network/interfaces I still have network configuring in the boot process (and 3 minutes waiting if not cancel it) and I have to unplug the Ethernet and disable the Wireless everytime I boot  my laptop.

I have to add that after the boot I can see the log on page of Gnome but after typing my username and password I see my harddisk working for a short while and then Gnome freezes. Mouse still works though.[/QUOTE]
 Did you try acpi=off in bootloader? Sometimes it help.

---

### Post by moment on 2005-06-04
I tried it after you said but it didn't help.

---

