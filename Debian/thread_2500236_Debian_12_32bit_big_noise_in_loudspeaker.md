---
title: "Debian 12 32bit: big noise in loudspeaker"
date: 2024-08-27
forum: Debian
---

### Post by maketopsite on 2024-08-27
Happens after sound initialization during boot. Persists until closing DE during reboot.

It resembles as if there is no signal to loudspeaker and you turn volume to max.

Values in pavucontrol and alsamixer are as usual - in the "middle". Other sound play normally.

```
echo 0 > /sys/module/snd_hda_intel/parameters/power_save 
``` did not help.


```
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
    Subsystem: Intel Corporation NM10/ICH7 Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at 903c0000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

```

```
Aug 08 15:22:21 maketopsite systemd[1]: systemd-rfkill.service: Deactivated successfully.
Aug 08 15:22:20 maketopsite systemd[1]: Reached target sound.target - Sound Card.
Aug 08 15:22:20 maketopsite systemd[1]: Finished alsa-restore.service - Save/Restore Sound Card State.
Aug 08 15:22:20 maketopsite systemd[1]: Started rtkit-daemon.service - RealtimeKit Scheduling Policy Service.
```

Any idea please ?

---

### Post by currentshaft on 2024-08-27
How is the speaker connected?

---

### Post by maketopsite on 2024-09-22
> **currentshaft said:**
> How is the speaker connected?

[https://en.wikipedia.org/wiki/Phone_connector_(audio)](https://en.wikipedia.org/wiki/Phone_connector_(audio))

(green color)

---

