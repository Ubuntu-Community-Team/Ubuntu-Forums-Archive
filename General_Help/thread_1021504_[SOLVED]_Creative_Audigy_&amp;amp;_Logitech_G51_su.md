---
title: "[SOLVED] Creative Audigy &amp;amp; Logitech G51 suround sound problems"
date: 2008-12-25
forum: General Help
---

### Post by rocker9455 on 2008-12-25
Hi,
Just bought some Logitech G51s and hooked them up to my box, only the sub, and the 2 front speakers play, how can i get all of them playing?

Thanks,

Will :)

---

### Post by rocker9455 on 2008-12-26
can i configure pulseaudio or something to output to all of the other 3 speakers?

---

### Post by rocker9455 on 2008-12-31
ive configured pulseaudio (pulseaudio.conf) to output to 6 channels yet it refues to :(

---

### Post by redilyn on 2008-12-31
Hi,

Open your volume control and click preferences.

Make sure the following are checked:

- Front
- Surround
- Center

Then make sure they are turned up. Hopefully that will help.

---

### Post by rocker9455 on 2008-12-31
:( already done that, i turned everything up to the max as soon as i changed it to 6 channels in the config file

---

### Post by redilyn on 2008-12-31
Are you using digital or analoge hookups?

What media player are you using to test sound?

This is just a plain old Audigy right? Not an audigy 2 etc?

---

### Post by rocker9455 on 2008-12-31
um analogue or digital :S not sure about that, how can i find out, i assume digital though

this is the exact soundcard i bought:
[http://www.amazon.co.uk/Creative-Sound-Blaster-Audigy-SE/dp/B000CF0ZXK/ref=sr_1_1?ie=UTF8&s=electronics&qid=1230744665&sr=8-1](http://www.amazon.co.uk/Creative-Sound-Blaster-Audigy-SE/dp/B000CF0ZXK/ref=sr_1_1?ie=UTF8&s=electronics&qid=1230744665&sr=8-1)

Im using rhythmbox to test, although i have tried with vlc, smplayer, amarok and mplayer

---

### Post by redilyn on 2008-12-31
Best guess (I have Audigy ES + Cheaper Logitech 5.1's) if you are using the 3 mini plugs you are using analogue, if you are using just one you probably using digital.

I have found in vlc that changing the audio device to Audigy Multi Channel Playback was necessary for me to get surround sound. Can you try that and see if it helps??

I really don't know much about this stuff, just trying to help since we have similar setups.

I would also try changing to ALSA in System -> Preferences -> Sound just to test.

---

### Post by rocker9455 on 2008-12-31
thanks i changed to alsa in system -> sound etc and tested, still only 2.1 :( how do i change it in vlc?

btw i really appreciate your help :D this is what i love about ubuntu so much, everyone in the community will try and help!

im using analogue

---

### Post by Ahadiel on 2008-12-31
I have a Creative Audigy SE and I managed to get 7.1 working by disabling hal-autodetection of devices, and manually specifying my sources/sinks in /etc/pulse/default.pa

If you could paste your /etc/pulse/default.pa and the output of 'aplay -L' I could make the modifications for you.

---

### Post by redilyn on 2008-12-31
I hear ya, If it wasn't for the community I probably would never have made the switch.

Okay, Open vlc and do the following:

- Open tools -> Preferences
- In the bottom left, change Show Settings from simple to all
- Expand Audio
- Choose Output Modules and choose ALSA
- Expand Output Modules and click on ALSA
- For ALSA device name choose Audigy Multi Channel Playback

*Note, it isn't actually called Multi Channel Playback but I'm not at home so I can't check the actual name. I'm sure you can probably pick out the right one from the list though :)

btw, Incase yours is different, did you also check to make sure PCM Front, PCM Surround etc was also turned up if you have those options?

---

### Post by rocker9455 on 2008-12-31
etc/pulse/default.pa
```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

aplay -L
```
default:CARD=SI7012
    SiS SI7012, SiS SI7012
    Default Audio Device
front:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    Front speakers
surround40:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=SI7012,DEV=0
    SiS SI7012, SiS SI7012
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=CA0106
    CA0106, CA0106
    Default Audio Device
front:CARD=CA0106,DEV=0
    CA0106, CA0106
    Front speakers
surround40:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=CA0106,DEV=0
    CA0106, CA0106
    IEC958 (S/PDIF) Digital Audio Output

```

---

### Post by Ahadiel on 2008-12-31
Okay, here it is
```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

load-module module-alsa-sink device=surround51:1

### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

---

### Post by rocker9455 on 2008-12-31
thanks Ahadiel il just reboot in a sec and try that out :)

redilyn - um im not sure which to choose, and thanks for the reply

il attach a screenshot as im a bit bewildered 

[[IMG]http://img50.imageshack.us/img50/1391/screenshottn7.th.png[/IMG]](http://img50.imageshack.us/my.php?image=screenshottn7.png)

---

### Post by Ahadiel on 2008-12-31
You should have something like this (except with surround51) afterwards.

[http://omploader.org/vMTJ0aA](http://omploader.org/vMTJ0aA)

---

### Post by rocker9455 on 2008-12-31
ARGHHHH still doesnt work :(

Edit: im sure the soundcard is fine because in winxp i can get 5.1 surround sound fine

---

### Post by Ahadiel on 2008-12-31
```
sudo apt-get install padevchooser
```
Then Alt+F2 and run "padevchooser". Left-click the icon that appears in your tray and go to Volume Control. Click the "Output Devices" tab and tell me what it shows.

Also you may want to try forcing everything to use pulseaudio through System => Prefs => Sound.

And lastly,
```
alsamixer
```
^ Pulse Audio ^
```
alsamixer -c 1
```
^ Creative Audigy ^

---

### Post by rocker9455 on 2008-12-31
[[IMG]http://img380.imageshack.us/img380/8325/screenshot1em4.th.png[/IMG]](http://img380.imageshack.us/my.php?image=screenshot1em4.png)

(was just in the process of uploading it when you replied hehe)

---

### Post by Ahadiel on 2008-12-31
Is CA0106 muted? The screenshot is kinda iffy. Have you tried playing music with something other than vlc? Totem?

---

### Post by rocker9455 on 2008-12-31
THANK YOU SO MUCH! i was pondering whether to switch back to windows, thank god i didnt 

"alsamixer -c 1" sorted it for me i just put the volume up :D

[[IMG]http://img247.imageshack.us/img247/9215/screenshot2hj6.th.png[/IMG]](http://img247.imageshack.us/my.php?image=screenshot2hj6.png)

---

### Post by Ahadiel on 2008-12-31
/me points towards the thanks button.

---

### Post by rocker9455 on 2008-12-31
hehe done!

---

### Post by Ahadiel on 2008-12-31
Thanks, and glad to see you got it working. It took me a while to figure out how to enable surround sound the first time -_-

---

