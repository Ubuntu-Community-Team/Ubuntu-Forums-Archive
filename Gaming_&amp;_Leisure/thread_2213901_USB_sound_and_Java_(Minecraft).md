---
title: "USB sound and Java (Minecraft)"
date: 2014-03-29
forum: Gaming &amp; Leisure
---

### Post by Nikobelia on 2014-03-29
Hey there,

I'm trying to get Minecraft sound to play over a USB headset - it works fine on speakers, but it'd be nice have voicechat and in-game sound at the same time! 

So I'm using 64bit Xubuntu and running Minecraft through OpenJDK 7 and Pulseaudio. Sound works fine over speakers. 

Java's sound.properties file seems configured sensibly:

```
shep@harbinger:/$ locate sound.properties
/etc/java-7-openjdk/sound.properties
/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/sound.properties

```

```

# OpenJDK on Ubuntu is configured to use PulseAudio by default
javax.sound.sampled.Clip=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
javax.sound.sampled.Port=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
javax.sound.sampled.SourceDataLine=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
javax.sound.sampled.TargetDataLine=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
```

The headset seems to be set as the default device according to ```
pactl stat
```

```
shep@harbinger:~$ pactl stat
Currently in use: 19 blocks containing 279.8 KiB bytes total.
Allocated during whole lifetime: 302522 blocks containing 524.1 MiB bytes total.
Sample cache size: 0 B
Server String: unix:/home/shep/.pulse/8025889c7b91e3c83926e02d00000002-runtime/native
Library Protocol Version: 26
Server Protocol Version: 26
Is Local: yes
Client Index: 38
Tile Size: 65472
User Name: shep
Host Name: harbinger
Server Name: pulseaudio
Server Version: 1.1
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.usb-047f_ad01-00-U0x47f0xad01.analog-stereo
Default Source: alsa_input.pci-0000_00_1b.0.analog-stereo
```

The default sink matches the headset on ```
pactl list
```:

```


Sink #1
	State: SUSPENDED
	Name: alsa_output.usb-047f_ad01-00-U0x47f0xad01.analog-stereo
	Description: GameCom 777 5.1 Headset Analogue Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 5
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Base Volume: 100%
	             0.06 dB
	Monitor Source: alsa_output.usb-047f_ad01-00-U0x47f0xad01.analog-stereo.monitor
	Latency: 0 usec, configured 0 usec
	Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "USB Audio"
		alsa.id = "USB Audio"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "1"
		alsa.card_name = "USB Device 0x47f:0xad01"
		alsa.long_card_name = "USB Device 0x47f:0xad01 at usb-0000:00:1a.0-1.1, full speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:1a.0-usb-0:1.1:1.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/sound/card1"
		udev.id = "usb-047f_ad01-00-U0x47f0xad01"
		device.bus = "usb"
		device.vendor.id = "047f"
		device.vendor.name = "Plantronics, Inc."
		device.product.id = "ad01"
		device.product.name = "GameCom 777 5.1 Headset"
		device.serial = "047f_ad01"
		device.form_factor = "headset"
		device.string = "front:1"
		device.buffering.buffer_size = "352800"
		device.buffering.fragment_size = "176400"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analogue Stereo"
		device.description = "GameCom 777 5.1 Headset Analogue Stereo"
		alsa.mixer_name = "USB Mixer"
		alsa.components = "USB047f:ad01"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-headset-usb"
		device.intended_roles = "phone"
	Ports:
		analog-output: Analogue Output (priority: 9900)
	Active Port: analog-output
	Formats:
		pcm
```

Audio in Firefox, Quod Libet, etc works fine, but even though Java is set to route its sound through this PulseAudioMixerProvider it doesn't seem to be getting there. Has anyone got any tips?

---

### Post by R33D3M33R on 2014-03-29
I use pavucontrol GUI (sudo apt-get install pavucontrol) to control sound outputs of the programs I'm using. Yes, you will probably have to manually switch outputs everytime you run a program, but if you not do this often, it's no problem.

---

### Post by Nikobelia on 2014-03-29
Pavucontrol didn't fix it, though I do really like it for ease of configuration. I could configure every other audio source to play through my headset in Pavucontrol, but Minecraft refused. My headset showed up in the dropdown menu of playback devices but it couldn't be selected; it reverted back to the old setting immediately.

I looked into command line control of Pulseaudio and found [this thread]("http://askubuntu.com/questions/71863/how-to-change-pulseaudio-sink-with-pacmd-set-default-sink-during-playback") about configuring Pulseaudio, which gave me some useful commands
```

pacmd list-sinks
```
Show playback devices, which are labelled with an index number. My headset had index: 2
```
pacmd list-sink-inputs
```
Show software creating an audio stream, also given an index number. Minecraft was index: 16. 

The sink-input entry for Minecraft was flagged with 
"flags: DONT_MOVE START_CORKED FIX_RATE" 

Unsurprisingly when I used ```
pacmd move-sink-input 16 2
``` it returned an error: the audio was tied to one output; that's why Pavucontrol couldn't change it. 

I googled the flag and found [a thread ]("http://steamcommunity.com/app/93200/discussions/0/864959809826195633/") with a fix. Creating a config file at home/[username]/.alsoftrc lets you override that setting: 

```
# ~/.alsoftrc
[pulse]
allow-moves=yes
```

This also made Minecraft respect Pulseaudio's default for me, and now it switches over seamlessly to my speakers if I unplug the headset while it's running. Victory!

---

### Post by peterp772000 on 2014-12-17
Thanks. It solved the problem. Now I can play Minecraft with a USB headset.

---

### Post by Funkey_Pigeon on 2015-08-13
I don't have a folder at home/funkeypigoen/.alsoftrc and when I create one and add a .cfg file it still does nothing

---

### Post by kostkon on 2015-08-14
> **Funkey_Pigeon said:**
> I don't have a folder at home/funkeypigoen/.alsoftrc and when I create one and add a .cfg file it still does nothing
I'm guessing that should be the name of the config file and not a folder, i.e. open/create the file:
```
gedit ~/.alsoftrc
```
and paste the two lines into it.

---

### Post by Funkey_Pigeon on 2015-12-13
> **kostkon said:**
> I'm guessing that should be the name of the config file and not a folder, i.e. open/create the file:
```
gedit ~/.alsoftrc
```
and paste the two lines into it.

Thanks so much! You fixed it :D

---

