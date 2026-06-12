---
title: "Audio stopped working"
date: 2006-09-27
forum: Desktop Environments
---

### Post by chrisccoulson on 2006-09-27
I've had no problems with audio up until now, and the last application to play audio on my system was Realplayer. But now, I can't get any sound suddenly. I don't even get the system sounds as GDM starts. My output of lspci | grep audio is:
```
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

```

This looks fairly normal to me.

The output of lsmod | grep snd is:

```
snd_mpu401              8968  0
snd_mpu401_uart         9792  1 snd_mpu401
snd_rawmidi            31072  1 snd_mpu401_uart
snd_seq_device         10704  1 snd_rawmidi
snd_intel8x0           37928  1
snd_ac97_codec        109820  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            58784  0
snd_mixer_oss          19968  1 snd_pcm_oss
snd_pcm               104008  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              28424  1 snd_pcm
snd                    68000  12 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              12640  1 snd
snd_page_alloc         13328  2 snd_intel8x0,snd_pcm

```

My master volume is right up. I've tried enabling and disabling software sound mixing via the Sound Preferences GUI, but it makes no difference. There haven't been any updates to my system since the sound last worked and I haven't intentionally made any changes to my system either.

The sound works fine if I boot to Windows.

I'm stuck. I'm not sure what else to check :(

---

### Post by chrisccoulson on 2006-09-27
Ok, if I run gstreamer-properties and set ALSA to the default output plugin and click test, I get 'ALSA - Advanced Linux Sound Architecture: Could not open resource for writing'. This is spat in to the terminal:
```
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open resource for writing. [gstalsasink.c(833): gst_alsasink_open (): /pipeline0/alsasink1:
Playback open error: No such file or directory]

```

Not sure if that helps or not.

---

### Post by WamBamBoozle on 2006-09-28
I have the same hardware you do. It is broken for me as well.

It broke under similarly mysterious circumstances as well. I was watching a movie -- my Ubuntu box is my multimedia machine -- and all was well. A few minutes later I go back to watch some ".mov" under totum and -- no sound.

I tried running gstreamer-properties but did not get the diagnostics mentioned. Ubuntu thinks there is nothing wrong with my sound.

I checked /dev/dsp -- it was 600. How'd that happen? Changing it to 666 doesn't seem to help.

---

### Post by WamBamBoozle on 2006-09-28
I tried re-installing the sound system as per [Comprehensive Sound Problems Solutions Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide"). This sent me down a hellish spiral of
reinstalling ubuntu-desktop and whatnot. It didn't seem to help.

I rebooted. No joy. Then I pulled up the volume control and noticed that PCM was muted. Unmuting it brought back the sound. I wonder what PCM is and whether it was muted all along.

---

### Post by chrisccoulson on 2006-09-28
Cheers for the suggestion. Unfortunately, PCM is already unmuted on mine. It's well and truly broken!

I'm reluctant to do a reinstall without first knowing what caused this. Although, if i can't fix it, thats going to be my only option.

If it's significant, the last time I used Realplayer, I had to forcefully kill it. AFAIK, the sound hasn't worked since then.

---

### Post by yargevad on 2006-09-28
Try turning the master volume and the volume on your player up all the way... I'm having basically the same issue. It looks like somehow the default sound levels got turned way down because I have to turn everything all the way up in order to hear anything.

Any idea how to fix that?

---

### Post by yargevad on 2006-09-28
> **yargevad said:**
> Try turning the master volume and the volume on your player up all the way... I'm having basically the same issue. It looks like somehow the default sound levels got turned way down because I have to turn everything all the way up in order to hear anything.

Any idea how to fix that?

Gotta love self-replies... so starting alsamixer from the command line and bumping PCM up from the low value it was at does the trick. And also doesn't affect the PCM setting in the main volume control.

---

### Post by chrisccoulson on 2006-09-28
I can't run alsamixer. I get:
```
No mixer elems found
```

I've searched and aearched the forums and I can't seem to find anything. I think my only option now is a total reinstall.:(

---

### Post by chrisccoulson on 2006-09-28
Ok, I've tried following the steps in "Getting the ALSA drivers from a *fresh* kernel" from [this]("http://www.ubuntuforums.org/showthread.php?t=205449") guide, but still no joy. Although, I seem to be able to run alsamixer now.

---

