---
title: "Microphone Crackling [Ubuntu 20.04]"
date: 2022-02-28
forum: Desktop Environments
---

### Post by agiesea on 2022-02-28
Microphone is crackling in all programs where I can play back the audio including usage of arecord. I have tried multiple solutions, adding echo cancellation to pulseaudio configuration, setting tsched to 0, adjusting the volume of the mic. So far nothing has helped and I'm looking for any guidance anyone can offer.

---

### Post by mIk3_08 on 2022-03-01
> **agiesea said:**
> Microphone is crackling in all programs where I can play back the audio including usage of arecord. I have tried multiple solutions, adding echo cancellation to pulseaudio configuration, setting tsched to 0, adjusting the volume of the mic. So far nothing has helped and I'm looking for any guidance anyone can offer. Try installing ALSA (Advanced Linux Sound Architecture) in your system and configure it there once installed completely. Just try to check if your chipset/sound card supported by ALSA (Advanced Linux Sound Architecture). Once ALSA (Advanced Linux Sound Architecture) installed completely test it in your Linux Ubuntu Operating System and play the configuration in it to fit your needs. Actually, maybe your system has already have an ALSA (Advanced Linux Sound Architecture) driver but maybe it needs additional configuration using ALSA (Advanced Linux Sound Architecture). Good Luck and Cheers

---

### Post by ActionParsnip on 2022-03-01
What is the output of
```

wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh

```

---

