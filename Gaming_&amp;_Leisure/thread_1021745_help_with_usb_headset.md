---
title: "help with usb headset"
date: 2008-12-25
forum: Gaming &amp; Leisure
---

### Post by Ixonal on 2008-12-25
so yeah, I got a usb headset which really has no support or drivers at all for linux, but I noticed that I get sound out through the headphones if I dump a file into /dev/dsp2. There some way I could use this fact to get the headphones working?

---

### Post by Ahadiel on 2008-12-26
System => Preferences => Sound
Does your usb headset show up in there?

---

### Post by kostkon on 2008-12-26
> **Ixonal said:**
> so yeah, I got a usb headset which really has no support or drivers at all for linux, but I noticed that I get sound out through the headphones if I dump a file into /dev/dsp2. There some way I could use this fact to get the headphones working?
Which Ubuntu version do you have?

Also, please post the output of
```
aplay -l
```
here

---

### Post by Ixonal on 2008-12-27
ahadiel: yes it does, as C-Media USB Headphone Set, but all the tests throw errors

kostkon: runnin ubuntu 8.10, and here's the output you asked for.
```

ixonal@Reinverka-II:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

can probly ignore the sound blaster live, stole it from my old computer and never really got it workin right, just never took it back out. I use onboard audio right now.

btw, sorry that took so long, work has been rather hectic recently...

update: rebooted (did some screwy stuff earlier tryin to get this thing to work, so that probly messed it up some) and I no longer get any errors when I try to do tests in system->preferences->sound, but I get no audio from 'em (headset or speakers) either.

---

### Post by Ixonal on 2008-12-28
hmmmmm, so I got VLC to send audio to it and it works fine that way (was way easier than I thought it'd be, probly why I didn't try earlier) I still need to get audio from wine programs too at least (after all, got these for vent)

---

### Post by kostkon on 2008-12-28
> **Ixonal said:**
> hmmmmm, so I got VLC to send audio to it and it works fine that way (was way easier than I thought it'd be, probly why I didn't try earlier) I still need to get audio from wine programs too at least (after all, got these for vent)
Yes, it seems your headset is recognised and should work just fine.

A good solution to your problem is to set your sound playbacks to *Autodetect* in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) and then use the *PulseAudio Device Chooser* utility to easily reroute any audio from your applications from your speakers (i.e. sound card) to your USB headser or vice versa.

Thus, install the *PulseAudio Device Chooser* using *Synaptic*. Then run it (its menu entry will be in *Applications &#8594; Sound & Video*) and it will put its icon in your taskbar. Left-click on its icon and select *Volume Control...*

In the *Playback* tab you should see all the applications that are currently running (only the ones that produce sound, obviously) and their volume levels. You can right-click on each of them and select *Move Stream...* to easily move their audio streams from your sound card/speakers to your headset, for example. *PulseAudio* will remember your choice the next time.

Furthermore, select the *Output Devices* tab, right click on the device you want your applications to use by default to output their sound and enable the *Default* option. For example, you may want to use your speakers as the default audio device in your system. Thus, right-click on your sound card and to set it as the default. Do the same in the *Input Devices* tab to set the default input device.

I saw that you tried to make *VLC* use your headset. If you have changed the sound configuration of *VLC* then you need to change it back again to the default. The default must be *ALSA* or *PulseAudio*. If this is not the default output device in *VLC* then set it yourself to one of above.

Then you can use the *PulseAudio Device Chooser* to send the sound of VLC to your headset or if you have set the default device in your system to be your headset then *VLC* will send its sound there automatically.

Hope that helps.

For any problems or questions regarding the above, don't hesitate to ask here.

---

### Post by Ixonal on 2008-12-28
sweeeeet. got that set up and switched my audio streams around with vlc (got it set back to default alsa and installed the pulseaudio plugin for it). gunna test it out and make sure it all works with my games and what not after work today.

edit: just had a thought: there a way I could set up a keybind to switch the output device of my currently selected program using that? like I turn on vlc and then press ctrl 1 or something like that and it switches to my headset?

update: got audio from WoW and vent runnin in 'em fine, so that's all good. just wonderin bout the keybind question now

---

### Post by ex.hav0k on 2009-01-09
checkout xkeybind, its in the repos.  it works pretty good :)

---

