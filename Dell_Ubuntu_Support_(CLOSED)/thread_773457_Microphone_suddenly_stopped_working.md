---
title: "Microphone suddenly stopped working"
date: 2008-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MedellinManDem on 2008-04-28
As the title says

I'm using Ubuntu Hardy on a Dell VOstro 1500.

---

### Post by Luke has no name on 2008-04-29
I have an ALC882 realtek audio, and my output is perfect. My mic, however, does not work. This is critical for me.

---

### Post by LiquidIQ on 2008-04-29
> **MedellinManDem said:**
> As the title says

I'm using Ubuntu Hardy on a Dell VOstro 1500.

I'm assuming you checked your mixer settings. Then checked your Sound Preferences panel.

If I remember right, there's also a BIOS option to turn on/off the Mic. Strange that it just stopped working though.

---

### Post by maccam94 on 2008-04-29
You need to open Edit -> Preferences in the mixer applet, and add the capture, mux, Digital Input Source, and Input Source options. Turn up capture and mux, and set the first Input Source from Mic to Front Mic. You can also switch between using an external or the internal mic by changing Digital Input Source from Analog Inputs to Digital Mic 1.

---

