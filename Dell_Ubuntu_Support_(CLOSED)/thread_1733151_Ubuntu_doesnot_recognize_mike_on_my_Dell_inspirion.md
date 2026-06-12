---
title: "Ubuntu doesnot recognize mike on my Dell inspirion N4010 laptop"
date: 2011-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dhirajv12 on 2011-04-18
Hi,
I have recently  installed ubuntu 10.04.2 on my dell laptop. While I ma using skype i could see the vedio and can even get the audio out. but the in built mike is not getting recognized on this OS. I even tried sound  recorder but it is not getting recorded as the mike is not detected. I need a solution to this problem, need help guys

Dhiraj

---

### Post by DMGrier on 2011-04-20
you did go into your sound config and turn up the sensitivity with your mic correct? I had to do that on my studio with a similar problem. If that does not work then also go into your sound config and go under the hardware tab and make sure you have your hardware set up to the analog duplex another issue I had when I did not switch it back from hdmi. finally if anything if you are using gnome go under system and look for additional drivers icon and click on that and make sure all your proprietary drivers are installed.

---

### Post by dhirajv12 on 2011-04-22
I have done these things, but ubuntu doesnot recognize the mike yet..... I guess I need necessary drivers for the  mike ........... i normaally upgrade my machine regularly...if I get any drivers i install......need help.....

---

### Post by varunendra on 2011-04-23
Please post back outputs of:
```
sudo lshw -C sound
```
```
dmesg | tail -20
```

Have you tried an external microphone (like a headphone mic)?

Also, try installing gnome-alsamixer from synaptic, open it from 'sound and audio' and see if the mic appears muted there.

---

### Post by dhirajv12 on 2011-04-25
Varun,

Here are the outputs
**dhiraj@dhiraj-laptop:~$ sudo lshw -C sound**
  *-multimedia            
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:f0600000-f0603fff
**dhiraj@dhiraj-laptop:~$ dmesg | tail -20**
[   17.073700] composite sync not supported
[   17.131128] Bluetooth: L2CAP ver 2.14
[   17.131130] Bluetooth: L2CAP socket layer initialized
[   17.212010] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.212013] Bluetooth: BNEP filters: protocol multicast
[   17.278343] Bridge firewalling registered
[   17.383831] Bluetooth: SCO (Voice Link) ver 0.6
[   17.383834] Bluetooth: SCO socket layer initialized
[   17.392830] ppdev: user-space parallel port driver
[   18.136238] Bluetooth: RFCOMM TTY layer initialized
[   18.136242] Bluetooth: RFCOMM socket layer initialized
[   18.136244] Bluetooth: RFCOMM ver 1.11
[   22.068377] composite sync not supported
[   22.205532] composite sync not supported
[   22.342316] composite sync not supported
[   24.815238] eth1: no IPv6 routers present
[   29.214469] composite sync not supported
[   90.343733] fglrxinfo[1896]: segfault at 4 ip 001896d0 sp bfe9035c error 4 in libGL.so.1.2[110000+c9000]
[  530.437360] dell-wmi: Unknown key 3a pressed
[  533.363738] dell-wmi: Unknown key 3a pressed


And varun I have installed gnome-alsa mixer but it has got no mike in it only Beep is mute, and I have not tried with a head phone mike.....I dont have one... I shall try it soon......

---

### Post by varunendra on 2011-05-03
Out of time and ideas right now, sorry.
However, I believe this is related with your HDMI problem in your [other thread]("http://ubuntuforums.org/showthread.php?t=1733145").

Will bump it up in hope someone else may share their valuable ideas..

!! BUMP !!

[B]
PS:[/B]
I think posting the output of alsa-info-script suggested in this thread may provide a better insight into the problem: [http://ubuntuforums.org/showthread.php?t=1741256&highlight=HDMI%2C+ATI](http://ubuntuforums.org/showthread.php?t=1741256&highlight=HDMI%2C+ATI)

---

### Post by Revjohn on 2011-05-03
> **DMGrier said:**
>  make sure you have your hardware set up to the analog duplex another issue I had when I did not switch it back from hdmi. 

Thank you!  This solved my mic issues!

John

---

### Post by lidex on 2011-05-04
Check all the basics first.
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
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

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

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
From ubuntu wiki:
> Changing default subdevice configuration

Some sound devices have multiple capture subdevices (eg. hda-intel), 
but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. 
ALSA may not be configured to use your preferred device as subdevice #0 by default.

Open the pulseaudio record meter (pavumeter --record)
Talk into your chosen device while you carry out the process and watch the meter.
Some channels are quite noisy even with no input (especially on integrated chipsets), 
so we are watching for movements that correspond to our voice. 

Use alsamixer -c n (where n is your sound card number, probably 0)
Press F4 to get to the capture console
Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), 
and the volume turned up.
Check the first input source is switched to your chosen plug (Mic, in my case) 
At this point, you should see the record meter bouncing in response to your voice.
I found that I had to repeat this procedure each time I wanted to use the Mic, 
even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized 
until it was repeated. This also works if you use the "Options" tab in the standard mixer app to do the same thing.

---

