---
title: "Installing Ubuntu with MS Keyboard"
date: 2007-03-25
forum: Desktop Environments
---

### Post by OzGordy on 2007-03-25
I am trying to install ubuntu on a computer with a MS keyboard and mouse. I think its a wireless / usb model. i.e. the mosue and keyboard have no wires but link via wireless / IR to a pod which is linked via a usb cable to the computer.

The issue is whjen my PC reboots and then launches the Ubuntu CD to do the install then the keyboard does not work thus preventing me selecting the safe install. The default install does not like my defult grahics card / screen combination so all i get is a blank screen after the initial load :(

What can i do to get over this keyboard problem.. I am assuming this is also going to be an issue when i install GRUB and i want to swap between Ubuntu and XP as i need a dual boot machine.. 

Thanks in advance

Gordy

---

### Post by kfazz on 2007-03-26
you could try going into your bios and enabling "usb keyboard/mouse support" or "legacy usb support" or "dos usb support" depending what it's called in your bios. or use a usb->ps2 adaptor for the wireless dongle.

---

### Post by OzGordy on 2007-03-26
Thanks matey.. I am trying that but having a problem getting into the Bios.. will have to use my old keyboard to try and intterupt the boot process...

thanks again

---

### Post by OzGordy on 2007-04-02
Nope.. still not working... update thebios on my DFI NF4 mother board to enable usb support..(or something like that) and when i reboot the dumb thing still doesnt work.. I have to use 2 keyboards at present to get the machien to boot and allow me to move between XP and Ubuntu.. ill keep search but it seems a weried problem and other people have pointed it out but never replied to say they have solved it..

Gordy

---

### Post by ronocdh on 2007-04-02
I have a similar problem. I'm on a laptop (second gen Macbook Pro), and rarely can I use the laptop's keyboard to select XP from GRUB. Oddly enough, I have an Apple bluetooth keyboard that I sometimes CAN use to select different options on the GRUB screen! I'd say that works about 25% of the time (when it's nearby, i.e. connected). Pretty cool that the keyboard talks to the computer at such a deep level that it's understood by a bootloader/live CD.

I have another friend who just installed Debian, and he can no longer can into XP, because he can't EVER change the selection on the bootloader. He has tried multiple keyboards to no avail; he'll have to use the XP installer CD and repair the MBR, I think.

All in all, I haven't ever seen anyone post a solution, either. So it goes. :confused: :confused:

---

### Post by kellemes on 2007-04-02
These problems most often have to do with the mboard not initializing the device. Often this can be fixed bu updating BIOS or check the "USB legacy support" in BIOS. In my case it never was possible, my usb keyboard (SAITEK II) seams to be "non standard" and simply is not supported by my mboard, the USB-PS/2 adapter is not working either..
And so I have 2 keyboards hooked, one PS/2 to get into BIOS and walk the bootmenu and my Saitek comes in from then on..

This is not a software/OS related issue!

---

