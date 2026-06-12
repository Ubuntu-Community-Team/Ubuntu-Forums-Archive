---
title: "problems with sound recording (so problems with skype)"
date: 2006-03-20
forum: Desktop Environments
---

### Post by bucz on 2006-03-20
hi,
i cannot record sound from my microphone (and so i cannot talk through skype). when i want to record from the 'default' sound recorder there is only either noise and patter or an error appears:  ' ALSA device "default" had an error'.

i have set ALSA as default sound source, but when i press 'test' an error appears" 'could not create test stream alsa'. i have turned on microphone capture and set volume bar of mic, also in 'alsamixer' capture volume is set and 'mic' selected. my soundcard is ac97.

---

### Post by beercz on 2006-03-22
I have a similar problem on a laptop.

When I use sound recorder I cannot record anything through the mic.

When I use skype I cannot hear anything nor record anything.  I discovered this by calling echo123.

Sound in breezy works fine otherwise.

Any ideas anyone?

---

### Post by beauty on 2006-04-01
[QUOTE=beercz]I have a similar problem on a laptop.

When I use sound recorder I cannot record anything through the mic.

When I use skype I cannot hear anything nor record anything.  I discovered this by calling echo123.

Sound in breezy works fine otherwise.

Any ideas anyone?[/QUOTE]
After Ubuntu installs the sound drivers, you need to open up the permissions:
   sudo chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi

This command line was taken from instructions for manual ALSA install at:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx)

Now here's my problem:  I got the microphone working, but the sound is very very soft.  I tried a different microphone, though maybe of no better quality, with the same results.  I have already maxed up microphone AND "In-gain" levels in the volume control.

Any ideas?  I'm assuming a good microphone should record with no problem at at least 12 inches distance.

---

### Post by bhowell on 2006-04-03
Did you enable Mic Boost?  Go into the preferences in volume control and make sure the box is checked for Mic Boost.  Then click the +20dB Mic Boost box in the volume control Switches tab.  

Does the mic max out when you tap on it with your finger?  Some mics have very sensitive sound fields so you may need to reorient it so that it points toward your mouth or whatever.

---

### Post by beauty on 2006-04-05
Thanks for the response.  I did not have a "+20dB Mic Boost" box available.  I dug into this and got 'alsamixer' running in a shell.  alsamixer *does* have a +20dB indicator but does *not* allow me to change the blasted thing!  (I can change the other items.)

However, I found some instructions for twiddling bits, and it worked!
[http://mail.gnome.org/archives/gnomemeeting-list/2002-April/msg00180.html](http://mail.gnome.org/archives/gnomemeeting-list/2002-April/msg00180.html)

---

### Post by niels on 2006-04-06
[QUOTE=beauty]After Ubuntu installs the sound drivers, you need to open up the permissions:
   sudo chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi[/QUOTE]

I just tryed this, but got this message:
  niels@nielslaptop:~$ sudo chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi
  Password:
  chmod: kan ikke tilgå (can't reache - or something like that) '/dev/sequencer': Ingen sådan fil eller filkatalog (No such file or directory)
  chmod: kan ikke tilgå '/dev/midi': Ingen sådan fil eller filkatalog
  niels@nielslaptop:~$

What to do about it?

---

### Post by niels on 2006-04-06
[QUOTE=beauty]Thanks for the response.  I did not have a "+20dB Mic Boost" box available.[/QUOTE]

Try the options and then mark all possibilities.

---

