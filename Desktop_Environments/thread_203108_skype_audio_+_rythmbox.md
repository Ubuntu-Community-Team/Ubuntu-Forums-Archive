---
title: "skype audio + rythmbox"
date: 2006-06-24
forum: Desktop Environments
---

### Post by galileon on 2006-06-24
hello everyone,
I am using dapper and trying to get skype to talk and listen to music at the same time...

i have tried a few hacks from this forum and elsewhere, but none seems to work, and most of them mentioned hoary, so i thought maybe there's a different one for dapper?

i have tried the ones changing asoundrc, etc and got 2 wav files playig simultaneously,[http://forum.skype.com/viewtopic.php?t=48195](http://forum.skype.com/viewtopic.php?t=48195)
but when i do aoss skype and run rythmbox, skype pretends a call is under way, but i hear nothing (i hear only the ringing, then nothing)
same thing with the skype_dsp_hijacker


and running skype directly says the usual "problem with dsp etc"

anyone can help please? thanks a lot!!

ps: sorry i cant use wengo or others, coz ive a lot of friends who hold on tightly to skype

---

### Post by Roner on 2006-06-26
Hi, I am just starting to work with Skype, but I think you may want to try the solution to the OSS problem I posted in regard to VMPlayer.  You can find it here:
[http://www.ubuntuforums.org/showthread.php?t=182304](http://www.ubuntuforums.org/showthread.php?t=182304)

Just substitute "skype" for every "vmplayer" you see there.

Let me know if it helps!

---

### Post by galileon on 2006-09-01
hello,
im awfully sorry for not replying, it was very impolite of me, but i actually thought i'd get an email when there was an update, and i was really busy and i also found a workaround and forgot about the whole business, sorry again...

i'm currently using the workaround from Lorenzo Colitti, which goes as thus:

gedit ./.asoundrc, and paste the following code into it, and do ALSA_OSS_PCM_DEVICE="skype" aoss /path/to/skype


 # .asoundrc to use skype at the same time as other audio apps like xmms
#
# Successfully tested on an IBM x40 with i810_audio using Linux 2.6.15 and
# Debian unstable with skype 1.2.0.18-API. No sound daemons (asound, esd, etc.)
# running. However, YMMV.
#
# For background, see:
#
# [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1228](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1228)
# [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1224](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1224)
#
# Usage:
# 1. cp .asoundrc ~
# 2. ALSA_OSS_PCM_DEVICE="skype" aoss /path/to/skype
#
# (C) 2006-06-03 Lorenzo Colitti - [http://www.colitti.com/lorenzo/](http://www.colitti.com/lorenzo/)
# Licensed under the GPLv2 or later

pcm.skype {
   type asym
   playback.pcm "skypeout"
   capture.pcm "skypein"
}

pcm.skypein {
   # Convert from 8-bit unsigned mono (default format set by aoss when
   # /dev/dsp is opened) to 16-bit signed stereo (expected by dsnoop)
   #
   # We can't just use a "plug" plugin because although the open will
   # succeed, the buffer sizes will be wrong and we'll hear no sound at
   # all.
   type route
   slave {
      pcm "skypedsnoop"
      format S16_LE
   }
   ttable {
      0 {0 0.5}
      1 {0 0.5}
   }
}

pcm.skypeout {
   # Just pass this on to the system dmixer
   type plug
   slave {
      pcm "dmixer"
   }
}

pcm.skypedsnoop {
   type dsnoop
   ipc_key 1133
   slave {
      # "Magic" buffer values to get skype audio to work
      # If these are not set, opening /dev/dsp succeeds but no sound
      # will be heard. According to the alsa developers this is due
      # to skype abusing the OSS API.
      pcm "hw:0,0"
      period_size 256
      periods 16
      buffer_size 16384
   }
   bindings {
      0 0
   }
}

---

