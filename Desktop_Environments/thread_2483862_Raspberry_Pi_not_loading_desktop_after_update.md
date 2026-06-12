---
title: "Raspberry Pi not loading desktop after update"
date: 2023-02-11
forum: Desktop Environments
---

### Post by draki on 2023-02-11
I have a Raspberry Pi 4 Model B Rev 1.5. This morning there was a security update that required a reboot and now the desktop environment won't start. I can ssh in and DMESG isn't that helpful:
```
hdmi-audio-codec hdmi-audio-codec.0.auto: ASoC: error at snd_soc_dai_startup on i2s-hifi: -19
MAI: __soc_pcm_open() failed (-19)

```

Any ideas about what might be wrong? 

I've purged and reinstalled the desktop environments

I have 4 packages held back from the update
```
The following packages have been kept back:
  gir1.2-gdkpixbuf-2.0 libgdk-pixbuf-2.0-0 libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common
```
Could it be that and I just need to wait for whatever is blocking them to be unblocked?

Any suggestions?
Thank you

---

