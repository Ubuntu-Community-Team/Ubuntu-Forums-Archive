---
title: "Unable to enter password on wake from suspend"
date: 2023-06-26
forum: Desktop Environments
---

### Post by peter-a on 2023-06-26
Ubuntu 23.04, Linux 6.2.0-23-generic

For a few weeks I have had a persistent problem which is that when I wake my PC from suspend, the login prompt appears but I cannot enter the password. Mouse works fine, no characters appear when I type.

I have to click the icon to switch users, and since I am the only user the login screen then reappears and I can log in normally. I can also switch to a different TTY and back again.

I then discovered, by playing with the screensaver/lock settings in dconf-editor, that this is the same problem that I get randomly whilst using my PC which is that for no reason that I can identify, Ubuntu acts as if my keyboard's Control key is stuck down. Unplugging the keyboard has no effect, the remedy is to press the shift then the control key. Accessibility features are all off.

When the PC wakes from suspend, it is in this 'control stuck' state so when I type my password I'm actually typing control characters. By pressing shift then control I can then login normally.

I have seen similar problems on older versions of Ubuntu with a fix to add various i8042 options to the grub boot line, I have tried all of these with no effect (i8042.nomux i8042.noaux i8042.dumbkbd=1 atkbd.reset i8042.reset).

Un/replugging the keyboard has no effect.

This happens on both Wayland and X11.

Power options are set to balanced, screen blank 15 mins, automatic suspend on. This happens whether the PC suspends automatically or manually.

dmesg shows system entering S3 sleep and waking with no obvious errors.

Following a solution from another similar problem I tried a resume script which resets all the USB ports with:

    eval "echo 0 > $USB" 2>/dev/null 
    eval "echo 1 > $USB" 2>/dev/null

I can see the ports resetting in dmesg but again, no effect.

I can't see anything relevant in syslog.

In syslog I can see Xorg adding the keyboard and other USB devices.

I'm fairly sure, therefore, that this is not a hardware problem but a gnome login problem of some kind.

What else can I try?

---

