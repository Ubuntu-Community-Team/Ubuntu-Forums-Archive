---
title: "Switching between soundcards (ALSA)"
date: 2005-08-18
forum: Desktop Environments
---

### Post by mrbrdo on 2005-08-18
Hello

I have set up my sound as the HOWTO for two sound cards says. However, i can't get it to switch cards unless i do a restart.
I've made this script:
```

#!/bin/sh
SNDSTATUS=`/bin/cat /etc/asound.conf | grep "hw:0,0"`
cd /home/mrbrdo/gnome_scripts/soundswitcher
if [ "$SNDSTATUS" = "" ]
then
  gksudo "/bin/cp asound.conf.1 /etc/asound.conf"
else
  gksudo "/bin/cp asound.conf.2 /etc/asound.conf"
fi
gksudo "/etc/init.d/alsa restart"

```

The asound.conf.2 is the same as asound.conf.1, only pcm "hw:0,0" is changed to pcm "hw:1,0".
The file is:
```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

```
(BTW: is the pcm.card0 section necessary? it was on that HOWTO but it seems irelevant)

After i change the file (i also tried in gedit), i do /etc/init.d/alsa restart . Now, if i have XMMS running, i stop it before doing that, and i press play after alsa is restarted, and the right card is used. But if i stop it again and do anything which causes GNOME to output a sound (like open a directory), and click play again, then the other card is used again (in XMMS too). Seems GNOME keeps reseting the default soundcard somehow (it's still correct in asound.conf, if i restart alsa again without doing anything else, XMMS again plays on the right card until i do anything in GNOME).

So: Which is the correct way to change the current output card without restarting?

Thanks

---

