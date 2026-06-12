---
title: "[HOW TO] Dell 1555 and many others"
date: 2010-02-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by garok89 on 2010-02-21
Many people seem to have issues with certain features of most Dell laptops. Personally I run the Studio 1555 and I know that straight out of the box a few things do not work.
With many Dells, battery info and certain extra function buttons do not like to work, in the case of the 1555; F1-F5, eject button, power button (occasionally) and the backlight 'switch'.

you need to disable apic (yes that is apic, not acpi)in grub

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
then update grub (i am not sure if you need to use update-grub2 or update-grub so do both)
```
sudo update-grub && sudo update-grub2
```
reboot and all shall be good hopefully


as for any issues with the graphics and wireless card not being detected by some peoples installs, persevere (or force the install)

for graphics, i did this
```
sudo apt-get install fglrx-amdcccle fglrx-kernel-source fglrx-modaliases
```
reboot and then enable via System>Administration>Hardware Drivers (may require second reboot)

for the wireless card (plug in via ethernet ofcourse)
```
sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
```
reboot and then enable via System>Administration>Hardware Drivers

or you could try this method suggested by borncrusader
> **borncrusader said:**
> I would recommend using envyng by Alberto Milone for installing the ATI drivers. This works like a charm.

You can enable the partner and backport repositories and using

```
sudo apt-get install envyng-core
```

to install the package and use

```
envyng -t
```

to install the drivers.

---

### Post by borncrusader on 2010-02-22
I would recommend using envyng by Alberto Milone for installing the ATI drivers. This works like a charm.

You can enable the partner and backport repositories and using

```
sudo apt-get install envyng-core
```

to install the package and use

```
envyng -t
```

to install the drivers.

---

### Post by garok89 on 2010-02-22
i will add that to the post
thanks
i havnt actually seen that method before

---

### Post by garok89 on 2010-02-25
bump

---

