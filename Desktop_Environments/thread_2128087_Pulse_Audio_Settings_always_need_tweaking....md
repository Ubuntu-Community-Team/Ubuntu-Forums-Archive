---
title: "Pulse Audio Settings always need tweaking..."
date: 2013-03-22
forum: Desktop Environments
---

### Post by dkolars on 2013-03-22
Normally (?), Pulse Audio works just fine... but, I use Skype 1x a week... before I can use it however, I have to go to the PA Volume Control panel, under "Configuration", "Built-in Audio",  and change the setting from "Analog Stereo Duplex" to "Analog Stereo Output".  For some reason, something keeps changing it back to Duplex, and that connection on Skype is static-y, and unuseable.  

So, any idea why it keeps re-setting itself to the Duplex setting?  Now that I know what I have to do to use things, I just do it, but it shouldn't oughta be that way!  TIA...

---

### Post by dabl on 2013-03-22
It probably depends on what else you are doing during the other 6 days per week.  For example, plug in headphones and the output will switch automatically to headphones (or it should).  Plug in a webcam and it will automatically become an available input device, but you might have to mute the analog mic input to use the webcam.

On my KDE 4.9.5 desktop, leaving the default "Analog Stereo Duplex" does not interfere with Skype -- in Skype settings > options > sound devices, I leave it set to "PulseAudio Server (local)" and it works great. 

In the KDE systemsettings > multimedia, there is a way to "promote" the analog stereo device to top priority, but I'm not familiar with the Xubuntu interface to sound devices.  Sorry.

---

### Post by dkolars on 2013-03-22
Thanks...  But, I never plug in headphones and my webcam is always plugged in but never used except for Skype 1x a week...  Checked my settings in Skype...  All set to "PulseAudio Server (local)" --  made a Test Sound, and it was static-y...  PA was set to Analog Stereo Output... changed it to Analog Stereo Duplex, and static went away... Seems as tho' whichever one it is set to, it has to be changed to the other to make it static free... weird.

---

