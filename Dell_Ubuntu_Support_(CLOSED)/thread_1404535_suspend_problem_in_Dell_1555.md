---
title: "suspend problem in Dell 1555"
date: 2010-02-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sushilsc on 2010-02-11
Hi,

 I recently purchased Dell 1555 and installed ubuntu 9.10 (32 bit) on it. Now when I close the lid it do not go in suspended mode.

  If i suspend it from the shoutdwon, restart menu then it does and again pressing the power buttion comes up nicely.

 Could some one help how to make it work when I close the lid of the system. (I have given this option in the power management window.)


Thanks a lot.
with best regards,
sushil

---

### Post by sushilsc on 2010-02-11
Anyone knows how to solve this issue or can provide the Xorg.config file??

Thanks and with best,
sushil

---

### Post by maximus.bobba on 2010-02-19
Well i had weird problem with the lid too. When i close the lid and open it up again, it just hangs.... 

Anyone know how to solve this?

---

### Post by garok89 on 2010-02-21
you could try disabling apic (yes that is apic, not acpi)in grub
this also fixes the eject button, the backlight 'switch' and the battery not detected issues

```
sudo gedit /etc/default/grub
```
then edit this line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```
then update grub (i dont know if you need to use update-grub2 or update-grub so do both)
```
sudo update-grub && sudo update-grub2
```
reboot and all shall be good

---

