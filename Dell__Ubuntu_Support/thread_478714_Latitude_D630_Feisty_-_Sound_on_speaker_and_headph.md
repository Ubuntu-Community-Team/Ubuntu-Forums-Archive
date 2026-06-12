---
title: "Latitude D630 Feisty - Sound on speaker and headphone at same time!"
date: 2007-06-19
forum: Dell  Ubuntu Support
---

### Post by apel_2804 on 2007-06-19
If I plug in an headphone the sound is played on both speaker and headphone. If I start the notebook with plugged in headphone, sound comes only from headphones - if unplugged no sound hear. Any ideas?

---

### Post by apel_2804 on 2007-06-20
*bump*

---

### Post by apel_2804 on 2007-06-20
really no ideas??

---

### Post by redrun on 2007-06-23
I don't have an answer, but I'm having the same issue with the Inspiron 1505n.  :(

---

### Post by afffffff on 2007-06-26
Same here with toshiba satellite a135, still looking for a way to solve this :(

---

### Post by apel_2804 on 2007-06-26
what sound card and chipset is installed in your satelite a135?

---

### Post by cnshzj007 on 2007-06-29
I have the same problem with D630 in Ubuntu7.10.

---

### Post by afffffff on 2007-07-02
in lspci i get this:

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

in the volume control I get 2 devices:

HDA ATI SB (alsa mixer)
Realtek ALC861-VD (oss mixer)

---

### Post by geppz on 2007-09-06
I have D830 with Gutsy and have the same problem. You can make the computer re-sense the headphones (i.e. detect whether they are inserted or not) by removing the module snd_hda_intel and modprobing it back in. You have to shut down kmix and the other applications using sound in order to be able to remove the module. Finally restart the sound applications. This nice and comfortable (ironic) procedure also restores sound after suspending/hybernating the laptop.

Have you found a way to use an external microphone? Only the embedded microphone works for me, whatever I do.

---

