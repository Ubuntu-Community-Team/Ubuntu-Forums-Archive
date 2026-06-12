---
title: "Sound problem on Elitegroup K7S5A"
date: 2005-07-25
forum: Desktop Environments
---

### Post by karl_kashofer on 2005-07-25
Hi !

I installed Ubuntu 5.04 on a K7S5A and can not get the onboard sound to work.

All sound related programs on the gnome panel die with various error messages.
I can not get any mixer or volume control working. vlc cant access /etc/dsp and dies with a memory access error.

This is what I find in dmesg:
```

i810: SiS 7012 found at IO 0xd400 and 0xd800, MEM 0x0000 and 0x0000, IRQ 11
i810_audio: Audio Controller supports 2 channels.
i810_audio: Defaulting to base 2 channel mode.
i810_audio: Resetting connection 0
ac97_codec: AC97 Audio codec, id: ALC38 (ALC100P)
i810_audio: only 48Khz playback available.
i810_audio: AC'97 codec 0 supports AMAP, total channels = 2

```

I have put i810_audio into /etc/modules
I also tried alsa.

Anyone know how to get that soundchip working ?
Any other info I can provide ?

Thanks,
Karl

---

### Post by karl_kashofer on 2005-07-26
Ok, adding the user to the video and audio group surely helps...
I removed all the modifications I had done from the various howtos and rely now only on the AC97 driver.

So now I have back all the mixers and get audio from all sources, but:

I can not get VLC to stream audio from my WinTV capture board.

The 878 chip should provide me directly with sound, and also the cable running from the WinTV card into the line-in of the onboard sound card definitely provides sound.

If I switch on the line-in in the volume control I can hear the sound of the TV even without running a TV app (not sure if thats good...)

Anyway, what is the parameter I have to use in VLC to get it to capture the line-in of my sound card, or the sound stream provided by the BT878 in the v4linux tab ?

I tried /dev/dsp which makes VLC crash with "memory access error" and /dev/dsp1 does not seem to provide any sound.

To hear sound from a DVD in VLC i had to kill esd, maybe this is related.

So if any of you good people could help me with getting sound into VLC that would be great,
Cheers,
Karl

---

