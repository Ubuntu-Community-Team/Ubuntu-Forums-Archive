---
title: "Ubuntu 8.10 freezes on shutdown"
date: 2009-04-05
forum: General Help
---

### Post by GodAmoungMen on 2009-04-05
When i try to shut down my machine I, I wind up with a blinking cursor, and the last line before the cursor is

[187.473179] ---[ end trace band782b0b4ae0d0d]

Any one know how to fix this?

---

### Post by spiderbatdad on 2009-04-05
possibly a problem with boot up. Or some other app you have installed...a band width monitor?

Perhaps dmesg will suggest you boot with the option acpi=force. Do you know how to read dmesg and apply this option?
Boot options are explained here and quite easy to try:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by GodAmoungMen on 2009-04-05
I'm pretty new, so I'm not too sure of everything. What is the dmesg command? I don't think I have a bandwidth monitor

---

### Post by spiderbatdad on 2009-04-05
```
dmesg > ~/Desktop/dmesg.txt
```If you want right click that file and select create an archive. You can upload the archive with the manage attachment tool below. I can help you decipher the file...possibly

---

### Post by GodAmoungMen on 2009-04-05
Here it is. Thanks for the help. I am just amazed how helpful everyone is on this forum. I wish I had the know how to return the favours.

---

### Post by spiderbatdad on 2009-04-05
well, the right options can be tricky to apply. Your kernel suggests:
```
acpi_use_timer_override
hpet=force
```
Maybe just acpi=force will be best.

You can experiment a bit and read dmesg after boot. I think your best result is going to come from using:
```
lapic pci=routeirq hpet=force
```You can try boot options from the grub options screen by pressing 'e' move to the OS you want to boot, if it isnt already selected. Move to the line starting with 'kernel', press 'e' again, then go to the end of the line and delete quiet splash, type in your options, hit enter, and press 'b.' When you are satisfied your system is booting and shutting down properly, edit the kernel line in /boot/grub.menu.lst as described in the wiki.

---

### Post by GodAmoungMen on 2009-04-06
The problem actually seems to be fixed now. When I first updated my system, I figured that would take care of it, but it didn't. I did another update yesterday and it works fine now. Thanks for your time though!

---

