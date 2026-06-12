---
title: "No Sound with Flash in Firefox"
date: 2009-03-09
forum: Desktop Environments
---

### Post by n8dude on 2009-03-09
Hey guys, I decided to give Kubuntu a try. Once I had everything installed, I copied over my old Firefox profile. Now there is no sound in Flash Videos at all.None of my Media Files play at all either, and I do have the Medibuntu packages installed so it's not a codec issue.  Anyone else having similar issues? I am using KDE 4.2 x86_64 with the 64bit Flash plugin installed if that helps.

---

### Post by Zorael on 2009-03-10
Did you install kubuntu-desktop atop an existing Ubuntu installation? Ubuntu uses PulseAudio and KDE's Phonon multimedia layer doesn't (per default), so perhaps they're conflicting.

If this is a fresh Kubuntu installation, that's weird. What's the terminal output of the following?
```
$ aplay -l
$ cat /etc/asound.conf
$ lshw -c multimedia
```
Does sound output if you enter this?
```
$ speaker-test -c2 -twav
```

---

### Post by n8dude on 2009-03-10
The outputs of those commands are:

aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /etc/asound.conf
cat: /etc/asound.conf: No such file or directory
That's probably one of the problems right there.

lshw -c multimedia
*-multimedia
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

And I do not hear any sound when I do speaker-test -c2 -twav
I do hear sound from Amarok and when I login though. Any thoughts?

---

### Post by Zorael on 2009-03-10
Well, you have several devices (analog, digital, modem). Perhaps it's outputting to the wrong one?
```
$ aplay -L
```
/etc/asound.conf should be empty/not exist, so no worries there.

If Amarok can play sound properly, stuff *works*, you just need to get Flash to output to the right device, or set the right device as the default one.

---

### Post by n8dude on 2009-03-10
Would you have any idea how to do that? I was wondering if it had something to do with Phonon, but I am pretty new to KDE4 so I wouldn't really know.

---

### Post by Zorael on 2009-03-11
Looking through the menus real fast, I'd try *System Settings* -> *Multimedia*, prefer/defer audio devices as you wish, *Apply Device List To*: everything.

Obviously, one way to know for sure if it's outputting to the wrong port (device) would be to connect something to that other port (analog/digital) and see if sound plays there.


Furthermore. I'm not sure it applies to this issue, but if you have several different cards, you can assign defaults by using the **asoundconf** script. I think it's included in Intrepid by default. (It certainly is in Jaunty a5.)
```
zorael@tleilax:~$ asoundconf
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf [COLOR="Lime"]set-default-card[/COLOR] [COLOR="RoyalBlue"]PARAMETER[/COLOR]
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio
asoundconf set-oss PARAMETER
asoundconf unset-oss

zorael@tleilax:~$ asoundconf list
Names of available sound cards:
[COLOR="RoyalBlue"]Intel[/COLOR]

zorael@tleilax:~$ asoundconf [COLOR="Lime"]set-default-card[/COLOR] [COLOR="RoyalBlue"]Intel[/COLOR]
*<stuff supposedly happens and .asound* files are created in your home directory>*
```

Also, there's a difference between aplay -l and aplay **-L**.
```
zorael@tleilax:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1                                                   
  Subdevice #0: subdevice #0                                        

zorael@tleilax:~$ aplay **-L**                                          
**default**:CARD=Intel                                                  
    HDA Intel, ALC1200 Analog                                       
    Default Audio Device
**front**:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Front speakers
**surround40**:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
**surround41**:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
**surround50**:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
**surround51**:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
**surround71**:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
**null**
    Discard all samples (playback) or generate zero samples (capture)
```
To test a certain device, use speaker-test with the **-D** argument. Increment -c with as many channels (speakers) as you want to test. Like so:
```
zorael@tleilax:~$ speaker-test -c[COLOR="Red"]2[/COLOR] -twav **-D**[COLOR="DarkOrchid"]surround40[/COLOR]

speaker-test 1.0.18

Playback device is [COLOR="DarkOrchid"]surround40[/COLOR]
Stream parameters are 48000Hz, S16_LE, [COLOR="Red"]2[/COLOR] channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 2.742553
...
```

---

### Post by Zorael on 2009-03-11
<double post, forum went bananas>

---

### Post by Zorael on 2009-03-12
Mmkay, so I suddenly ran into the same problem.

My Intel HDA card has several channels that all affect output (Master, Headphone, PCM and Front). They're multiplicative, in the sense that if I have them all at 80%, the end volume is 0.8*0.8*0.8*0.8 = 0.4096, ~41%. My multimedia keys on this laptop control the Master volume, so I just set the other three reasonably high and live with it.

Turns out that KDE system sounds and Amarok 2 (amongst others, perhaps) disregard the PCM channel, while still obeying Master, Headphone and Front. Flash depends on them all. And my PCM volume had somehow dropped to 0.

KDE/Amarok: 0.8*0.8*0.8*0.8 = **0.4096**
Flash: 0.8*0.8*[COLOR="Red"]**0**[/COLOR]*0.8 = [COLOR="Red"]**0**[/COLOR]

Pop up a terminal and start **alsamixer** to make sure that's not what's causing it for you.
```
$ alsamixer
```
May need to make that **alsamixer _-Dhw_** if you're running Pulse, not sure.

---

### Post by n8dude on 2009-03-14
Looks like that solved it! Thanks for your help.

---

### Post by cgoddard on 2009-04-10
Very helpful.  Thank you.

---

### Post by anupkshah on 2009-04-25
Thanks. Adjusting the PCM channel did it for me too. It was zero for some reason.

The previous day, after rebooting from the upgrade to Kubuntu 9.04, sound was working as per 8.10 (where if say I was using Firefox, then no sound from Amarok, or the other way round. I'd have to close the former and then open the latter for sound to work). 

This morning when I booted up, sound didn't work from Firefox at all. At first I uninstalled and reinstalled the flash plugin. The I came across this post, and adjusting the PCM channel did the trick (so I don't know if un/reinstalling the flash plugin has an impact or not).

---

### Post by sidnick on 2009-04-26
I checked my levels with alasmixer and while I have a headphone label its unsetable. Any idea why that would be?

---

### Post by sidnick on 2009-04-26
never mind, even though the headphone setting is 0 and can't be set at all, with all the other levels set to high (two called Front Mi, Surround, Center, LFE, Side, and Line) the sound now works, 

Thanks a bunch!

---

### Post by eldette on 2012-03-26
I have to revive the thread as I'm facing the same problem with no sound on flash/ firefox although my vlc and system sounds are ok. I had a gstreamer update yesterday, perhaps it's related? I'm running Kubuntu 11.10 64bit and all seems fine with my alsamixer and my multimedia section in Settings...

aplay -l output:
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```cat /etc/asound.conf output:
No such file or directory exists.

lshw -c multimedia output:
```
  *-multimedia            
       description: Audio device
       product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:e1600000-e1603fff   
```Any help?

---

