---
title: "How do I choose audio device for gMFSK?"
date: 2009-06-14
forum: General Help
---

### Post by simonz on 2009-06-14
I am running Linux Mint 7 (Ubuntu 9.04 derivative) and using my Ham radio programs are the last hold out for running Windoze.  I just downloaded gMFSK (program for digital mode for ham radios) and the first question it asks me is which /dev is my sound card connected to.  They give several choices such as:  /dev/dsp /dev/dsp0 and /dev/dsp1 but none seem to work.

My question is, which /dev is my sound card connected to?

thanks,
simonz


Found the answer.  The /dev/dsp is the correct device.  I had to mess around with the audio setting the VolumeControl in the GnomePanel to have the sound connected to the Recording stream.

---

### Post by ml41782 on 2009-08-08
The following Linux commands may help to show the device identification..
After connecting - sudo tail -f /var/log/messages
or look at dev folder before and after connecting ( ls /dev/dsp* )

---

