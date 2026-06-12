---
title: "All webbrowsers crash"
date: 2009-02-23
forum: General Help
---

### Post by Nikoros on 2009-02-23
Hello!

I am experiencing a very weird problem. All of my webbrowsers I have installed crash. And it doesn't matter which website I enter: flash or no flash, javascript or no javascript. I tried to switch them both off, and that didn't help. They often crash when I hit a link, but other times they crash when I right-click on a picture or on some text. I don't know why, but I can't browse normally for more than 30 sec- 5 min. And that is really annoying. :(

I have an AMD Athlon Xp 1900+ with 512mb RAM and 1,6Ghz. I guess it's not because of performance. I have Ubuntu 8.04.2 installed. But I experienced this in Kubuntu 8.04 and 8.10 as well.

The webbrowsers are:
Opera --> crashes really often, in 30 to 90 seconds.
Firefox --> I never use this one any more, can't browse for 5 seconds.
Epiphany --> as bad as firefox
Konqueror --> the best I have, usually 5 minutes to that KDE-crash message.

Please can someone help?

Thanks a lot!

---

### Post by trash.eighty on 2009-02-23
Are web browsers the only you have problems with?  When you boot, hit ESC at the GRUB screen and call up memtest86.  If that doesn't run clear, you may have bad RAM.

---

### Post by Nikoros on 2009-02-23
Well, actually not. I've got update-manager crashing often when updating, so tomorrow I'll run the memtest. Thanks!

---

### Post by Nikoros on 2009-02-28
Hello,

Well, a few days ago I ran the memtest86+, no errors in RAM. But it still got crashing. So I've tried other Linux-distributions, thinking that would be the cause. Well, it wasn't. OpenSUSE, Fedora, Kubuntu and even PuppyLinux crashed. Not only webbrowsers, but a lot of other programs. So I've reinstalled Ubuntu, got the updates and it all started again: webbrowsers, Audacity, OpenOffice, they all crash, without any reason. Sometimes when I simply move the mouse or hit a key. And sometimes Ubuntu crashes along. Could that be another hardware issue? :confused:

---

### Post by Nikoros on 2009-03-03
What else could it be? Some software piece I've installed wrong?

---

### Post by Hadraniel on 2009-03-03
> **Nikoros said:**
> Sometimes when I simply move the mouse or hit a key. And sometimes Ubuntu crashes along. Could that be another hardware issue? :confused:

This is most likely a hardware issue. Any hints in the system logfiles?
Check dmesg, /var/log/messages,syslog etc...

Remove all USB and pci cards and check if the instability persists. Run Memtest86 over night, for 12 or more hours. Fallback your BIOS settings to the least agressive, safe settings. Check for IRQ-sharing issues.

If your computer is unstable with just Graphics and memory enabled, trash your board and/or CPU.

---

### Post by Nikoros on 2009-04-12
I'm sorry for my very late reply, but the problems were indeed my RAM and surprisingly enough my almost-new hard drive. Anyway, I've got an older computer now, the system is slower, but I can do much more with this old thing because it doesn't crash all the time as the other did. Everybody, thanks a lot! :D

---

