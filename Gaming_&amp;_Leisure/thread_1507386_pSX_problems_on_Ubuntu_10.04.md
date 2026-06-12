---
title: "pSX problems on Ubuntu 10.04"
date: 2010-06-11
forum: Gaming &amp; Leisure
---

### Post by japzone on 2010-06-11
I have old PS1 games lying around my house and a few years ago decided to go Emulator on my laptop. I've tried all the emulators for Linux/Ubuntu and pSX always worked best. It was annoying that I had to kill PulseAudio whenever I wanted to use it but that was fine. However I recently had to upgrade to 10.04 due to problems in my old Installation of Ubuntu. I went and installed pSX and it's needed libraries but when I went to run it it crashes. I get to the part where it can't find the BIOs file (That's Normal) I select my BIOs file and it Crashes. I get a brief flicker of the window then nothing. I ran it through Terminal and got a weird error I've never seen or heard of before. To narrow down possible causes I ran pSX with and without the special PulseaudioKill/Unkill Script that's usually needed, and I get a similar error either way. I can't figure out what's wrong. I'll post the Output of both tries below and the Script to see if you can help me. Any advice is Appreciated.

**PulseAudio Kill/Unkill Script:**
Note: I attached the Script below as well.
```
#!/bin/bash
# A script to disable pulseaudio, run pSX, then renable pulseaudio

gksu /etc/init.d/pulseaudio stop
sleep 1
gksu killall pulseaudio # Forcefully ends pulseaudio if still running
sleep 1
exec ~/pSX/pSX
sleep 1
gksu /etc/init.d/pulseaudio start
```[B]Running pSX without Script:
[/B]Note: I'm Running pSX from my Home Directory
```
user@ubuntu:~$ pSX/pSX

(pSX:3790): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3790): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3790): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3790): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3790): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3790): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3790): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3790): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
```[B]Running pSX with Script:
[/B]Note: I'm Running pSX from my Home Directory
```
user@ubuntu:~$ pSX/pSX.sh
 [COLOR=Orange]*[/COLOR] PulseAudio configured for per-user sessions

(pSX:3811): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3811): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3811): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3811): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3811): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3811): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:3811): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:3811): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
```Again I am still unsure of what exactly is the cause so any help would be appreciated.

PS: Some of you may tell me to go post this on pSX's forums but I can't. pSX's Forums now require Moderator approval in order to SignUp (as I never needed one before, and who knows how long until I get approved) and the forum isn't very active recently so I don't know when if ever I'd get an answer.

---

### Post by dfreer on 2010-06-11
Maybe give this a try:
```
sudo aptitude install libgtkglext1 libgtkglext1-dev
echo "autospawn = no" > /etc/pulse/client.conf
pkill pulseaudio
./pSX
```

Another error that occurs due to sound is that pSX doesn't always pick up the device ID for the sound card correctly, and then crashes when it can't output audio. Some have reported success with running pSX as the root user (not normally recommended but fine for first time config), and then copying the relevant portions of the psx.ini file from the root's home directory into the user's ~/.pSX/psx.ini file.

But IDK, honestly it's such a freaking pain to get pSX working. Seems like it breaks in a brand new way with every release. Maybe try a debian live CD or an old Ubuntu CD that it's known to work on, and grab the psx.ini file from that.

