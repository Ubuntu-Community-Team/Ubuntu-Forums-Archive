---
title: "No sound when running applications"
date: 2005-10-24
forum: Desktop Environments
---

### Post by i-x on 2005-10-24
Hello,

Please help me.


I used to have sound in KDE, then I messed around with alsamixer to switch the speakers off, because I wanted to use my headphones.

After that I have no sound when I run applications like VLC-gtk. If I load XFCE4 desktop I'll get sound but not in KDE.

If I hit the Test Sound button in Kcontrol I'll here the test sound.


Anyone got any bright ideas about this?
Maybe there is a config file I could erase etc.?


Thank you,
i-x

---

### Post by red_plague on 2005-10-24
2 things:

1. Go to the control center, under sound system, search for( and check) "duplex" mode, (something with duplex)
check if you have sound, if not:
2. start alsamixer again and enable what you need, then close alsamixer and do: alsactl store
check for sound, if you have sound:
then go in /home/your_account/.kde/Autostart
and create a text file in which you put:
#!/bin/sh
alsactl restore

ok, now right-click on it, and select the "is executable" check mark.

if you still don't have sound you could try to do: lsmod and see if your sound card module is listed there. if it isn't: sudo modprobe yyy, where yyy is yout sound module. (I'm assuming thet your instalation isn't dammaged, ofcourse.)

---

