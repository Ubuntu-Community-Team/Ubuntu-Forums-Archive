---
title: "XPS M1530 internal mic not working"
date: 2011-01-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bloodorange on 2011-01-04
Can anyone help?  Since installing Maverick, I can't get the internal microphone on my XPS M1530 to work.  I've tried 32-bit and 64-bit, and neither work.

Earlier in the year, with Lucid installed, the microphone was definitely working.  I know for sure because I used Skype whilst on holiday.  However, I've tried Lucid again this last week and my microphone doesn't work even with that installed.  I realise the microphone could be broken, but I would be surprised if it is, and I don't really want to install Windows just to find out!

I suppose I at least just want to know if anyone else with the same laptop is having the same problem.

---

### Post by lidex on 2011-01-05
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

No help? Provide some more info please. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by bloodorange on 2011-01-05
Thanks very much for your help and advice, lidex.  I tried all your suggestions, but it doesn't seem to have worked.  It seems to me that the internal microphone hasn't been recognised at all by Ubuntu.  I'm pretty sure I remember that, in previous versions (when the mic worked), the microphone was listed as Digital, but there is no such listing in Sound Preferences, or even gnome-alsamixer.  Although, Digital input does show up in alsamixer.

In Sound Preferences, the input options are 'Microphone 1/Microphone'; 'Microphone 1/Line-In'; 'Microphone 2/Microphone'; 'Microphone 2/Line-In'; 'Microphone 3/Microphone'; 'Microphone 3/Line-In'.  The only one that works is 'Microphone 2/Microphone', which turns out to be the external microphone input on the front of my laptop. As far as physical inputs go, my laptop has one microphone input and two headphone inputs, all of which work fine.

I've run the alsa-info-script as you instructed, and the result is here: [http://www.alsa-project.org/db/?f=49d27568c043186df7bca0ab709bd9d4808d6b1d](http://www.alsa-project.org/db/?f=49d27568c043186df7bca0ab709bd9d4808d6b1d)

---

### Post by lidex on 2011-01-05
I think you need to tweak these mixer settings:
```
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%] [21.00dB] [off]
  Front Right: Capture 14 [100%] [21.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%] [21.00dB] [off]
  Front Right: Capture 14 [100%] [21.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Digital Mic'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Digital Mic'
  Item0: 'Digital Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Digital Mic'
  Item0: 'Digital Mic'
```

This may help:
[http://ubuntuforums.org/showpost.php?p=9016631&postcount=2](http://ubuntuforums.org/showpost.php?p=9016631&postcount=2)

---

### Post by bloodorange on 2011-01-06
OK, I'll have a go.  Thanks again.

Cheers

---

### Post by kayris on 2011-01-06
I had the same problem with my m1210 until recently. If you go to System> Preferences> Sound> Input - then click on your internal input device. Next, to the right of the "Input volume" slider-bar, is the mute button checked? A silly question, I know, but I seriously tooled with this forever and /facepalmed when I unchecked it and it worked. I had just never noticed it before.

---

### Post by bloodorange on 2011-01-07
Thanks for your reply, kayris.  I've double-checked all my inputs, though, and none of them are muted, unfortunately.

---