[http://ubuntuforums.org/showpost.php?p=7953652&postcount=299](http://ubuntuforums.org/showpost.php?p=7953652&postcount=299)
[http://ubuntuforums.org/showpost.php?p=7282494&postcount=8](http://ubuntuforums.org/showpost.php?p=7282494&postcount=8)

---

### Post by disturbedite on 2010-06-12
> **dfreer said:**
> But IDK, honestly it's such a freaking pain to get pSX working. Seems like it breaks in a brand new way with every release. Maybe try a debian live CD or an old Ubuntu CD that it's known to work on, and grab the psx.ini file from that.

or maybe try a different distro. you're right: these pulseaudio problems are always reported when a new version of ubuntu is released. however, on the distro i use, opensuse, there have never been problems. as a matter of fact i've seen it discussed that these are ubuntu-centric problems (with pulseaudio) that don't occur with opensuse. (for whatever reason(s)).

---

### Post by test540va on 2010-07-04
Yes I agree pSX doesn't work with Ubuntu 10.04... or not in a way that ManKind knows about.  So.... Does anyone know of a PlayStation1 emulator that Does work in Ubuntu 10.04 (Lucid Lynx) ? ??  ?  and if you do, please in easy to understand steps tell me how you did it ?!?!?!?

---

### Post by hikaricore on 2010-07-04
Pretty much every emu save for the pcsx forks has suffered a development death..
I still use epsxe on my 10.04 system and it works perfectly fine.

---

### Post by japzone on 2010-07-04
I know it's not a Pulseaudio problem because I'm using the special Script that fixes that. So it has to be something else in 10.04. No I'm not installing another Distro, I like Ubuntu and I don't have space on my Laptop to install another OS.

---

### Post by dfreer on 2010-07-04
> **japzone said:**
> I know it's not a Pulseaudio problem because I'm using the special Script that fixes that. So it has to be something else in 10.04. No I'm not installing another Distro, I like Ubuntu and I don't have space on my Laptop to install another OS.

I wouldn't be surprised if that script doesn't stop pulseaudio, IIRC it came from my pSX thread back in '08-'09 and doesn't actually stop it anymore. Check your system monitor and make sure nothing pulseaudio related is running.

---

### Post by TempleNav on 2010-07-10
> **hikaricore said:**
> Pretty much every emu save for the pcsx forks has suffered a development death..
I still use epsxe on my 10.04 system and it works perfectly fine.
 You were able to get Epsxe to run in Ubuntu nativley? I have had some trouble   getting it to work. I keep getting errors when I try to configure the video or the audio plugins in the GUI. The other config settings work fine... I think its a GL table error...

---

### Post by LibertyZero on 2010-07-22
pSX works perfectly well in Ubuntu 10.04! However, when using the prop.  ati graphics drivers (at least catalyst 10.6) the program segfaults. The  open drivers and the prop. nvidia drivers seem not to be effected by  this.

---

### Post by japzone on 2010-07-23
Is there any way to change drivers? I've never needed to change drivers so I haven't looked into it.

---

### Post by lee321987 on 2010-11-07
I got PSX to start inside a virtual machine (VM), by doing this:
System > Administration > System Monitor [Processes tab]
Right-click "pulseaudio" > Stop Process     ---  (I tried to kill it, but it just instantly restarts)

Then run PSX...
File > Configuration [sound tab] > chose a device.

Now I can run PSX without messing with pulseaudio.

Maybe I didn't have to chose a sound device (just run it once, and exit...?).

It's running REALLY slow and choppy video/sound, with this message  "sound: underrun" repeating in the terminal, but I got a game to start.   I don't know how different it would be outside a VM.

P.S. Sound isn't choppy if i turn the latency really high.

---

### Post by thatguruguy on 2010-11-08
pcsx-r. Really.

---

### Post by japzone on 2010-11-08
> **thatguruguy said:**
> pcsx-r. Really.
What does that do?

---

### Post by japzone on 2010-11-08
> **lee321987 said:**
> I got PSX to start inside a virtual machine (VM), by doing this:
System > Administration > System Monitor [Processes tab]
Right-click "pulseaudio" > Stop Process     ---  (I tried to kill it, but it just instantly restarts)

Then run PSX...
File > Configuration [sound tab] > chose a device.

Now I can run PSX without messing with pulseaudio.

Maybe I didn't have to chose a sound device (just run it once, and exit...?).

It's running REALLY slow and choppy video/sound, with this message  "sound: underrun" repeating in the terminal, but I got a game to start.   I don't know how different it would be outside a VM.

P.S. Sound isn't choppy if i turn the latency really high.

I'll look into it later. Just to clarify, what version of Ubuntu are you using. The Version I'm having problems in is 10.04.

---

### Post by elricscripts on 2010-12-19
> **thatguruguy said:**
> pcsx-r. Really.

Thank you Thank you!!!

---

### Post by thatguruguy on 2010-12-19
Happy to help.

---

