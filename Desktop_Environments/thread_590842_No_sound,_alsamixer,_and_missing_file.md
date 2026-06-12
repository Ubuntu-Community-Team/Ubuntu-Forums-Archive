---
title: "No sound, alsamixer, and missing file"
date: 2007-10-25
forum: Desktop Environments
---

### Post by Glowing Fish on 2007-10-25
There is actually a story behind this (as there always is), but most of it isn't too important just yet.

I have updated to Gutsy, which I have actually been using for several months now as it was in development, with some warts. I was hoping that in the finished version, everything would be fine. However, since I have been apt-get dist-upgrading since Dapper, I think that my system might have a lot of kludge in there.

The only real problem right now is that I don't have any type of audio beyond system beeps. When I play a file in xmms, it shows that it is moving forward, but I don't get any sound. (and yes, I have done the most obvious thing and checked that the speakers are plugged in the right place). After trying various things, I tried to open up alsamixer, which gave me this error:

ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

It looks like it needs a module for my sound blaster card, but where and how does that module get in there? I can't seem to find anything through apt-get

---

### Post by renzokuken on 2007-10-25
did it work before (or ever) ?

have you tried compiling/installing the latest alsa-driver?

could you post the output of ```
lspci -v
```

---

### Post by Glowing Fish on 2007-10-25
1. It did work before, although that was on both a different computer, and a different version of ubuntu. (I moved this harddrive from an AMD 1.2 GHz into a P4 2.2 GHz, which made the sound work poorly, and then work not at all). 

2. I haven't.

3. 02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4832 SBLive! Value
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at b800 [size=32]
        Capabilities: <access denied>

is the relevant output, I believe.

---

### Post by mlind on 2007-10-25
remove ~/.asoundrc and then do
```

asoundconf list
asoundconf set-default-card foo

```
where the foo is one of the sound cards listed by 'asoundconf list'

Are you using pulseaudio btw?

The missing /usr/lib/alsa-lib/libasound_module_ctl_pulse.so, this library is provided by **libasound2-plugins** package.

---

### Post by Glowing Fish on 2007-10-25
I am using pulse audio, and this does work.

Well, it mostly works. I can get sound now (thank you!) but it is still turned down really low, even with sound up to maximum on my subwoofer set, and in my application. 

I am thinking I should go into alsamixer and turn things up, but that alsamixer gives me this error:

*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused

---

### Post by mlind on 2007-10-27
make sure you're member of pulse-rt group, so you get access to pulseaudio
```

sudo adduser $USER pulse-rt

```
you'll need to relogin to your xserver session after this.

I have these pulseaudio related packages installed, you could try to install the same packages
```

libao-pulse
libgstreamer-plugins-pulse0.10-0
libpulse-browse0
libpulse-mainloop-glib0
libpulse0
padevchooser
paman
paprefs
pavucontrol
pavumeter
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-gconf
pulseaudio-module-hal
pulseaudio-module-x11
pulseaudio-module-zeroconf
pulseaudio-utils

```

To raise sound volume, open 'alsamixer' and max 'Master, PCM, Front' channels volume.

---

### Post by Glowing Fish on 2007-10-28
This seems to have not changed anything at all.

alsamixer still gives me this error:

*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused


And sudo alsamixer gives me the same error as well.

---

### Post by Glowing Fish on 2007-10-28
For added information, on System->Preferences->Sound, there is a "Sound Playback Test"

This works with autodetect, OSS, and multichannel

It does not, however, wrok with ALSA, or PulseAudio

---

