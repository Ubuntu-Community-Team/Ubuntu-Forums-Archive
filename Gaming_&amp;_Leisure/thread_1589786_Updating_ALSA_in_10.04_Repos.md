---
title: "Updating ALSA in 10.04 Repos"
date: 2010-10-06
forum: Gaming &amp; Leisure
---

### Post by ngrieb on 2010-10-06
I really don't have any clue where to ask for this, so if I am in the wrong place for posting this please feel free to move it. 

I just wanted to see if there is an ALSA update coming soon for 10.04 because even if I update using an update script found around on the forums every time a new kernel comes out my ALSA updates get knocked. This kills all of my gaming, music, and audio on this laptop unless I recompile all of the ALSA 1.0.23 junk over and over again. So to sum up:

Devs: Are we going to get an update for ALSA in the 10.04 repos soon?
   
Don't get me wrong I appreciate all the work that everyone does and has done. I would gladly help out on this as well myself seeing as at the moment I am free anyways, however, I just do not know where to start.

---

### Post by snowpine on 2010-10-06
You can track the status of a package at packages.ubuntu.com for example [http://packages.ubuntu.com/lucid/alsa-base](http://packages.ubuntu.com/lucid/alsa-base)

Generally speaking, once a version of Ubuntu is released, it gets only minor bug fixes and security patches. If a new version of alsa comes out after April 2010 (that's what 10.04 stands for) then it shows up in a future release, for example [http://packages.ubuntu.com/maverick/alsa-base](http://packages.ubuntu.com/maverick/alsa-base)

Is there a specific problem with alsa 1.0.22?

---

### Post by NightwishFan on 2010-10-06
Try removing what the script does and then run this command:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```

This will install alsa modules from 2.6.34

---

### Post by ngrieb on 2010-10-07
There is a bug with some of the Realtek codecs. I am running a Toshiba A665 which runs very well with the exception of the (ALC 269?) Realtek codec. Without the ALSA 1.0.23 build I cannot get consistent speaker output, mic input, or headphone output. Even with the new build I cannot get any sound via the HDMI cable (although it is recognized at least). I read somewhere that ALSA is a few versions ahead of the upcoming Ubuntu versions (probably for testing) and that some of the hardware is very new hence the lack of support. I have looked for days for a solution and it seems that the only way to get anything working consistently is to update ALSA. 

Is it possible to tap the repos of 10.10 once it comes out? or will that require a full kernel upgrade (or basically a full upgrade)? 

@NightwishFan: Do the backports help for this problem? ^^

---

### Post by NightwishFan on 2010-10-07
They do for me. I have a problem where sound is too quiet and the alsa backports make it work. So it must install a newer alsa. All I know is the modules are from the 2.6.34 kernel. It is easy to uninstall if it does not work. :)

---

### Post by lidex on 2010-10-07
You could try the ppa for alsa on ubuntu. That should automagically keep your alsa-modules up to date for whatever kernel version you're on.
Here's how: Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by snowpine on 2010-10-07
Great tip, NightWishFan! :)

---

### Post by ngrieb on 2010-10-07
Alright, I'll give it try. I'll let you know if it works. Thanks.
Yes, the backports seem to do it. Now if only I could get HDMI sound output working it would be perfect.

---

