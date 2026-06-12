---
title: "All sound stopped with pulse updates-ubuntu 9.10"
date: 2009-12-06
forum: Desktop Environments
---

### Post by Lori700698 on 2009-12-06
Yesterday my darling 13 year old ran his updates I saw the word pulse and before I could say wait he hit install and sound is now gone.  It has been 3 weeks since I installed 9.10 for him and the sound worked fine up until that moment.  I found some interesting errors in my logs, anybody have any ideas???

```
Dec  6 14:58:32 Dan-Ubuntu os-prober: debug:
running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Dec  6 14:58:32 Dan-Ubuntu 50mounted-tests: debug: /dev/sda2 type not
recognised; skipping
Dec  6 14:58:32 Dan-Ubuntu os-prober: debug: os detected
by /usr/lib/os-probes/50mounted-tests
Dec  6 14:58:32 Dan-Ubuntu os-prober: debug:
running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Dec  6 14:58:32 Dan-Ubuntu 50mounted-tests: debug: /dev/sda5 is a swap
partition; skipping
Dec  6 14:58:32 Dan-Ubuntu os-prober: debug: os detected
by /usr/lib/os-probes/50mounted-tests
Dec  6 15:11:57 Dan-Ubuntu pulseaudio[1502]: ratelimit.c: 113 events
suppressed
Dec  6 15:11:57 Dan-Ubuntu pulseaudio[1502]: alsa-sink.c: ALSA woke us
up to write new data to the device, but there was actually nothing to
write!
Dec  6 15:11:57 Dan-Ubuntu pulseaudio[1502]: alsa-sink.c: Most likely
this is a bug in the ALSA driver 'snd_hda_intel'. Please report this
issue to the ALSA developers.
Dec  6 15:11:57 Dan-Ubuntu pulseaudio[1502]: alsa-sink.c: We were woken
up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0
or another value < min_avail.
Dec  6 15:13:44 Dan-Ubuntu python: io/hpmud/pp.c 627: unable to read
device-id ret=-1
Dec  6 15:48:47 Dan-Ubuntu pulseaudio[1502]: ratelimit.c: 91 events
suppressed
Dec  6 15:58:45 Dan-Ubuntu pulseaudio[1502]: ratelimit.c: 104 events
suppressed
Dec  6 16:01:18 Dan-Ubuntu pulseaudio[1502]: ratelimit.c: 100 events
suppressed
Dec  6 16:03:47 Dan-Ubuntu pulseaudio[1527]: ratelimit.c: 113 events
suppressed
Dec  6 16:06:13 Dan-Ubuntu pulseaudio[1527]: alsa-sink.c: ALSA woke us
up to write new data to the device, but there was actually nothing to
write!
Dec  6 16:06:13 Dan-Ubuntu pulseaudio[1527]: alsa-sink.c: Most likely
this is a bug in the ALSA driver 'snd_hda_intel'. Please report this
issue to the ALSA developers.
Dec  6 16:06:13 Dan-Ubuntu pulseaudio[1527]: alsa-sink.c: We were woken
up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0
or another value < min_avail.
Dec  6 17:50:49 Dan-Ubuntu pulseaudio[1527]: ratelimit.c: 117 events
suppressed
Dec  6 17:51:21 Dan-Ubuntu pulseaudio[1527]: ratelimit.c: 108 events
suppressed
Dec  6 17:54:48 Dan-Ubuntu pulseaudio[1527]: ratelimit.c: 95 events
suppressed
Dec  6 20:01:19 Dan-Ubuntu python: io/hpmud/pp.c 627: unable to read
device-id ret=-1
Dec  6 21:14:26 Dan-Ubuntu pulseaudio[1488]: ratelimit.c: 120 events
suppressed

```

Thanks for looking & helping!  I'm VERY pleased with the Ath5k support in 9.10, my older son still has 8.04 and the driver needs rebuilt every kernel update, I've been through the sound issues with pulse on 8.04, so yea I did look at the basics and everything appears in place.  I'm stumped and I have to look to see what exactly updated, maybe I can remove it.

---

### Post by Lori700698 on 2009-12-06
Never mind, seemed to be my fault not the update.  I removed all the packages I installed...just not sure which one caused the issue.  I will have to re-install one at a time and test to see which one cause the failure.

---

