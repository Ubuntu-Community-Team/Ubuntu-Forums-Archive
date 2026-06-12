---
title: "Xubuntu: no sound"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Cable on 2006-09-01
I put Xubuntu on an older 500 MHz family computer.  Works amazingly except for one thing:  sound.  The computer is a HP Pavilion 8580C.  The sound card in it is a Riptide PCI Audio Controller.  OEM Vendor is Risq Modular Systems, Inc.  This is what the old OS on the computer detected it as (Win98SE *shudder*), and Knoppix detects it as this as well.  I believe it's actually an integrated card, but I'm not positive.  Xubuntu seems to think that there is no sound card.  Any way I can get sound to work without purchasing a different card?

---

### Post by Cable on 2006-09-01
Well, let me change what I originally said a bit.  I installed hal-device-manager and it does indeed see the sound card and detects it as the same thing as Win98SE and Knoppix.  So it does see it.  But, sound still does not work.  I have the volume control applet in the panel, and opening up the volcume control window and looking at the options has no device listed there to use for sound.  How can I get sound?

---

### Post by Cable on 2006-09-01
bump

---

### Post by doobit on 2006-09-01
I'll have to check this more closely when I get home to my Xubuntu box, but here's something to try:
Open a terminal and type ```
sudo alsamixer
```
Then enter your password
Use your arrow keys to go through all of the channels and make sure they are not muted (use the "m" on your keyboard to mute or unmute selected tracks) and that the main and PCM volumes are turned up.
There is also a sound applet, available by a right click on the top panel, that you can add to the panel for easier volume control.

---

