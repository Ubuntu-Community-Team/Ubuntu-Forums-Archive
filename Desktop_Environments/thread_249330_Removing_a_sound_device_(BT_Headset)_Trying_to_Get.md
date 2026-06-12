---
title: "Removing a sound device (BT Headset): Trying to Get sound recording to work"
date: 2006-09-02
forum: Desktop Environments
---

### Post by HarryHalpin on 2006-09-02
I'm having issues recording sounds with anything and even playing sounds with audacity. Note that a few months ago everything worked fine, including audacity and even video/audio DJinging using Lives - so I know it's not a fundamental hardware problem. 

However, this summer I tried installing a bluetooth BT headset, and I need help removing it's drivers, since I think its the source of my problem. In essence, the BT Headset drivers are loading as the default sound card (0) and therefore all applications which try to use sound fail, until I manually change it using "System >> Sound >> Preferences" in GNOME. Even after changing it manually, any sound recording application (See [1] below) and audacity still fail (See [2] below)  - and they worked beforehand. I assume they are still perhaps trying to use the BT Headset instead of my sound card, and are bypassing GNOME. However, there must be a way to change or get rid of the BT Headset drivers on the commandline - and change it permanently! What's the sequence of steps?

A friend helped me install btsco, so I'm not sure exactly what he did. Worse case, I could upgrade to dapper, but I'd like to start with a fresh sound card install and a fresh alsa install. However, I'm not even sure how todo that. 

My goal is to get audacity working again, as well as to use Skype with my new non-wireless off-the-shelf headset+mike from Sony.

As one can tell, the BT Headset loads as default because it's numbering is 0:

$ less /proc/asound/cards
0 [Headset        ]: Bluetooth SCO - BT Headset
                     BT Headset 1
1 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with AD1981B at 0xc0000c00, irq 11

$aplay -l
card 0: Headset [BT Headset], device 0: Bluetooth SCO PCM [BT SCO PCM]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel
82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958
[Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[1] Sound recording both with GNOME Sound recorder and the commandline "sound-recorder" both fail to record sound. In facdt, GNOME Sound Recorder just starts "recording" and then hangs forever, eventually leading me to kill the process.

mplayer produces:
"Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts."

but it works as long as change my System>>Administration>>Sound to my sound card as opposed to the BT Headset.

[2] Audacity
Note i've read previous posts and already disabled esd via killall esd. Esd is not the problem. I've also "chmod 666" both /devices/dsp and /devices/dsp1. 

With "audacity" it says "There was an error initializng the audio/io layer"

With "aoss audacity" when we get:
Pa_SetLatency: could not SNDCTL_DSP_SETFRAGMENT
Pa_SetLatency: numBuffers = 2, framesPerBuffer = 512, powerOfTwo = 11
Pa_SetupDeviceFormat: could not SNDCTL_DSP_SETFMT
Pa_SetLatency: could not SNDCTL_DSP_SETFRAGMENT
Pa_SetLatency: numBuffers = 2, framesPerBuffer = 512, powerOfTwo = 11
Pa_SetupDeviceFormat: could not SNDCTL_DSP_SETFMT
but it allows me to open files, then producing a 
"Error while opening sound device..." error.

Could it be my sampling? I've changed it around a few times but to no avail!

---

### Post by HarryHalpin on 2006-09-02
I suspect now I could do this with **modprobe**...but not exactly sure how without messing things up.

---

