---
title: "Sounds Problems related or not?"
date: 2006-01-20
forum: Desktop Environments
---

### Post by Sef on 2006-01-20
I have these two sound problems that might be related.

A) Downloaded pysol and the sound, but get this error message:

    -) Internal Error.  Please report this bug:  exceptions.AssertionError

        1) How can fix this that it plays the music?


B) When I go to listen to the radio over xmms, I get this message.  I click on it and reclick on xmms and it works fine.  (Sometimes I have to click on it 3 times to get it to play.)

    -) Please check that:  Your soundcard is configured properly.  You have the correct output plugin selected.  No other program is blocking the soundcard.

    1) How can I fix this, so I don't get that message?

C) Are they related or just two different problems entirely.

D) Default soundcard:  VIA 82C686A/B rev50

---

### Post by FarEast on 2006-01-23
I am not sure, but there is an option 'enable' that may have something
to do with the issue.

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx)

Give a try:
Describe 'options snd-via82xx enable=1' in /etc/modprobe.d/sound .
Execute 'sudo update modules' and restart the system.

---

