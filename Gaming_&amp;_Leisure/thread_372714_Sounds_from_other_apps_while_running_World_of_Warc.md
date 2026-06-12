---
title: "Sounds from other apps while running World of Warcraft through cedega"
date: 2007-02-28
forum: Gaming &amp; Leisure
---

### Post by jfanaian on 2007-02-28
I am running World of Warcraft through cedega and the game runs fine. The problem is that while I'm running the game no other sounds work, such as gaim event sounds. I tested a few things while the game is open to simply debug the problem. 

I tried to run a test from gnome-sound-properties and got the following error:

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Resource busy or not available.

```

I tried to run an mp3 using mpg321 and got the following:
```

jfanaian@jfanaian-laptop:~$ mpg321 sample.mp3
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
Title  : It's Over                       Artist: 3against1                     
Album  : 3 Song Demo                     Year  : 2003
Comment:  00001E4C 0000209A 00004F5E 00  Genre : Alternative                   

Playing MPEG stream from sample.mp3 ...
MPEG 1.0 layer III, 128 kbit/s, 44100 Hz stereo
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
ALSA snd_pcm_open error: Device or resource busy
- using device default
- using device default
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
Creating link /home/jfanaian/.kde/socket-t-jfanaian-laptop.
can't create mcop directory

```

I was trying to follow a few posts I found in a few different sites and this is what my ~/.asoundrc file currently looks like:
```

# ~/.asoundrc or /etc/asound.conf
# ALSA configuration file

##### USAGE #####
# Save this file as "~/.asoundrc" (for user-specific sound configuration) or
# "/etc/asound.conf" (for system-wide sound configuration) and specify ALSA
# device names ad described in the next section.


##### DEVICE NAMES #####
# This configuration file defines four devices for use by the user.  Those
# devices are "analog", "mixed-analog", "digital", and "mixed-digital".  The
# user may also re-define "default" to be identical to one of the above-named
# devices (i.e. to send all sound output to the digital output unless otherwise
# specified).  Use the device names as described below:
#  - "analog" outputs to the analog output directly and (at least on software
#  sound cards) blocks other audio output.  After playback completes, "queued"
#  sounds are output in sequence.
#  - "mixed-analog" mixes audio output from multiple programs into the analog
#  output (so you can hear beeps, alerts, and other noises while playing back
#  an audio stream).
#  - "digital" outputs to the digital output directly.  Since most (all?)
#  digital outputs expect 48kHz PCM audio, this may not work for some playback
#  (i.e. CD's--which are 44.1kHz PCM audio--or 32kHz audio streams from TV
#  recordings, etc.).
#  - "mixed-digital"

# All other devices created within this file are used only by the configuration
# file itself and should /not/ be used directly.  In other words, do not use
# the devices "analog-hw", "dmix-analog", "digital-hw", or "dmix-digital".


##### IMPORTANT #####
# To make this ALSA configuration file work with your sound card, you will need
# to define the appropriate card and device information for the "analog-hw" and
# "digital-hw" devices below.  You can find the card and device information
# using "aplay -l".


##### Configuration File #####

