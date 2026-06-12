---
title: "NO KEYBOARD 2650 notebook dell"
date: 2010-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hatewindows on 2010-10-17
I was told to set ACPI=off should do the trick--However where do i go to make this change? I'm able to use a USB keyboard for the time being.. Thanks for any help!! MARK  Have a good night........:confused:

---

### Post by hatewindows on 2010-10-17
I'm using 10.10

---

### Post by orthello on 2010-10-18
Press 'e' in the GRUB boot menu and add acpi=off
Or do a normal startup and edit /boot/grub/menu.lst using a usb mouse+keyboard





I have accidentally managed to get everything to work by changing  power management settings, using a USB mouse and reboot. This turned out  to be a permanent fix/workaround. As far as I can remember the laptop  still powers down by itself when shutting down.

I'll investigate this further in a few days. Then I will also come up  with the exact changes in power management. Because it was by accident, I  don't exactly know any more what I did. *blush*

---

### Post by RR-GraphixGuy on 2010-10-21
I had the exact same problem on my Inspiron 2650. One thing I noticed is that keypresses during boot (not sure if specific keys or not) seemed to enable the keyboard. Almost as though something had to be in the keyboard buffer for it to pass a test to be enabled... something like that....

I applied the fix noted above (acpi=off) however with a clean install of 10.10, you get GRUB 2, which does not use menu.lst anymore. Instead, a file called grub.cfg is generated from various scripts. It is a big no-no to directly edit grub.cfg, since any updates or changes by the system will cause the file to be rewritten anyway. 

I found the best place to put the "acpi=off" command was in **/etc/grub.d/10_linux** on (on mine) line 77 after "recordfail" within the** linuxentry()** function. 

```
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
    recordfail
    acpi=off
EOF
```Incidentally, auto reboot still works as expected. Shut down, however, still requires one last push of the power button to actually shut the power off.

Edit- Remember to **sudo update-grub** afterwards to rebuild grub.cfg. Reboot, disconnect your USB keyboard, and see if that works.

If there is a more appropriate way to do this, I'm all ears.

-Mike

---

