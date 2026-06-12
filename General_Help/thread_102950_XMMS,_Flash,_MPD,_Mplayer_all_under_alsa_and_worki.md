---
title: "XMMS, Flash, MPD, Mplayer all under alsa and working"
date: 2005-12-13
forum: General Help
---

### Post by bsantos on 2005-12-13
In case it helps someone:

My board is a DFI LanParty based on the nf2 chip.

As stated in the topic I have everything working with alsa dmix.

My /etc/asound.conf is:

```
pcm.!default {
type plug
slave.pcm "dmixer"
}
pcm.dsp0 {
type plug
slave.pcm "dmixer"
}
pcm.dmixer {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 666
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
type hw
card 0
}

```

I don't use esd anywhere, so my /etc/esound/esd.conf is:
```

[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-as 5

```

I use alsa-oss for firefox, so my /etc/mozilla-firefox/mozilla-firefoxrc is:

```

# which /dev/dsp wrapper to use
FIREFOX_DSP="aoss"

```

As for mpd my /etc/mpd.conf is:
```

playlist_directory "<insert yours here>"
music_directory "<insert yours here>"
port "6600"
log_file "/var/log/mpd/mpd.log"
error_file "/var/log/mpd/errors.log"
# optional, but HIGHLY RECOMMENDED
db_file "/var/lib/mpd/mpddb"
user "mpd"
# optional, but recommended
state_file "/var/lib/mpd/state"
mixer_type "alsa"
mixer_device "default"
mixer_control "PCM"
ao_driver "alsa09"
ao_driver_options "dev=default"

```

My /etc/libao.conf is:
```

default_driver=alsa09 

```

Also define ```
ao=alsa
``` in /etc/mplayer/mplayer.conf and /etc/mplayerplug-in.conf :)

Any other issues should be covered in previous posts regarding this matter, so this is just an addon to those, and should be taken as an it works for me kind of post. Maybe it works for someone else, that's why I'm posting it.

Cheers.

---

### Post by anil_robo on 2005-12-14
Thanks for posting this. Have you tried sound "recording" as well? I can't get it to work!

---

### Post by ubDed on 2007-09-13
thanks, it helps a lot.
Now at last flash and mpd works together without crashes

---

