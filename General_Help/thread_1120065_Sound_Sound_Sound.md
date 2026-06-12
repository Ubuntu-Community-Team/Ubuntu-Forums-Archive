---
title: "Sound Sound Sound"
date: 2009-04-08
forum: General Help
---

### Post by matt101 on 2009-04-08
hi Im new to ubuntu I'm haveing a bit of a weard sound issue I have a pci soundbalster and a onboard sound that does not work this is why I use the soundblaster pci card. Anyway I go to Sound and test sound I here beeps and the test are all ok I set it to soundblaster all that good stuff but I have no sound when ubuntu starts or in any games or a VM this is the speck's Can someone help me out please I did a few diffent commands I look in the forums here. Thanks Alot

00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
00:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 01)



**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4670]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Live [SBLive! Value [CT4670]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive! Value [CT4670]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


 0 snd_emu10k1
 1 snd_via82xx
/proc/asound/modules (END)

---

### Post by Therion on 2009-04-08
Reboot your PC and enter the BIOS setup.
Disable your onboard sound, save changes and exit.

Leaving the onboard sound enabled in the BIOS when you have a PCI sound-card installed is a common mistake, but you need to fix it.

---

### Post by matt101 on 2009-04-08
> **Therion said:**
> Reboot your PC and enter the BIOS setup.
Disable your onboard sound, save changes and exit.

Leaving the onboard sound enabled in the BIOS when you have a PCI sound-card installed is a common mistake, but you need to fix it.


Thank you very much sir that just slipped right buy me I feel like an ***

---

