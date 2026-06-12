---
title: "WoW - One day sound, next day, no sound."
date: 2007-02-21
forum: Gaming &amp; Leisure
---

### Post by daemonfly on 2007-02-21
Having a problem lately with absolutely no sound in WoW here & there. One day, it will work fine, next day (after a reboot, or cold boot) sound no longer works.

I screw around with tons of audio settings and eventually get it to work, sometimes, but never knowing what I really did.

winecfg is properly set to have only the OSS driver checked, per the install guide.

Proper entries are also in the WoW config file.
config.wtf
```
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
```

Sound for everything else works fine.

---

### Post by dtruesdale on 2007-02-21
try aplay -l and see if it throws an error up on the console?

---

### Post by daemonfly on 2007-02-21
```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SBLive! Platinum [CT4760P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SBLive! Platinum [CT4760P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SBLive! Platinum [CT4760P]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by dtruesdale on 2007-02-21
You have another app running hogging OSS. OSS doesn't like to share, I run wow in Cedega using Alsa. Tried the OSS and it says it's working but no sound comes out.

---

### Post by daemonfly on 2007-02-21
hrm, nothing else should be using OSS.  I'll have to take a look.

---

### Post by Sammi on 2007-02-21
run this command:
```
sudo apt-get install alsa-oss
```to install alsa-oss, which is a little app that tunnels oss programs through alsa, making them work more or less like regular alsa apps.

To use it you just run wow.exe with the "aoss" command in front, something like this
```
aoss wine wow.exe
```If you've made an icon launcher for WoW, then you just need to edit the launcher in the same way(add aoss in front).

---

### Post by pwolfe on 2007-02-21
I frequently have to kill the artsd process to be able to get sound going in WoW.

---

### Post by daemonfly on 2007-02-22
No artsd running.


Alsa-oss worked, which I thought it might, but I read that it was a performance hit and wanted to try to get OSS working by itself "perfectly" like it did for months now, until just recently.

---

### Post by Sammi on 2007-02-22
I like to have music playing in Amarok, while palying WoW. That's why I use alsa-oss, otherwise Amarok would be choked from using sound by OSS(WoW).

---

