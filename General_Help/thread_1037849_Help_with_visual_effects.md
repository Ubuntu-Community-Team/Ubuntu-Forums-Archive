---
title: "Help with visual effects"
date: 2009-01-12
forum: General Help
---

### Post by french_do182 on 2009-01-12
I have Windows Vista Premium Home and I have just installed Ubuntu 8.10

I want to enable the visual effects but here is the problem: I open system/preferences/appearance and goto the visual effects tab, I click on either normal or extra and a window pops up which sais"Enable driver FGLRX graphics driver" which i click enable and it doesnt seem to install and then i get a message "desktop effects could not be enabled"

I know my GFX card is fully capable to do this so what have i done wrong, please help me

Thanks Ryan

---

### Post by cros13 on 2009-01-12
1. Launch the “Restricted Devices Manager” program from the menu System &#8594; Administration &#8594; Restricted Devices Manager

2. Enable the “ATI accelerated graphics driver” driver

3. Reboot

Simple as that.

---

### Post by french_do182 on 2009-01-12
Thank you very much, ill give you a reply if it works :)

---

### Post by french_do182 on 2009-01-12
There is no restricted devices?????????????

---

### Post by cros13 on 2009-01-12
It is part of the basic install and should be there.

[IMG]http://www.ubuntugeek.com/images/nv/1.png[/IMG]

---

### Post by french_do182 on 2009-01-12
Its not there :( damn, I have the latest build of ubuntu just downloaded

---

### Post by cros13 on 2009-01-12
OK, Let's take another approach.

Go to Applications -> Accessories -> Terminal

Run the command:
> sudo apt-get install xorg-driver-fglrx

Enter your password and hit Y when asked.

Reboot.

---

### Post by french_do182 on 2009-01-12
That didnt work, oh well

I think ill have to get the updates to get the device manager

Thanks alot for your help

Appreciated

---

### Post by cros13 on 2009-01-12
Whups, Forgot some stuff *shame*.

Sorry, I'm not an ATI user. I thought that the software package did this automatically.  :(

Edit the /etc/X11/xorg.conf file. With Terminal type in:

> sudo gedit /etc/X11/xorg.conf

Find the line labeled “Driver” in the “Device” section. It should currently say something like Driver “radeon” or Driver “vesa”. Change this to:

Driver "fglrx"

Save

Reboot

---

