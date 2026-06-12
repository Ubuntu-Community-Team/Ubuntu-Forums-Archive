---
title: "aoss introduces delay in wine"
date: 2007-06-04
forum: Gaming &amp; Leisure
---

### Post by Klin'Targ on 2007-06-04
I have been trying to get WoW to run with Vent/TS for a while now. My current status is:
WoW + OSS: works fine.
WoW + ALSA: ~500ms delay.
WoW + OSS + aoss: ~500ms delay. The following message is output on the console when using this method:
```
err:wave:wodOpen fragment size set failed, size is now 4096
Your Open Sound System driver did not let us configure small enough sound fragments.
This may cause delays and other problems in audio playback with certain applications.
```

I have tried all combinations I can think of with the hardware emulation options in winecfg, but nothing seems to make any difference.

I am using a Sigmatel 9221 based Intel HDA audio onboard chipset (Intel D975XBX motherboard). ALSA works fine outside of wine, including mixing. I have esound disabled.

---

