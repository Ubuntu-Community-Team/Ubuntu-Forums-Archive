---
title: "odd behavior with left click on left edge of window"
date: 2017-04-29
forum: Desktop Environments
---

### Post by rawlins02 on 2017-04-29
Running 14.04 on a Lenovo laptop. When laptop is connected to a Dell external monitor, a left click on the left edge (as when resizing) of a window (browser, terminal) that is displayed on the monitor will send the window shooting over to the laptop display. The window also resizes to tall and narrow. Occasionally the window will display distorted. This does not happen when laptop is not connected to the external monitor. Is this expected behavior? If no, how might I disable it or otherwise diagnose a problem?

---

### Post by Autodave on 2017-04-29
Are you mirroring the display? Or, is one display supposed to be showing something different?

What video card are you using and what driver? Where did you obtain the driver?

---

### Post by rawlins02 on 2017-04-30
> **Autodave said:**
> Are you mirroring the display? Or, is one display supposed to be showing something different?

What video card are you using and what driver? Where did you obtain the driver?


No I'm not mirroring. The window manager automatically sets the displays side-by-side when I plug in the VGA connection. It functions like one big desktop, with ability to move windows back and forth between the displays. A typical setup. 

Video card is NVIDIA GeForce GT 730M. I'm using X.Org X server - Nouveau display driver. I believe the driver is part of the 14.04 install.

---

### Post by Autodave on 2017-04-30
That card came out about the beginning of 2013. I am thinking that you are using an out-dated driver.....if you are using any at all.  Have you installed any drivers for the card?  If not, go to Settings -> Software & Updates -> Additional Drivers. Let Linux search for a driver. You will probably get a choice of several: use the one that is recommended.

---

### Post by rawlins02 on 2017-05-01
> **Autodave said:**
> That card came out about the beginning of 2013. I am thinking that you are using an out-dated driver.....if you are using any at all.  Have you installed any drivers for the card?  If not, go to Settings -> Software & Updates -> Additional Drivers. Let Linux search for a driver. You will probably get a choice of several: use the one that is recommended.


Under Software and Updates -> Additional Drivers there are three options. No where does the word "recommended" appear. The other two options, besides the open source driver I'm using, are two NVIDIA proprietary drivers; version 375.39 and version 340.102. My understanding is that it's best to use the open source driver. Hoping someone can confirm that using a proprietary driver is a good choice here.

---

### Post by rawlins02 on 2017-05-01
Today I experienced more odd behavior when attempting to present a slide show using LibreOffice Impress. Connected to an external display, both mirrored and not mirrored, the presentation (after clicking start from first slide) spanned across the two displays. I could not get a full screen on the external monitor, and I'd done so many times before. Cursor occasionally disappearing after connecting and disconnecting from an external monitor has been an ongoing issue for some time. 

Seems that OS updates are not interacting well with video card and the open source driver.  Prefer not to have to install a newer version of Ubuntu.

Edit: Mouse disappears when I move it off of the external display and over to the laptop display. So odd behavior with left edge of a window AND the mouse is confined to when laptop is connected to an external monitor.

---

### Post by rawlins02 on 2017-05-01
I tried the latest proprietary NVIDIA driver. Could not get it to display in dual screen mode. Switched back to Nouveau driver. Now everything, left side of windows and mouse, are all working fine. It's like there was a reset of things going haywire. I'm going to mark this tread solved and hope for the best.

---