# Override the default output used by ALSA.  If you do not override the
# default, your default device is identical to the (unmixed) "analog" device
# shown below.  If you prefer mixed and/or digital output, uncomment the
# appropriate four lines below (only one slave.pcm line).
#
# Note, also, that as of ALSA 1.0.9, "software" sound cards have been modified
# such that their default "default" device is identical to the "mixed-analog"
# device.  Whether using an ALSA version before or after 1.0.9, it does no harm
# and has no affect on performance to redefine the device (even if the
# redefinition does not change anything).  Also, by using this ALSA
# configuration file, you once again have access to unmixed analog output using
# the "analog" device.
pcm.!default {
  type plug
## Uncomment the following to use "mixed-analog" by default
  slave.pcm "dmix-analog"
## Uncomment the following to use (unmixed) "digital" by default
#  slave.pcm "digital-hw"
## Uncomment the following to use "mixed-digital" by default
#  slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the card
ctl.!default {
  type hw
  card 0
}

# Alias for (converted) analog output on the card
# - This is identical to the device named "default"--which always exists and
# refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog" to access analog
# output on the card
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine
# "default" to do mixing, meaning this device is different from "default" and
# allows playback while blocking other sound sources (until playback
# completes).
pcm.analog {
  type plug
  slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the card
ctl.analog {
  type hw
  card 0
}

# Alias for (converted) mixed analog output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the dmix plugin (in this case 48000Hz)
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine
# "default" to do mixing, meaning this device is identical to "default" for
# "software" sound cards.
pcm.mixed-analog {
  type plug
  slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the card
ctl.mixed-analog {
  type hw
  card 0
}

# Alias for (converted) digital (S/PDIF) output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the S/PDIF hardware (in this case 48000Hz)
pcm.digital {
  type plug
  slave.pcm "digital-hw"
}

# Control device (mixer, etc.) for the card
ctl.digital {
  type hw
  card 0
}

# Alias for mixed (converted) digital (S/PDIF) output on the card
#  - This will accept audio input--regardless of rate--and convert to the rate
#  required for the S/PDIF hardware (in this case 48000Hz)
pcm.mixed-digital {
  type plug
  slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the card
ctl.mixed-digital {
  type hw
  card 0
}

# The following devices are not useful by themselves.  They require specific
# rates, channels, and formats.  Therefore, you probably do not want to use
# them directly.  Instead use of of the devices defined above.

# Alias for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.analog-hw {
  type hw
  card 0
  # The default value for device is 0, so no need to specify
#  - Uncomment one of the below or create a new "device N" line as appropriate
#    for your sound card or 
#  device 1
#  device 4
}

# Control device (mixer, etc.) for the card
ctl.analog-hw {
  type hw
  card 0
}

# Alias for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.digital-hw {
  type hw
  card 0
#  device 1
#  - Comment out "device 1" above and uncomment one of the below or create a
#    new "device N" line as appropriate for your sound card or 
  device 2
#  device 4
}

# Control device (mixer, etc.) for the card
ctl.digital-hw {
  type hw
  card 0
}

# Direct software mixing plugin for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.dmix-analog {
  type dmix
  ipc_key 1234
  slave {
    pcm "analog-hw"
    period_time 0
    period_size 1024
    buffer_size 4096
    rate 48000
  } 
}

# Control device (mixer, etc.) for the card
ctl.dmix-analog {
  type hw
  card 0
}

# Direct software mixing plugin for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.dmix-digital {
  type dmix
  ipc_key 1235
  slave {
    pcm "digital-hw"
    period_time 0
    period_size 1024
    buffer_size 4096
    rate 48000
  } 
}

# Control device (mixer, etc.) for the card
ctl.dmix-digital {
  type hw
  card 0
}

```

Also, this is the output from aplay -l:
```

jfanaian@jfanaian-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I am runnng the game on ALSA according to the cedega properties.

Can anyone help me find a solution to this problem?

Thanks

---

### Post by russianbandit on 2007-02-28
I also don't have sound on other apps when playing WoW. Might be cuz WoW ties up the sound system.

---

### Post by jfanaian on 2007-02-28
It does, from what I understand most onboard cards do not support hardware mixing, therefore two applications can't get access to sound at the same time. The idea is to set up software mixing from what I've read but I have no clue how to do this. I've tried a few different .asoundrc templates but they don't seem to work. Instead, they break sound alltogether, or have no effect on any of it.

---

### Post by Sammi on 2007-02-28
I've tried to explain this issue in the "Voice Chat" section of the community WoW/Wine howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

It should be solvable by using the aoss command.

---

### Post by justin whitaker on 2007-03-01
> **Sammi said:**
> I've tried to explain this issue in the "Voice Chat" section of the community WoW/Wine howoto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

