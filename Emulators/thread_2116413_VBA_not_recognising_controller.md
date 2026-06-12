---
title: "VBA not recognising controller"
date: 2013-02-15
forum: Emulators
---

### Post by DiabolicalClaptrap on 2013-02-15
OS: Ubuntu 12.04 x86-64

I'm running v 1.8.0.dfsg-0.1 of VBA (not VBA express, installed via synaptic) and I'm noticing that my wired xbox 360 controller (USB) isn't recognised and that no button works in joypad config. To troubleshoot, I went through the follwoing steps:

[LIST]
[*]Googled. I found one thread linking to Ubuntu's page on 360 drivers. But you'll see below that that isn't necessary.
[*]Used command 'dmesg' from terminal. The controller IS in the list. Input here:
[   28.141402] input: Microsoft X-Box 360 pad as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input14
[*]Closed VBA, unplugged controller then plugged controller back in and ran VBA.
[*]Tested controller with desmume. The controller is picked up and all buttons work properly/can be assigned.
[*]Rebooted Ubuntu with controller unplugged, and plugged it back in after log in.
[/LIST]
I can't seem to figure this out. Has anyone experienced a similar issue or am I missing something?

Edit: Tried with mednafen, since its gba/gbc/gb engine is based on VBA. My Controller fully works there. Only issue is I'm unable to enable RTC (real-time clock) which I need. Compiling from source produces* a "error: *** OpenGL header file not found!* " dependency error. Furthermore, I'm unable to implement any fixes as my version (0.8.D.3) is dated. Searching synaptic yields 0 results, too (. I'm running an Intel HD video card, if that helps.

Suggestions for VBA or mednafen are welcome. By god, one of these damn emulators will work. =p

---

