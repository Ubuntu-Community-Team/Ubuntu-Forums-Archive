---
title: "Set brightness with setpci in xfce"
date: 2012-07-07
forum: Desktop Environments
---

### Post by LonelyStar on 2012-07-07
Hi,

I have xubuntu installed on a Asus EEE R052C.
The brightness control does not work.
But what I can do is:

    sudo setpci -s 00:02.0 f4.b=80

In the console. Ok, but tedious. Can I somehow automate this so that I have an easy control over brightness (preferable the stander xfce brightness panel plugin)?

Thanks!
Nathan

---

### Post by Toz on 2012-07-07
The first thing to try would be to get the brightness keys on your keyboard to work. Have you tried the **acpi_backlight=vendor** kernel parameter? Here is how:
1. Edit the grub file:
```
sudo leafpad /etc/default/grub
```

2. Change the line that reads:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

3. Save the file.

4. Update the boot loader:
```
sudo update-grub
```

5. Reboot your computer and try again to see if the brightness keys work.


If not, I have a script that can automate the brightness changing, but it will need to be modified to your setup. Can you run the following command and post back the results:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; done
```
^^This command will report back your backlight interfaces and their current values.

---

### Post by Merrattic on 2012-07-07
You can also use xrandr to adjust screen brightness:
```
xrandr --screen VGA1 --brightness 100
```

---

### Post by detronator on 2013-03-20
Same problem here on asus notebook..
Update to the grub didn't worked out :/


Result of the command is 


/sys/class/backlight/intel_backlight
4296
1728

---

### Post by Toz on 2013-03-20
> **detronator said:**
> Same problem here on asus notebook..
Update to the grub didn't worked out :/


Result of the command is 


/sys/class/backlight/intel_backlight
4296
1728

Can you provide more info about your system (specifically the model number)?

Also:
1. What video card(s) do you have:
```
sudo lspci -vnn | grep -A12 VGA
```

2. The results of the following command _after_ you've tried the **acpi_backlight=vendor** kernel parameter:
```
cat /proc/cmdline
```

---

### Post by detronator on 2013-03-20
sudo lspci -vnn | grep -A12 VGA
Result: 
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:14f7]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915



cat /proc/cmdline

Result:

BOOT_IMAGE=/boot/vmlinuz-3.5.0-26-generic root=UUID=ce5ed486-4b35-4670-8cfa-cef698edf40f ro acpi_backlight=vendor quiet splash vt.handoff=7



Laptop model is : ASUS X501A, running xubuntu 64bit. CPU is [COLOR=#444444][FONT=Tahoma]Intel Celeron B830 1.80GHz, VGA is [/FONT][/COLOR][COLOR=#444444][FONT=Tahoma]Intel	 HD Graphics 2000 with 1696MB shared memory[/FONT][/COLOR]

---

### Post by Toz on 2013-03-20
Can you give the following kernel parameters a try instead (remove acpi_backlight). Try them individually: 
- **acpi_osi=**
- **acpi_osi=Linux acpi_backlight=vendor**

When you've booted with each of these kernel parameters:
1. Post back the results of:
```
cat /proc/cmdline
```

2. Post back your dmesg log:
```
pastebinit /var/log/dmesg
```
...and paste back the link that is generated.

---

### Post by detronator on 2013-03-21
Ok we have huge success :) Brightness buttons started working like they should! Thanks very much for the help.

I tried both possible solutions and the first one (GRUB_CMDLINE_LINUX="acpi_osi=") did the job. For testing purposes I tried the other one as well but with no success. Here are both logs, again - for testing purposes : 


1) with [COLOR=#008000]GRUB_CMDLINE_LINUX="acpi_osi="[/COLOR] (winner!) 

**cat /proc/cmdline : **


BOOT_IMAGE=/boot/vmlinuz-3.5.0-26-generic root=UUID=ce5ed486-4b35-4670-8cfa-cef698edf40f ro acpi_osi= quiet splash vt.handoff=7


**pastebinit /var/log/dmesg : **


[http://paste.ubuntu.com/5633901/](http://paste.ubuntu.com/5633901/)




2) with [COLOR=#008000]GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"[/COLOR]


**cat /proc/cmdline : **


BOOT_IMAGE=/boot/vmlinuz-3.5.0-26-generic root=UUID=ce5ed486-4b35-4670-8cfa-cef698edf40f ro acpi_osi=Linux acpi_backlight=vendor quiet splash vt.handoff=7


**pastebinit /var/log/dmesg : **


[http://paste.ubuntu.com/5633903/](http://paste.ubuntu.com/5633903/)


PS: After I saw that my brightness control slider on the panel was resetting the brightness whenever i click on it, I deinstalled the whole xfce power manager and this fixed an old issue with the brightness resetting on every restart;

---

