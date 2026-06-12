---
title: "Backlight doesn't working on Samsung laptop"
date: 2013-07-17
forum: Desktop Environments
---

### Post by yakudzam on 2013-07-17
Hello! I have a Samsung NP300E5Z laptop. When I was on Ubuntu 12.04, my backlight was working, but when I update my system to 13.04, brightness control was gone. On previous version I used the legendary string "acpi_backlight=vendor", but on 13.04 that trick doesn't work. How can I fix this issue???

---

### Post by Toz on 2013-07-17
Can you try the **acpi_backlight='!Windows 2012'** parameter instead?

If it doesn't work, can you post back:
```
cat /proc/cmdline
```
...so to confirm it is being applied?

---

### Post by yakudzam on 2013-07-17
> **Toz said:**
> Can you try the **acpi_backlight='!Windows 2012'** parameter instead?

If it doesn't work, can you post back:
```
cat /proc/cmdline
```
...so to confirm it is being applied?


**maxym@maxym-300E5Z:~$** *cat /proc/cmdline* 
BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=8bc3e261-0e77-4b30-8cae-807ef5bddffc ro quiet splash pcie_aspm=force acpi_osi=Linux "acpi_backlight=!Windows 2012"

---

### Post by Toz on 2013-07-17
Sorry, major brain cramp. Lets try this again.

Remove both "acpi_backlight=!Windows 2012" and "acpi_osi=Linux" and try:
```
acpi_osi='!Windows 2012'
```

---

### Post by yakudzam on 2013-07-17
BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=8bc3e261-0e77-4b30-8cae-807ef5bddffc ro quiet splash pcie_aspm=force "acpi_osi=!Windows 2012"


don't working(

---

### Post by Toz on 2013-07-17
Can you try this?

1. Remove acpi_osi='!Windows 2012' and add back "acpi_backlight=vendor"

2. Log in and try function keys and slider again.

3. If they don't work, then:
```
sudo modprobe -r samsung_laptop
```

4. Try the function keys and slider again.

5. If they don't work, log out and back in again and test again.

6. If still not working, log out, go to first tty (Ctrl+Alt+F1), log in to the text console and run:
```
sudo service lightdm restart
```

7. Log in again and test once more.

---

### Post by yakudzam on 2013-07-17
All this steps work, but only until I reboot the laptop. After next start backlight doesn't work again

---

### Post by Toz on 2013-07-17
As root, add:
```
blacklist samsung_laptop
```
...to /etc/modprobe.d/blacklist (create the file if it doesn't exist)

Reboot to test.

---

### Post by yakudzam on 2013-07-17
For now, laptop starts with max brightness, Fn-keys can only reduce brightness level and if I want to increase it - slider stops at ~30% and doesn't want to go upper.

---

### Post by Toz on 2013-07-17
Can you post back the following:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
```
lsmod | grep samsung
```
```
dmesg | grep samsung
```

---

### Post by yakudzam on 2013-07-17
**maxym@maxym-300E5Z:~$** for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
/sys/class/backlight/intel_backlight
3718
4648
/sys/class/backlight/samsung
2
8

```
**maxym@maxym-300E5Z:~$** lsmod | grep samsung
```
samsung_laptop         14532  0 
video                  19390  2 i915,samsung_laptop

```

**maxym@maxym-300E5Z:~$** dmesg | grep samsung
```
[   30.494988] samsung_laptop: enabled workaround for brightness stepping quirk
[   30.500566] samsung_laptop: detected SABI interface: SwSmi@

```

---

### Post by Toz on 2013-07-17
Hmm. blacklisting samsung_laptop didn't work. 

Can you rename /etc/modprobe.d/blacklist to /etc/modprobe.d/blacklist.conf, run:
```
sudo update-initramfs -u
```
...reboot and test again?

---

### Post by yakudzam on 2013-07-17
For now it works! Cool! Thank you!! I will save this thread to my bookmarks!

---

### Post by Toz on 2013-07-17
Great to hear. Can you mark this thread as solved using the instructions in the "How To Mark A Thread [SOLVED]" link in my signature? Thanks.

---

### Post by yakudzam on 2013-07-17
Yeah, sure! Already done this)

---

### Post by Captain NFB on 2013-07-18
Hi
I think this may be the solution to my problem- but I don't entirely understand the instructions.
I posted my own thread:

[http://ubuntuforums.org/showthread.php?t=2163522](http://ubuntuforums.org/showthread.php?t=2163522)

Thanks.

---

### Post by yakudzam on 2013-07-18
If it Samsung device - I think, it must work similar to my laptop. Try to do all steps as I did.

---

