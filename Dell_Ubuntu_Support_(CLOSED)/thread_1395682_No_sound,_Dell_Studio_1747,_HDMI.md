---
title: "No sound, Dell Studio 1747, HDMI"
date: 2010-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by merry_meerkat on 2010-02-01
[UPDATE: solved, [see post #7 below for solution]("http://ubuntuforums.org/showpost.php?p=8765582&postcount=7"). In fact, contrary to the title of this thread, it doesn't seem to have anything to do with HDMI]

Hello,
I'm having very little luck in getting sounds/audio to work on my new computer. Any help would be greatly appreciated! It's a new **Dell Studio 1747** with an ATI Mobility Radeon HD 4650 graphics card and what Dell calls "High Definition Audio 2.0". As far as I understand the sound is also somehow from AMD/ATI. The problem is that it is making no sound whatsoever. No system sounds, no WAV or OGG playback, etc. The computer seems to think that everything is working fine, i.e. audio files will play (e.g. in Totem, or by typing *aplay -D plughw:1,3 tada.wav*) - but everything stays silent. I assume that it has something to do with having the right settings for HDMI audio.

Here's some more information in the hope that it helps to identify the problem:

```
lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
02:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
cat /proc/asound/card0/codec#0 | grep Codec
Codec: IDT 92HD73C1X5
```

```
grep options /etc/modprobe.d/alsa-base.conf

options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-pcsp index=-2
options snd-hda-intel power_save=10 power_save_controller=N
```


```
lspci -v

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Dell Device 02eb
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0c00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
	Subsystem: Dell Device 02eb
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at cfeec000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Vendor Specific Information <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```


Other details:
OS: Ubuntu 9.10 Karmic Koala (dual-boot with Win 7 Home Pro)
Kernel: 2.6.31-17-generic
Gnome: 2.28.1
Alsa: 1.0.20
Pulseaudio: 0.9.19

Dell Studio 1747 - BIOS version A05

I've downloaded and installed the latest ATI Catalyst proprietary driver from here [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English)
...more about the computer here: [http://www.laptopmag.com/review/laptops/dell-studio-17-core-i7.aspx?mode=specs](http://www.laptopmag.com/review/laptops/dell-studio-17-core-i7.aspx?mode=specs)

[SIZE="4"]Any help greatly appreciated!!
Thanks![/SIZE]


PS: Another thing I've noticed is that every minute or so I hear a tiny popping sound (similar to when you turn plug speakers into a soundsystem, but MUCH less audible) and the fans turn themselves on for about 5 seconds. This may be entirely unrelated, though. I can't tell whether that sound is coming from the speakers as it is really very quiet.

---

### Post by merry_meerkat on 2010-02-01
Oh, hot on the heels of my first post, an update. I've managed to get *just a little* sound out of the machine!

I added ***options snd-hda-intel model=dell-m6*** to **/etc/modprobe.d/alsa-base.conf**.
(tip from here [http://www.rschulz.eu/2009/11/dell-studio-1557-core-i7-with-kubuntu.html](http://www.rschulz.eu/2009/11/dell-studio-1557-core-i7-with-kubuntu.html))

As a result the system-ready sound is playing perfectly! I.e. the little bongo-drum-roll when the login screen appears.

But as soon as I login - again: no sound :(

Any ideas?

---

### Post by tr33m4n on 2010-02-01
Im using the same chipset as you, and from what I can see it looks like your sound output in gnome is using the ATI output, which is for the sound on the HDMI output of your system. If you go to sound preferences in gnome and select internal audio, does that work?

---

### Post by merry_meerkat on 2010-02-01
> **tr33m4n said:**
> Im using the same chipset as you, and from what I can see it looks like your sound output in gnome is using the ATI output, which is for the sound on the HDMI output of your system. If you go to sound preferences in gnome and select internal audio, does that work?

Thanks for the suggestion. Could you tell me how I would do that?

Please see the attached screenshot. I don't seem to have another option than the HDMI device. Or am I missing something?

Thanks again.

---

### Post by tr33m4n on 2010-02-01
Hmm, I think something might be missing, not sure what though. Have u tried just a general update through apt? I've attached a screenshot of what appears in my output

---

### Post by tr33m4n on 2010-02-01
Actually, just comparing the specs, u have different sound hardware to mine (my laptop is the older 1735)... however this post should help [http://forum.notebookreview.com/showthread.php?t=420136]("http://forum.notebookreview.com/showthread.php?t=420136")

cheers

---

### Post by merry_meerkat on 2010-02-02
> **tr33m4n said:**
> however this post should help [http://forum.notebookreview.com/showthread.php?t=420136]("http://forum.notebookreview.com/showthread.php?t=420136")

Awesome! Yes, I found the solution via that post. Thanks!

First of all, in the sound preferences/hardware tab I had to select "Internal Audio" under "choose a device to configure" and set it to "Analog Stereo Duplex"... only then would it let me to select it in the output tab. Before, as posted above, it wouldn't appear in that list.

Then, and more importantly, I had to modify the alsa-base.conf file. The relevant part is to add these lines to the end of the /etc/modprobe.d/alsa-base.conf file:
```
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m6
options snd-hda-intel enable_msi=1
```

The full reference for this is: [https://answers.launchpad.net/ubuntu/+question/75137](https://answers.launchpad.net/ubuntu/+question/75137)

Thanks again! Sound is working great. :guitar:

---

### Post by sssthegreat on 2010-03-16
Thanks a lot. :)
Carried out the same steps. Works fine. Thanks again. Mine is a Dell Studio 1558 with HDMI.

---

### Post by merry_meerkat on 2010-07-29
Just a quick update after having installed Lucid Lynx:
Most things worked out of the box, only the sound would not play through headphones. I.e. plugging in headphones would mute the speakers but no sound would come through the headphones.

That was easily solved by adding the following line to **/etc/modprobe.d/alsa-base.conf**
```
options snd-hda-intel model=dell-m6
```

That's all.

(Dell Studio 1747 with Ubuntu 10.4 Lucid Lynx 64-bit)

---

