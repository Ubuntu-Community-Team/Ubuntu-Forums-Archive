---
title: "More problems with alsa"
date: 2005-07-14
forum: Desktop Environments
---

### Post by Pixel on 2005-07-14
I tried reading every howto and thread about alsa here, and none seem to be able to help me.

I have a Sound Blast Audigy LS, I can get sound out of anything. Heres my asound.conf.

I'm using libesd-alsa0.

```

asound.conf

# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}


```

---

### Post by Mooie on 2006-08-21
have you installed your cards drivers via synaptic? thats what I had to do on my old SB card.  to download the file you might have to have multiverse repos enabled...  i'm not really sure.   I found it in a search for alsa, but you could probably search "sound blaster alsa" and find it much faster.  It has some weird name, so make sure not to miss it. I hope it helps :D

---

### Post by Mooie on 2006-08-21
just realised this post was from a year ago... hope it helps sombody else...

---

