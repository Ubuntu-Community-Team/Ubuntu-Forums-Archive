---
title: "Sound/surround configuring/kmix"
date: 2005-04-27
forum: Desktop Environments
---

### Post by Terracotta on 2005-04-27
Hye,
My sounddrivers are working fine, I think, but I just don't seem to be able to get sound of my rear?center?mid boxes, just front left and right are working, does anyone knows how/where to change this? oh and the subwoofer isn't working either, I had this installation working in windows xp, but there I had a nice  tool to configure 5.1 or 7.1 is there something similar, all I find is kmix (or alsamixer for that matter) wich has 3d sound but no sliders for the boxes sepperatly. Is there a tool in linux to make you get sound from the subwoofer, music and movies are so much nicer with a sub.

PS, I have an onboard (yeah, junk I know) sound card via V8237, on the ASUS A8V motherboard, and alsa has recognised and configured the card out of the box... (a bit)

---

### Post by getaceres on 2005-04-27
Make sure kde is using ALSA and not OSS.
To make that go to the control center, and look in the system sound propierties in the hardware tab.
Now, if it's using ALSA you should see in kmix the LFE slider (subwofer) and the sorround slider (the rear speakers).

---

### Post by Terracotta on 2005-04-27
KDE is using ALSA, everything should work, I just don't get any sound, even my frontboxes don't work anymore, :s, don't know what I've done wrong this time.

---

### Post by thecrimsonking on 2005-04-27
With Logitech z640 speakers I have 5.1 surround sound with these settings in Kmix:
but I also have a sound card.

Also, sometimes you have to switch the jacks around for the speakers to work correctly in linux.
My jacks have to be in completely different plugins when I am gaming in Windows to get 5.1 sound.

---

### Post by Terracotta on 2005-04-28
I though onboard sound, is a soundcard too :-), and euhm, well, I just don't get sound out of any of the jacks.

---

### Post by jr06compmaster on 2006-12-18
I too have the Z640 speaker system, but I also have an Audigy LS soundcard.  I have sound from the front left/right speakers and the center if I hit the matrix button on the center speaker.  Using the volume control, I can manipulate the front speakers using the Analog Front from the menu, but Analog Rear does not control the rear speakers.  Can anyone help me?  I don't use kmix.

---

