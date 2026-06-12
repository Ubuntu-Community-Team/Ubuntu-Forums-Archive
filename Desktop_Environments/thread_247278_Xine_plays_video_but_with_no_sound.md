---
title: "Xine plays video but with no sound"
date: 2006-08-30
forum: Desktop Environments
---

### Post by TheBishopOfSoho on 2006-08-30
Hi everyone, Im a recent windows to linux convert. I know windows inside out but decided now was the time to switch adn see what Linux was like, and so far Im loving the switch, albeit witha  couple of niggles. 

For example Im trying to play mpeg and WMV files and the video plays fine but no sound plays for them. Sound does work as I can play internet streams in other media players just fine. Now, as Ive only been using Linux for the past week, Im a bit slow on teh uptake so whats teh easiest way for me to get sound working for Xine?

Many, many thanks in advance for your help

Bish

---

### Post by TheBishopOfSoho on 2006-08-30
Actually, I should mention its actaully the gxine player Im using mostly, I have Xine and gxine installed but I prefer the gxine interface. My sound card is an SB live 5.1, VLC works fine and I can listen to all my MP3s on that but VLC wont play any WMV files (The sound seems to work but no video?)

---

### Post by razorsmile on 2006-08-31
i have a similiar problem - the only sounds I can get are from xmms.  every other engine seems broken.  now this is an odd one and has arisen from me trying to fix a previously not working xmms ;-)

I have two sound cards, output of aplay -l is as follows:


> card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


and xmms kept defaulting to the first card when it's the c-media card the speakers are plugged into.  some fiddling with alsa settings and modules seemed to get xmms working fine now (i was trying to use streamtuner to record some streams with the xmms engine, hence the need) but has buggered everything else, including sound on vids etc...

and I'm not entirely sure what I did with the alsa stuff...

is there anyway of flushing and rebuilding the sound environment from scratch or any pointers as to why the other apps aren't playing sound...i have checked as far as I can and everything seems to either be set to auto or also as the drivers and nothings muted in the alsamixer...

help :confused:

---

