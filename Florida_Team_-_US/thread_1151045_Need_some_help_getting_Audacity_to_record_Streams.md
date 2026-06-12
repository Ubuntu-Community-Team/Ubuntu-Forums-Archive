---
title: "Need some help getting Audacity to record Streams"
date: 2009-05-06
forum: Florida Team - US
---

### Post by LaughingHorse on 2009-05-06
Hi!

First Thanks for reading this post.

I have a Dell 8300.
It has according to the Dell service tag
Card, Multimedia, Audio, SB0243 (Audigy 2 Dell)

according to what my system hardware -PCI Devices-  says:

Name: Creative Labs SB Audigy
Class: Multimedia audio controller
Domain: 0
Bus, Device, function: 2,2,0
Vendor: Creative Labs creative.com
OEM Vendor: Creative Labs Device 1003
IRQ: 17
Latency: 64
Bus Master: Yes
I/O Ports at: 0xdf00 - 0xdf40

And the hardware components whos it as a 
Audio Adapter        : Audigy2 - Audigy 2 ZS [SB0353]

rather than  SB0243

I had a version of Kubuntu installed Kubuntu 8.04 (Hardy)

I could use audacity to record audio streams on my computer using audacity. But I had to use OSS. ALSA would not work.

Recently I did a fresh install of Jaunty but changed to Ubuntu from Kubuntu for better graphics, multimedia, look and feel, etc.

I have it set to use ALSA for sound.
I can play MP3's, etc. on my computer, even in audacity.
I can use my microphone in skype.

I can not record using either my microphone or streams using audacity.

I have tried using the alsamixer from terminal. I adjusted the settings to the max before getting buzz.

I have gone through every single possible setting in audacity using the audacity device toolbar.

I tried installing Ubuntu Studio to see if that could help.
It didn't.

My sound preferences are set:

Sound Events:
Sound playback: ALSA - Advanced Linux Sound Architecture

Music and Movies
Sound Playback: Autodetect

Audio Conferencing
Sound Playback: Autodetect
Sound Capture: ALSA - Advanced Linux Sound Architecture

Default Mixer Tracks
Device: Audigy 2 ZS(SB0353)

Note: In the drop down menu there is no option for SB0243.

I tried "Test" buttons and got sound on all sound playbacks, but did not get sound on "Sound Capture"

I also went to "Control Center" and clicked on "Multimedia Systems"

Under the Audio section
Default Input
Plugin: ALSA
Device: ADC Capture/Standard PCM Playback
Pipeline: alsasrc device="hw:0,0"

I tried changing the Device to "Default"
the pipeline changed to : alsasrs

I tried testing the sound by clicking the sound button, and got no sound.

In Audacity, I tried setting it up to work under OSS, and could not record or play audio.

I set both input and output to OSS:/dev/dsp and now I get an error that says
"Error while opening sound device. Please check the input device settings and the project sample rate."

When I have Audacity set up to use ALSA for input and output, I can import MP3 and other audio files into audacity and play them. I just can not record anything.

I wanted to record streams I have on my MD player which can only record by playing through my computer and capturing the sound as it is being played. I also want to be able to record using the microphone, and record streams on my system.

Any ideas?

I am located in Jacksonville Fl.

Thanks in advance for any assistance or ideas you can provide.

So in a nutshell, I can hear sounds. I can play sounds. I can use my microhpone in skype. I just can not record anything.

---

### Post by itnet7 on 2009-05-06
> **LaughingHorse said:**
> Hi!

First Thanks for reading this post.

I have a Dell 8300.
It has according to the Dell service tag
Card, Multimedia, Audio, SB0243 (Audigy 2 Dell)

according to what my system hardware -PCI Devices-  says:

Name: Creative Labs SB Audigy
Class: Multimedia audio controller
Domain: 0
Bus, Device, function: 2,2,0
Vendor: Creative Labs creative.com
OEM Vendor: Creative Labs Device 1003
IRQ: 17
Latency: 64
Bus Master: Yes
I/O Ports at: 0xdf00 - 0xdf40

And the hardware components whos it as a 
Audio Adapter        : Audigy2 - Audigy 2 ZS [SB0353]



Have you tried anything more current than 8.04? Also if you right click on the volume control (Speaker near clock if using gnome) and open volume control. You can select the volume control preferences this will permit you to add a whole lot more options that you can adjust and play with. Sometimes the microphone is muted under the Record option that you can enable (if it isn't by default).  Other than that there isn't much I can suggest. We have a couple of Florida Team Loco Members who happen to live in/or near Jacksonville. we might be able to get one of them to meet up with you and help you to troubleshoot. 

Pop into the IRC channel and ask around or reply here and I will see if we can get you some help!

Chris C. 

itnet7

---

