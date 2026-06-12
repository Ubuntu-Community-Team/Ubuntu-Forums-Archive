---
title: "General observation about MIDI keyboards."
date: 2009-04-18
forum: General Help
---

### Post by dirkmitt on 2009-04-18
Hello,

I've noticed that some of you were having trouble getting a USB MIDI keyboard to work, which you had already purchased, because I was doing a lookup of the same keyboard prior to buying mine.

On that note, I'm not a Ubuntu user, using Kanotix Thorhammer myself, Kernel 2.6.24 .  But my advice may also help some Ubuntu users, and may avert the risk that somebody throws out his $200 keyboard unnecessarily. The other person's question has since passed into the READ ONLY section, for which reason I'm placing a new thread, moderators permitting.

I was able to get my M-Audio Oxygen 61 MIDI controller keyboard to work very well under Linux. I did load the kernel module

snd_usb_audio

manually. But there is a general observation about hardware MIDI, which could be useful to the other users, who were entry-level in music just as I am.

There is a general discrepancy between how any computer-MIDI works, and how professional MIDI boxes work. In computer-MIDI it's common that the MIDI controller chooses which instrument to play, so that simply to send a MIDI file to a MIDI server will allow it to play. I happen to be using TiMidiTy myself.

But in most professional MIDI setups, the keyboard does not have a setting that chooses an instrument number, a bank number, etc., because here this is chosen from a dial on the physical MIDI synth. Who knows, maybe there are numerous professional MIDI controller keyboards, which have this setting? But just to be sure, the Oxygen 61 does not have it as part of its hardware function. So, I did try what the other Ubuntu forum users had tried, just to make sure that it would not work, and no surprise it doesn't work. I also can't just connect my keyboard's MIDI output to TiMidiTy via 'Aconnectgui', and expect the keyboard to play.

But the fact that my keyboard shows up by name there, is already a good sign, and it does finally work up to my expectations.

In order to get this to work, just having the SoftSynth port is not enough. One needs to have DAW ("Digital Audio Workstation") software installed, from which the choice of which virtual instrument to play can be made more interactively. I happen to have "FL Studio 7" up and running under "Wine", because version 8 of FL Studio is using a license validation system, that Wine was not supporting the last time I checked. And under FL Studio 7, I can select the still-properly-named keyboard as my MIDI input, and can then play all the virtual instruments correctly.

I've been having a lot of fun with this !

But I think this is also why M-Audio does not officially claim to be Linux-compatible. The keyboard ships with software which I don't use. And this software is really not Linux compatible. BUT, certain controllers on the keyboard have specific effects, only due to the software. As a general MIDI keyboard, using preset 1, these are just arbitrary virtual MIDI controllers which get passed on to the software, and which need to be programmed in FL Studio, to control a virtual knob there by choice. But it could be any virtual knob, not just the one which is labeled on the keyboard, and so far I've also tested that the numbered slider chosen by me will pilot the GUI-depicted effect, chosen by me.

And yet, some of the features of the keyboard are meant to have a specific effect, which may or may not depend on the software one is using, depending on how MIDI-like that intended effect happens to be. If you want to record your melody and play it back, you're going to have to ignore the labels on the keyboard for doing so, and are going to have to use the controls in your software.

One item of advice which was given in this forum, is that some M-Audio products require a special Linux firmware driver. BUT, the Oxygen 61 is not one of those products. I was afraid that the other person might try very hard to install incorrect firmware and screw up their setup, while what you really need is DAW software. Mine works with no firmware, but as I said with the sliders, knobs and wheel assigned by my whim, not assigned to the functions that they would have with the supplied M-Audio software.

Dirk

Edit: For the benefit of other people, who may not have the cash outlay to buy a license of FL Studio, since like me they also don't have the budget for a Axiom keyboard, I did test the Oxygen 61 with LMMS ("Linux MultiMedia Studio") which *is* an example of DAW software. Here, the extra step one needs to take, in my case just to get the default Triple Oscillator virtual instrument to play, is that one needs to click on the keyboard-shaped icon in the instrument's track, which will produce a MIDI In and a MIDI Out Context-Menu submenus. And here one can both see and select as an available MIDI Input, the Oxygen 61.

But if you forget to set the individual track of this software to use a specific MIDI Input, then it won't be listening to any MIDI Input, and will only work from the GUI (the mouse).

---

### Post by mint gum on 2009-09-17
im trying to get my usb midi oxygen 61 to work with fl studio 9. it said file or command not found when i type snd_usb_audio in a terminal. i also downloaded aconnectgui and timidity no luck so far. i would like to use jackd for the wineASIO driver, with the oxygen 61 but fl studio only recognizes my midi when i put the wine audio config as oss. my alsa produces no sound with fl. i think i have to fix it though, somehow. what type of audio driver are you using? How exactly did you get this to work? please explain step by step. it will be greatly appreciated thanks!

---

