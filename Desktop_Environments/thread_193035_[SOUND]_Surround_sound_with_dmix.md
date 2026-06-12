---
title: "[SOUND] Surround sound with dmix"
date: 2006-06-09
forum: Desktop Environments
---

### Post by brechtvb on 2006-06-09
After i installed ubuntu, and my sound works, also with multiple streams, but my sound wasn't mixed from 2.0 to 5.1.

With this .asoundrc. from a gentoo-wiki i, the sound is mixed, but dmix does not work, so while i was testing, sound from exaile and VLC don't play together.

```
pcm.!dmix {
   type plug
   slave {
       pcm surround51
       channels 6
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 6
   route_policy duplicate
}

```

Dapper Drake
My soudcard is: Creative SB Live!-24bit
my sound driver is: ca0106

Any suggestions on how to get dmix working ?

---

### Post by Sutekh on 2006-06-11
I found this .asoundrc to work better for my SB Live 24bit (CA0106) than the one you used, which seemed to skip over audio files.  I have 5.1 sound now.

> #########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

#######################################################
#This is what one could call the "factory default setting", in other
#words, it only plays the actual channels. so if you fx want to watch a
#5.1 movie, on the analog output, this is the option you want.


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}
 Also taken from the Gentoo Wiki

[Gentoo Wiki - HOWTO ALSA Complete]("http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#VIA_Envy24HT_.28ice1724.29_chip")

---

