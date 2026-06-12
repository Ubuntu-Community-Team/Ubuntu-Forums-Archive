---
title: "A minimal system - With Wireless!"
date: 2009-01-14
forum: General Help
---

### Post by blazemore on 2009-01-14
I'm interested in starting from a base system and working my way up, compiling or installing everything from X to Firefox.

However, I only have a wireless connection, which uses WPA encryption.
Is there a way I can install a base system (With the Alternate CD), and connect to my wireless network to install the packages I need?
A base Ubuntu system would contain the kernel, the package manager, a compiler (maybe) and not much else!

---

### Post by mikewhatever on 2009-01-14
This guide is just for you.
[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)

---

### Post by HunterThomson on 2009-01-14
> **blazemore said:**
> I'm interested in starting from a base system and working my way up, compiling or installing everything from X to Firefox.

However, I only have a wireless connection, which uses WPA encryption.
Is there a way I can install a base system (With the Alternate CD), and connect to my wireless network to install the packages I need?
A base Ubuntu system would contain the kernel, the package manager, a compiler (maybe) and not much else!

Well, You can install a linux sys on a new parttion wile in a running linux OS on a difrent partition. 

Or, you could download the repo miror then install packages you need from that.

You really sound like your looking for Arch Linux.

---

### Post by adamlau on 2009-01-14
What I do is first take note of dependant packages while I compile what I need on a standard install on a secondary drive. Then perform a minimal install, mount the secondary drive, install required dependencies and make install accordingly. Very clean and simple enough. You install a minimal system via the minimal CD (which really isn't all that minimal). Prepare to spend hours and hours on your box and yes, you can do what you are asking :) .

---

### Post by kerry_s on 2009-01-14
i agree you should give arch a go, i did my install by wireless.

just make sure you select dev, that will give you a submenu, there it has the wireless tools, drivers/firmware. then when it gets to the part where it says the ttys are available, switch tyy and then manually bring it up.

example:
iwconfig <tells you what device
ifconfig ? up <replace ? with the device, aka: wlan0,ath0,eth1, whatever
dhcpcd ?

read up here:
[http://wiki.archlinux.org/index.php/Wireless_Setup](http://wiki.archlinux.org/index.php/Wireless_Setup)

---

### Post by Andreas1 on 2009-01-14
> **mikewhatever said:**
> This guide is just for you.
[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)

this looks really like something i could use.
i am not so expert though, and there are a few general questions, maybe someone can explain to me:
i like ubuntu because: it detects my graphic chipset (intel 915) & display, lets me choose my usb-soundcard as default (internal is broken), wireless... and all other laptop hardware components. what will it be like if i follow that instruction? to what extent will my system know which drivers to install? what will i have to do to make the sound work?...and so on, my concern is the laptop hardware.

i am considering this because ubuntu is just getting too heavy on my centrino laptop. i also considered switching to xfce, but i really like gnome and basicall what i want would be a lighter system still using gnome. is that possible?

---

### Post by blazemore on 2009-01-14
Does anyone know how to configure my wireless from the commandline?
I'd like to use the text-based WPA passphrase, rather than the whole hex key if possible!

---

### Post by kerry_s on 2009-01-14
> **blazemore said:**
> Does anyone know how to configure my wireless from the commandline?
I'd like to use the text-based WPA passphrase, rather than the whole hex key if possible!

[http://wiki.archlinux.org/index.php/WPA_Supplicant](http://wiki.archlinux.org/index.php/WPA_Supplicant)

---

