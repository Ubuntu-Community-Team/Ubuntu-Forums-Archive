---
title: "Ibex Error"
date: 2008-12-13
forum: General Help
---

### Post by BlackSwordD2 on 2008-12-13
I seem to have had the same string of bad luck as many other Ibex users have had with no sound post update (which is the definite cause as i have one computer 100% updated with no sound and another with 0 updates and runs flawlessly). Been searching around for a while for a solution (don't want to live in the dark by never updating). found one major tutorial which may very well fix my problem but i think im just a few feet behind the finish line.

so heres what i know;

its a bug due to sloppy programming for the switch between ALSA and PulseAudio

the sound card is recognized but the driver seems to be misplaced

```
Results from aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

by mainly folowing this tutorial 
[HTML]http://ubuntuforums.org/showthread.php?t=789578&highlight=ibex+bug[/HTML]

i believe that my problem lies in this line of text
```
$ pulseaudio & pavucontrol
[1] 24626
W: ltdl-bind-now.c: **Failed to find original dlopen loader.**
E: pid.c: [COLOR="Red"]**Daemon already running.**[/COLOR]
E: main.c: [COLOR="Red"]**pa_pid_file_create() failed.**[/COLOR]
[1]+  Exit 1                  pulseaudio

```

I have that feeling due to more searching around in that forum i see similar issues with others but i still cant figure out how to fix this bug

---

