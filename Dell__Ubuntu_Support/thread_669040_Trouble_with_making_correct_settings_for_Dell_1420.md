---
title: "Trouble with making correct settings for Dell 1420 sound in alsa"
date: 2008-01-16
forum: Dell  Ubuntu Support
---

### Post by rkj90266 on 2008-01-16
I recently purchased a Dell 1420 laptop and then upgraded to 7.10 gutsy.  I'm hopeing someone can help me understand how the mixer settings in alsamixer relate to and control the physical devices, because so far the only recording source I've been able to enable is the internal mic.  I cannot get the external mic to respond but there are so many possible combinations of controls perhaps I just haven't hit upon the right one.

It appears there are 3 inputs available - the internal mic, the external mic jack, and the middle jack which apparently is configured as a line in jack by default.  I know that if I enable "Line in as output" the middle jack becomes a second headphone port, so I guess that means it is an input when that option is not enabled.

On the "Capture" tab in alsamixerI see 7 controls - 
Capture
Capture 1
Capture 2
Digital
Mux
Mux1
Mux2
Logically it would seem that the Capture, Capture 1 and Capture 2 controls would correspond to those 3 physical interfaces, and if I enabled input on all 3 I would get input from all 3 simultaneously.  But in fact I have not been able to get any but the first one to do anything, and then only the internal mic.  And I have no idea what the muxes are for, what do they mux, and how should they be set.

On the "Playback" tab there are "Input Source", "Input Source 1" and "Input Source 2" controls that can be set to values "Mic", "Front Mic" or "Line" so it would seem logical that these switch the physical jacks/devices to the "Capture" controls but I have not been able to get that to work either.  There is another control labeled "Digital" that can be set to values "Digital" or "Analog Inputs" and the only setting that seems to work is if I set this to "Digital" and then only the internal mic works.

Finally, there are volume controls on the "Playback" tab that correspond to 5.1 surround channels, but there is only a stereo output jack.  Is there some way to actually get surround sound out? Or are these just useless controls?

Any help in understanding this will be much appreciated.

---

