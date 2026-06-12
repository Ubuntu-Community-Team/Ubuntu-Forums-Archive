---
title: "Sound problems"
date: 2006-04-12
forum: Desktop Environments
---

### Post by Aimo on 2006-04-12
Hi all...

This may be an old problem, but i cant seem to find the solution although it was close...
I have recently installed Ubuntu on my laptop and the only problem i'm having is that there is no sound.  My sound card is the one on the mainboard (Intel 915PM/MXM) which ubuntu has recognised as "Intel ICH6".
I have tried to change the sound server from Esound to Polyoaudio but with no luck. and then i have tried to change sink and the source in the "multimedia systems selector"... But there has been no luck at all...
Hope to see if you can help

- Aimo -

---

### Post by apjone on 2006-04-12
In system > preferances > sound ensure that 'Enable sound server at startup' is checked and your sound card is selected.
In system > preferances > multimedia system selector try 'ALSA', 'ESD' AND 'OSF'

---

### Post by Aimo on 2006-04-13
Done that... and still no sound...

---

### Post by Ramses de Norre on 2006-04-13
Is your sound card listed in system > preferences > sound > default sound card?
Type alsamixer in terminal and check the settings so no volume is muted.

---

