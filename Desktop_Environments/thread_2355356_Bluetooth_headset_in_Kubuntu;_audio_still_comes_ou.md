---
title: "Bluetooth headset in Kubuntu; audio still comes out of speakers"
date: 2017-03-12
forum: Desktop Environments
---

### Post by ravalox on 2017-03-12
So I've looked and I don't think I see a relevant topic that has an answer- I have a bluetooth headset that I connect to my kubuntu laptop; connects just fine but for some reason it still sends the audio from the speakers.  I've tried to tweak every setting I've found; in the bluetooth menu for the audio profile it gives me a few options; High Fidelity Playback (A2DP sink), Headset Head Unit (HSP/HFP), or off.  None of these put the audio through to the headset.  I don't see anything in the UI to make this happen; this seems like a simple thing that should have a simple solution.

---

### Post by ajgreeny on 2017-03-12
I don't use buetooth for anytyhing; haven't even got the hardware to do so, but I think a workaround for this may be using pulseaudio-volume-control which you get to from the panel **Volume icon ->Sound Settings ->Output Devices** tab and muting the speakers there.

I am assuming that will not affect bluetooth volume, but as I have no experience of that system, I can't say for sure.

---

### Post by jeremy31 on 2017-03-12
I usually have to select audio profile "off" then disconnect from my headset, reconnect and select audio profile A2DP.  Then I check the sound output device like ajgreeny described.

It seems to be the result of some conflict between Bluez and Pulseaudio

---

### Post by ravalox on 2017-03-12
Wow, that's hardly seamless.  I figured out the pavucontrol thing but even with that when I disconnect the bluetooth headset it goes haywire and reconnecting and configuring everything is a bear.  This is a mess.  I can reboot to windows and operate with the headset seamlessly.  I'll see if I can submit something to launchpad- I have to imagine this issue has been around for years too.

---

### Post by michelbevan on 2017-03-12
You have to configure the sound device settings to send the output to the desired device. I am sure there is something mistake your settings. Try it now and enjoy...!

---

### Post by jeremy31 on 2017-03-13
> **ravalox said:**
> Wow, that's hardly seamless.  I figured out the pavucontrol thing but even with that when I disconnect the bluetooth headset it goes haywire and reconnecting and configuring everything is a bear.  This is a mess.  I can reboot to windows and operate with the headset seamlessly.  I'll see if I can submit something to launchpad- I have to imagine this issue has been around for years too.

This issue wasn't present in Ubuntu 14.04 that I know of
There is an a2dp.py program referenced to at [https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197) that will help automate the process

---

