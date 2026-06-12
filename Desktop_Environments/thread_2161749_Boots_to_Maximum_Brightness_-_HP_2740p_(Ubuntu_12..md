---
title: "Boots to Maximum Brightness - HP 2740p (Ubuntu 12.04 64-bit)"
date: 2013-07-11
forum: Desktop Environments
---

### Post by entropy1 on 2013-07-11
Toz,

My machine always boots to maximum brightness, but I wanted about half.  I was able to modify your instructions (in this thread: [http://ubuntuforums.org/showthread.php?t=2161442&p=12726967]("http://ubuntuforums.org/showthread.php?t=2161442&p=12726967")) to set the brightness to half on boot.  Thank you!

P.S.  I noticed that even though I get the brightness I want, when I go to System Settings > Brightness, the slider is all the way to one side...

---

### Post by Toz on 2013-07-11
> **entropy1 said:**
> Toz,

My machine always boots to maximum brightness, but I wanted about half.  I was able to modify your instructions to set the brightness to half on boot.  Thank you!

P.S.  I noticed that even though I get the brightness I want, when I go to System Settings > Brightness, the slider is all the way to one side...

Does your brightness slider actually change the brightness?

What is the make and model of your computer and what version of *buntu are you using?
Also, can you post back the results of these commands?
```
cat /proc/cmdline
```
```
sudo lspic -vnn | grep -A12 VGA
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

---

### Post by entropy1 on 2013-07-11
> **Toz said:**
> Does your brightness slider actually change the brightness?

What is the make and model of your computer and what version of *buntu are you using?
Also, can you post back the results of these commands?
```
cat /proc/cmdline
```
```
sudo lspic -vnn | grep -A12 VGA
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

1) Yes, moving the slider adjusts the brightness as you would expect.

2) HP 2740p running Ubuntu 12.04 64-bit

3) Commands:

```
$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-36-generic root=UUID=f9d0f81d-97f8-4393-a94c-2318d63e10da ro quiet splash vt.handoff=7

$ sudo lspci -vnn | grep -A12 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device [103c:7007]
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5050 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915
	Kernel modules: i915

$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
24
24
/sys/class/backlight/intel_backlight
145
648
```

The 145 is what I put in the rc.local file.

---

### Post by Toz on 2013-07-11
I moved this over to its own thread.

---

### Post by Toz on 2013-07-11
Before we try any manual adjustments, can we try something that might fix the whole issue? 

Can you try the **acpi_backlight=vendor** kernel parameter? Here is how:

1. Edit the grub config file:
```
gksu gedit /etc/default/grub
```

2. Change the line that reads:
> GRUB_CMDLINE_LINUX=""
...to
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

3. Save the file.

4. Run:
```
sudo update-grub
```

5. Reboot and test.

---

### Post by entropy1 on 2013-07-11
Toz,

The combination of ```
echo 324 > /sys/class/backlight/intel_backlight/brightness
``` in the /etc/rc.local file and the changing of /etc/default/grub as you suggested above makes my system boot to half brightness and set the slider half way too.  Thank you!

---

