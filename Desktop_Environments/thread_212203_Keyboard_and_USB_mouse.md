---
title: "Keyboard and USB mouse"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Hoffmann on 2006-07-09
Hello:

I decided to change my PS/2 mouse to a USB one. However, amazingly, now the keyboard doesn't work (it isn't recognized anymore). If I put the old PS/2 mouse back, the keyboard is recognized by the system again.
When I am on the Windows XP partition, all works fine!

Should I change anything on Ubuntu configuration? What should I do to have both my NEW USB mouse and the keyboard recognized?

Thanks.

---

### Post by saphil on 2006-07-09
Wow, this is an interesting mystery.  My 5.10 installation often "lost" the USB mouse after being inactive for a while.  Unplugging the mouse and reinstall brought it back.  It hasn't happened in the 6.06 upgrade.

When I was trying to use a USB keyboard on my dual-boot machine, I couldn't choose the non-default OS choice.  The USB drivers were not loaded at boot-up.  These are probably not similar issues at all, but at first blush they seemed to be similar to your ps/2 keyboard disappearing.
I found this on a search:
[http://www.whacked.net/ldl/faq/faq](http://www.whacked.net/ldl/faq/faq)
```

5.1. Using an external USB pointer device in X
        Most people want both the stick/touchpad working full-time, 
        and to be able to plug in an external USB mouse whenever they 
        want and have it work without having to retool XF86Config each 
        time.  I have successfully done this with the following
        sections in my XF86Config-4:
            Section "InputDevice"
                # This section controls the stick/touchpad
                Identifier    "Mouse0"
                Driver        "mouse"
                Option        "Device"    "/dev/psaux"
                Option        "Protocol"    "PS/2"
                Option        "Emulate3Buttons"    "on"
            EndSection

            Section "InputDevice"
                # This section controls an optional USB mouse
                Identifier    "USBMouse"
                Driver        "mouse"
                Option        "Device"    "/dev/pointer"
                Option        "Name"    "AutoDetected"
                Option        "Protocol"    "IMPS/2"
                Option        "Vendor"    "AutoDetected"
                Option        "ZAxisMapping"    "4 5"
            EndSection

        Next, modify the "ServerLayout" section to look something like:
            Section "ServerLayout"
                Identifier    "MyXLayout"
                Screen    "Screen0"
                InputDevice    "Mouse0"    "CorePointer"
                InputDevice    "USBMouse"    "SendCoreEvents"
                InputDevice    "Keyboard0"    "CoreKeyboard"
            EndSection
        This tells the Xserver to always look for Mouse0, and barf if 
        it's not there (which hopefully will never happen), and if the 
        USBMouse is detected on /dev/pointer, then have it send core 
        signals to the Xserver, but don't barf if it can't find it.

        Last note, make sure you make a symbolic link from 
        /dev/input/mice (this is on the 2.4.x kernel) to /dev/pointer
``` 
This looks like it might be a way to specifically denote your ps/2 keyboard and USB mouse.  If you are having a boot-phase issue, like I seem to be having on my dual-boot machine, then you are not in luck..  It appears that grub cannot see any USB device, from what I am finding..

---

### Post by blue_shift on 2006-07-09
I have a dell USB keyboard and I can select options at the grub menu, type commands and so on. Surely therefore grub can recognise this? Perhaps a version problem? However, I don't have any PS/2 peripherals.

---

### Post by Hoffmann on 2006-07-09
> **saphil said:**
> Wow, this is an interesting mystery.  My 5.10 installation often "lost" the USB mouse after being inactive for a while.  Unplugging the mouse and reinstall brought it back.  It hasn't happened in the 6.06 upgrade.

When I was trying to use a USB keyboard on my dual-boot machine, I couldn't choose the non-default OS choice.  The USB drivers were not loaded at boot-up.  These are probably not similar issues at all, but at first blush they seemed to be similar to your ps/2 keyboard disappearing.
I found this on a search:
[http://www.whacked.net/ldl/faq/faq](http://www.whacked.net/ldl/faq/faq)
```

5.1. Using an external USB pointer device in X
        Most people want both the stick/touchpad working full-time, 
        and to be able to plug in an external USB mouse whenever they 
        want and have it work without having to retool XF86Config each 
        time.  I have successfully done this with the following
        sections in my XF86Config-4:
            Section "InputDevice"
                # This section controls the stick/touchpad
                Identifier    "Mouse0"
                Driver        "mouse"
                Option        "Device"    "/dev/psaux"
                Option        "Protocol"    "PS/2"
                Option        "Emulate3Buttons"    "on"
            EndSection

            Section "InputDevice"
                # This section controls an optional USB mouse
                Identifier    "USBMouse"
                Driver        "mouse"
                Option        "Device"    "/dev/pointer"
                Option        "Name"    "AutoDetected"
                Option        "Protocol"    "IMPS/2"
                Option        "Vendor"    "AutoDetected"
                Option        "ZAxisMapping"    "4 5"
            EndSection

        Next, modify the "ServerLayout" section to look something like:
            Section "ServerLayout"
                Identifier    "MyXLayout"
                Screen    "Screen0"
                InputDevice    "Mouse0"    "CorePointer"
                InputDevice    "USBMouse"    "SendCoreEvents"
                InputDevice    "Keyboard0"    "CoreKeyboard"
            EndSection
        This tells the Xserver to always look for Mouse0, and barf if 
        it's not there (which hopefully will never happen), and if the 
        USBMouse is detected on /dev/pointer, then have it send core 
        signals to the Xserver, but don't barf if it can't find it.

        Last note, make sure you make a symbolic link from 
        /dev/input/mice (this is on the 2.4.x kernel) to /dev/pointer
``` 
This looks like it might be a way to specifically denote your ps/2 keyboard and USB mouse.  If you are having a boot-phase issue, like I seem to be having on my dual-boot machine, then you are not in luck..  It appears that grub cannot see any USB device, from what I am finding..


Thanks for reply.
My machine is a desktop, instead of a laptop.
In my posting I forgot to mention that my keyboard is a PS/2 one. So, when I have both PS/2 keyboard and PS/2 mouse, all is ok. However, the problem starts when I have both PS/2 keyboard and USB mouse. In this last scenario, the keyboard doesn't work at all. So, the USB mouse has been recognized on Dapper (my problem is with the PS/2 KEYBOARD, when the USB mouse is plugged in). No problem on Windows.
Any hint?

---

### Post by saphil on 2006-07-09
:-) No hint! except it sounds like the mouse & keyboard might be in eachother's port on the back of the machine, and there is only confusion on the Ubu side when the mouse is out.  I have seen (once) such a hardware confusion in Win95 when there was no mouse at all.. (keyboard didn't work in the designated mouse ps/2 port) but that can't entirely make sense in your situation.

---

### Post by Hoffmann on 2006-07-09
> **saphil said:**
> :-) No hint! except it sounds like the mouse & keyboard might be in eachother's port on the back of the machine, and there is only confusion on the Ubu side when the mouse is out.  I have seen (once) such a hardware confusion in Win95 when there was no mouse at all.. (keyboard didn't work in the designated mouse ps/2 port) but that can't entirely make sense in your situation.

Defenitely, that is not my case. I mean, the mouse and the keyboard are in their respective (correct) ports on the back of my machine.
Thanks, anyway.

---

