---
title: "Bootchart - What am i doing wrong?"
date: 2009-02-16
forum: General Help
---

### Post by Andysan on 2009-02-16
Hi all,

I installed Bootchart through Synaptic along with all of the dependencies that it required. I have created an entry in menu.lst as follows:

title Bootchart Logging 8.10, kernel 2.6.28-sickboy-kuki
uuid 42f7456a-34a4-46e1-a6cc-0620e2ffbfd5
kernel /boot/vmlinuz-2.6.28-sickboy-kuki root=UUID=42f7456a-34a4-46e1-a6cc-0620e2ffbfd5 ro quiet splash elevator=noop init=/sbin/bootchartd
initrd /boot/initrd.img-2.6.28-sickboy-kuki
quiet

When i reboot and select this kernel through GRUB, i don't see a Bootchart in the expected directory. Entering "bootchart" at the terminal yields a "command not found" response.

Do I need to do anything else for Bootchart to work please, or am I looking in the wrong place for the image (/var/log/bootchart)?

Thank you.

---

### Post by Old_Grey_Wolf on 2009-02-16
You don't need to add Bootchart to the menu.lst. All you do is boot normally then look in /var/log/bootchart for a new chart. Every time you boot it creates a new file. Unless you uninstall Bootchart it will continue using more disk space for each new file it creates.

---

### Post by Andysan on 2009-02-17
Hi Old_Gray_Wolf,

I may attempt a reinstall of BootChart then as it certainly doesnt create them images, either before or after amending menu.lst.  

Thought it must have just been me, cheers!

---

### Post by Old_Grey_Wolf on 2009-02-17
> **Andysan said:**
> Hi Old_Gray_Wolf,

I may attempt a reinstall of BootChart then as it certainly doesnt create them images, either before or after amending menu.lst.  

Thought it must have just been me, cheers!

All I do to get Bootchart to work is enter the following in the terminal:
```
sudo apt-get install bootchart
```

---