It should be solvable by using the aoss command.

That's the trick. You need to start the other application first via CLI aoss Ventrilo and then aoss Cedega.

---

### Post by Sammi on 2007-03-01
> **justin whitaker said:**
> That's the trick. You need to start the other application first via CLI aoss Ventrilo and then aoss Cedega.Exactly. It won't work unless both the game and the voice chat application are running with the aoss command in front.

---

### Post by jfanaian on 2007-03-02
I tried that but it still didn't seem to work. The only thing is that I ran aoss cedega instead of aoss cedega PATH_TO_WOW/WoW.exe because I can't alt tab if I do it that way to run the sound. I'm going to try playing a sound first and then running the game.

---

### Post by jfanaian on 2007-03-02
I tried running aoss Songbird and playing a song, and then running aoss cedega WoW (while in the wow dir) and the song kept playing but the WoW sounds did not.

---

### Post by justin whitaker on 2007-03-02
> **jfanaian said:**
> I tried running aoss Songbird and playing a song, and then running aoss cedega WoW (while in the wow dir) and the song kept playing but the WoW sounds did not.

Hmm...that is odd. 

In Cedega, how do you have audio set up? Full Multiplex?

---

### Post by murraysw on 2007-03-02
I have the same issue and have all of the above things, however, I run WoW in WINE.  I will post my specs in a bit.

---

### Post by jfanaian on 2007-03-23
I have dmix working fine. I even went through with someone for help and they verified that I had dmix working. I mean, I can play audio from more than one app at a time. Such as having Songbird playing music, with mpg321 playing another file, and gaim still plays it sounds, all together but when it comes to cedega it just wont play nice. I changed my ~/.asoundrc to know have a device for dmix called ossmix and dsp0 pointing to that device but if I set CTL and PCM to that device it just plays no audio, but everything else has audio (music, gaim, etc.) I'm really stuck on this one.

Here's my .asoundrc as it is now
```

pcm.ossmix {
    type dmix
    ipc_key 1024          # must be unique!
    ipc_perm 0660         # sound for everybody (at least in your group)
    slave {
        pcm "hw:0,0"      # you cannot use a "plug" device here, darn.
        period_time 0
        period_size 1024  # must be power of 2
        buffer_size 8192  # dito. It
        #format "S32_LE"
        #periods 128      # dito.
        #rate 8000        # with rate 8000 you *will* hear,
                          # if ossmix is used :)
    }
}
# bindings are cool. This says, that only the first
# two channels are to be used by dmix, which is enough for
# (most) oss apps and also lets multichannel chios work
# much faster:

bindings {
        0 0   # from 0 => to 0
        1 1   # from 1 => to 1
}

pcm.dsp0 {
    type hw
    slave.pcm "ossmix"     # use our new PCM here
    #card 0
}
# mixer0 like above
ctl.mixer0 {
    type hw
    card 0
}

```

---

### Post by voidzero on 2007-04-02
Hi guys,

As a gentoo user who has experience with using ubuntu variants, I came across your thread. I also play WoW, using cedega 5.10.

I used to own a yamaha ymfpci soundcard, a very nice one with hardware mixing and optical output. Unfortunately it died on me leaving me with the option of using onboard sound (which already is in use for my voip system) or using a cmipci soundcard without hardware mixing. I chose the latter, but fortunately I'll get a new card soon :guitar: 

Anyway, I came across this same problem: wow takes up the sound leaving no option over for other apps. And the strange thing is that the sound test from cedega, *does* work.

[COLOR="DarkBlue"]So for those of you who, like me, cannot use world of warcraft with sound together with other applications, even when you have tried aoss cedega or esddsp cedega, try to use alsa (not OSS) and turning off the mmap setting. It works for me...... but pretty choppy.
[/COLOR]
Get a new soundcard is probably the best tip though, like a yamaha or creative labs, that does support hardware mixing. After this experience I know I will, soon.

Hope this helps.
Mark

---

