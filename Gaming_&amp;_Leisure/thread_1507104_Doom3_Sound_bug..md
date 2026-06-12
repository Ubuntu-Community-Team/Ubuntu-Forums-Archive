---
title: "Doom3 Sound bug."
date: 2010-06-11
forum: Gaming &amp; Leisure
---

### Post by Gosujii-sama on 2010-06-11
I've looked around for a solution no luck or I'm not looking in the right places. The bug is basically this. While running doom3 using the install bash files n such I have no issues or with the actual game play. The issue arrives when sound is attempting to play. Walking around I'll get a delay before the foot steps start and then they will "catch up" after I'm done walking. All sound seems delayed from when the sound was queued. Shots running walking jumping monsters sound files pda even menu clicks.

Running: Ubuntu 10.04 LTS - Lucid Lynx
Card: nVidia GeForce

I realize it's not my card due to I've run Doom 3 from this very same pc with ubuntu before however that was 9.10 I believe was last one I had it loaded and working. So either I missed something in system or it's bugged from the upgrade. Plz helpz I friggin love Doom. :)

-EDIT
Forgot to mention I have issues other than this with the alsa sound server and not just this install. For example running a sound program in wine such as a game and trying to run an outside sound source (not the default rhythm box) such as a web sound will kill sound in one but not the other.

Full details straight from the Doom3:

> 
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.22
opened Alsa PCM device default for playback
device buffer size: 5461 frames ( 65532 bytes )
allocated a mix buffer of 49152 bytes


And here's where I believe the bug comes in:
> 
idAudioHardwareALSA::Write: 10 frames overflowed and dropped
idAudioHardwareALSA::Write: 51 frames overflowed and dropped
idAudioHardwareALSA::Write: 35 frames overflowed and dropped
idAudioHardwareALSA::Write: 9 frames overflowed and dropped
idAudioHardwareALSA::Write: 61 frames overflowed and dropped
idAudioHardwareALSA::Write: 45 frames overflowed and dropped
idAudioHardwareALSA::Write: 96 frames overflowed and dropped

Well it's not always giving write errors so I'm clueless. It doesn't seem to give any spicific bug for this issue... I'm assuming it has something to do with any changes made in the alsa between 9.10 to 10.04

Might be unrelated but the alsa restart and force restart still insist SOMETHING is using them even though everything's shut off.
> 
 (failed: processes still using sound devices: 2499(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/**********/.gvfs

Also refuses to let me end it to restart.

---

### Post by rlarrowe on 2010-06-14
use:

pasuspener -s=alsa -- <the program you want to run>

there will be a delay before it starts but after .. no sound delay

---

### Post by FireDemonSiC on 2010-08-27
> **rlarrowe said:**
> use:

pasuspener -s=alsa -- <the program you want to run>

there will be a delay before it starts but after .. no sound delay

I am having the same issue.

The above solution did not work :(

---

### Post by Cresho on 2010-08-27
gedit ~/.pulse/client.conf
and add "autospawn = no" without quotes

then

system->preferences->startup applications add
title:   pulseaudio start
command: pulseaudio


then in the game script.

 
#!/bin/bash
sleep 2 &&
pulseaudio -k
cd /whereeveritis/doom3/
./doom3
sleep 2 && pulseaudio



if you want to do away with pulseaudio destroying your audio all the time, do this as a permanent solution and no need to modify scripts all the time




  #alsamixer and fix audio
gedit ~/.pulse/client.conf
and add "autospawn = no" without quotes

then

system->preferences->startup applications add
pulseaudio killer
pulseaudio -k


use alsamixer to adjust volume


add pulseaudio command at startup applications

#gnome-terminal -e alsamixer

---

### Post by bigseb on 2010-08-30
> **Cresho said:**
> gedit ~/.pulse/client.conf
and add "autospawn = no" without quotes

then

system->preferences->startup applications add
title:   pulseaudio start
command: pulseaudio


then in the game script.

 
#!/bin/bash
sleep 2 &&
pulseaudio -k
cd /whereeveritis/doom3/
./doom3
sleep 2 && pulseaudio



if you want to do away with pulseaudio destroying your audio all the time, do this as a permanent solution and no need to modify scripts all the time




  #alsamixer and fix audio
gedit ~/.pulse/client.conf
and add "autospawn = no" without quotes

then

system->preferences->startup applications add
pulseaudio killer
pulseaudio -k


use alsamixer to adjust volume


add pulseaudio command at startup applications

#gnome-terminal -e alsamixer


Very interesting. What exactly is pulse audio, is it necessary?

---

