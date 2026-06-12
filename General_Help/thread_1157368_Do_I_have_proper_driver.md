---
title: "Do I have proper driver?"
date: 2009-05-12
forum: General Help
---

### Post by Barmaleychik on 2009-05-12
Hello,

I installed 9.04 on ASUS a8n vn csm motherboard which has video, sound and LAN on the board. Everything was kind of working, but video resolution was set wrong. I found that I need to install nVidia drivers and then my monitor was recognized and I got my 1600x1200 screen resolution.

My sound and LAN are working but I am not sure that I have good drivers. How can I check if I do have the best drivers for this motherboard?

Is it possible that I need some additional drivers of which I am not aware?

Thank you in advance

Barmaley

---

### Post by bobnutfield on 2009-05-12
"Drivers" for hardware devices are modules that are built into the kernel.  Ubuntu has excellent hardware recognition and will usually load the correct module for the hardware it identifies.  If the hardware is working, you have the correct module loaded.

Graphics drivers are a little different.  While the correct "open source" driver will be loaded, you can get better performance with a proprietary driver sometimes.  This is the case with your nVidia on-board chipset.

---

### Post by nacho32 on 2009-05-12
if it is working they are correct and I'm sure the latest. Run update manager it will detect if their are a newer release

---

### Post by Skripka on 2009-05-12
For on-board audio the ALSA drivers are fine (which should be default), the LAN drivers should be fine too.

Linux comes with generic enough drivers to get these to work fine out of the box usually.  And odds are ASUS does not make Linux drivers anyway.  Don't worry ;)

---

### Post by Barmaleychik on 2009-05-12
Thank you guys for your fast responses.It was re-assuring

---

