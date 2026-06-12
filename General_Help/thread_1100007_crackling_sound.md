---
title: "crackling sound"
date: 2009-03-18
forum: General Help
---

### Post by dejay68 on 2009-03-18
Hi, me again :D
Can anyone explain why my sound crackles when i mute it ?

It sounds like my laptop is burning - although i know it isn't ;)

Thanks again

---

### Post by dejay68 on 2009-03-19
anyone ?

---

### Post by dejay68 on 2009-03-19
:popcorn:

---

### Post by acimmarusti on 2009-03-19
what's your audio card?

```

lspci -v | grep Multimedia

```

Do this and tell me if you hear a lady saying front left and right 5 times without problems?

```

speaker-test -c2 -ls -twav

```

---

### Post by Nano_ext3 on 2009-03-19
This can happen if you dont have a good driver configured for your sound.  Try the PulseAudio driver or the ALSA driver:

You may want to go to your settings and to the "Sound" manager in Ubuntu (System > Preferences > Sound). The ALSA driver is known to work on many occasions where the real driver fails to work. This happened to me on my desktop, which is understandable as it is choc full of custom hardware. Change each entry on the main page of the sound editor to ALSA. You can test the output by hitting the test button. Change your driver if ALSA does not work, one of the drivers in each drop down should work, but you want to keep the same driver for all if you can.

Also install alsamixer as suggested above, it will greatly help you out. Turn all levels up from alsa mixer. The command to istall alsamixer is:

"sudo apt-get install gnome-alsamixer"


Cheers!

-Nano

---

### Post by dejay68 on 2009-03-20
tried changing driver as sugested (system >preferences >sound) but i still get static/crackling sound when audio is muted .:(

---

