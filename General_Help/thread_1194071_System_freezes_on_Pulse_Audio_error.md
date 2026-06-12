---
title: "System freezes on Pulse Audio error"
date: 2009-06-22
forum: General Help
---

### Post by Varro on 2009-06-22
Hi there, i got a problem with Jaunty.
First of all i'm italian, so excuse me for the bad english, then my computer freezes randomly and the error i can read when i read the log is:

```

pulseaudio[3745]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
pulseaudio[3745]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
pulseaudio[3745]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 23,00 dB to 23,00 dB which makes no sense.

```

I'm using Ubuntu 9.04 with the last officials upgrade (Pulseaudio 0.9.14-0ubuntu20).
I reported this annoying bug here ([https://bugs.launchpad.net/ubuntu/+bug/389969](https://bugs.launchpad.net/ubuntu/+bug/389969)) and in the italian ubuntu forum but nobody answer me.
I hope someone had same problem and solved it.
Thank you in advance.

---

### Post by Varro on 2009-06-25
The last system upgrade solved the problem, i can see the error in the log but the system doesn't freeze anymore

---

