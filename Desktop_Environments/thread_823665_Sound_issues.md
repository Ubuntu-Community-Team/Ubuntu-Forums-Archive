---
title: "Sound issues"
date: 2008-06-09
forum: Desktop Environments
---

### Post by frankos44 on 2008-06-09
My shuttle PC has sound issues on hardy 32bit.

On fresh installation all worked fine including sound from flash player plug-in except for system sounds found in system->preferences->sound. 

I installed esound as follows:

$ sudo apt-get install esound

This caused my desktop to freeze shortly after logging in.

After browsing the internet I found this:

$ sudo apt-get install esound esound-clients esound-common libesd0 libesd0-dev gstreamer0.10-esd

That stopped it freezing, got the system sounds working but now there is no sound on flash player now.

Any ideas?

---

### Post by Zorael on 2008-06-09
As far as I'm aware, if you're using Hardy then you're using the ESD drop-in replacement, PulseAudio. As such, to get sound in FF3, try installing the **libflashsupport** package.

As for what happens if you *manually* install ESD, heck if I know. Likely Pulse still overrides it, but don't quote me on that.

---

### Post by frankos44 on 2008-06-10
> **Zorael said:**
> As far as I'm aware, if you're using Hardy then you're using the ESD drop-in replacement, PulseAudio. As such, to get sound in FF3, try installing the **libflashsupport** package.

As for what happens if you *manually* install ESD, heck if I know. Likely Pulse still overrides it, but don't quote me on that.

Is PulseAudio installed as default? What is FF3 and how do you install libflashsupport?

---

### Post by Zorael on 2008-06-10
PulseAudio is the default in Ubuntu Hardy, yes. Not Kubuntu though, and not sure about {Xu,Flux,Edu,...}buntus.
> PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.
FF3 is just an abbreviation for Firefox 3. My apologies, I was just lazy and didn't think to convey the meaning better than that. :<

To install the **libflashsupport** package, just pop up Synaptic, search for it, tag it for installation and apply. Alternatively, enter this in a terminal.
```
$ sudo aptitude install libflashsupport
```
To explain, Flash 9 doesn't work well with pulse. It will require exclusive access to your soundcard, which means that you'll either *only* get sound in your Flash content (read: browser), or *only* in your other programs. So "no sound in firefox" fits the description.

The new Flash 10 beta supposedly works (better) with it, though I imagine it's not without its own bugs. See [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html).

For general hints on getting Pulse to work with your apps, see [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup).

---

### Post by frankos44 on 2008-06-10
> **Zorael said:**
> PulseAudio is the default in Ubuntu Hardy, yes. Not Kubuntu though, and not sure about {Xu,Flux,Edu,...}buntus.

FF3 is just an abbreviation for Firefox 3. My apologies, I was just lazy and didn't think to convey the meaning better than that. :<

To install the **libflashsupport** package, just pop up Synaptic, search for it, tag it for installation and apply. Alternatively, enter this in a terminal.
```
$ sudo aptitude install libflashsupport
```
To explain, Flash 9 doesn't work well with pulse. It will require exclusive access to your soundcard, which means that you'll either *only* get sound in your Flash content (read: browser), or *only* in your other programs. So "no sound in firefox" fits the description.

The new Flash 10 beta supposedly works (better) with it, though I imagine it's not without its own bugs. See [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html).

For general hints on getting Pulse to work with your apps, see [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup).

Thnaks for the suggestions. I installed flashplayer10 and tried PulseAudio as well as Autodetect but still no sound in flash, sound still Ok everywhere else. I noticed that a reboot is required when switching between the Sound playback options.

---

