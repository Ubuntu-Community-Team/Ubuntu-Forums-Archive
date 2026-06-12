---
title: "Torcs/SuperTuxKart/Random other games sound issues"
date: 2009-11-11
forum: Gaming &amp; Leisure
---

### Post by RabidWeezle on 2009-11-11
The sound pops on those games. From what it looks like, it seems at random times they have issues connecting to the pulseaudio server or something. I setup openal (what torcs uses) to use pulseaudio, The sound might work for a second, and then sound like fuzz, the console spits out:

bt_audio_service_open: connect() failed: Connection refused (111) 

This laptop uses: HDA NVIDIA CONEXANT audio chipset, I haven't removed pulseaudio or anything strange like that. 

CPU: AMD Athlon X2 64
uname -r: 2.6.31-14-generic
Ubuntu Karmic AMD64
4 gigs of ram
4 gig swap
ext4/non-encrypted

And yes, I have googled/forum searched for these issues before asking.

---

### Post by lessmemorelove on 2009-11-14
i copied this from another thread response trying to make sure the word gets out. hopefully this will help people as i know i was bothered by this since karmic came out.

i was having sound issues in these games with karmic, too. i found the solution that works for me. it allows dosbox, wine, and openal games to all play nice. this idea has been taken from other places on the forums and cobbled together.

1. edit /etc/default/pulseaudio as root and change PULSEAUDIO_SYSTEM_START=0 to PULSEAUDIO_SYSTEM_START=1

2.  add your user name to the pulse audio family with this command in terminal:

sudo adduser $user pulse-access

substitute your user name in for $user

3. edit /ect/openal/alsoft.conf as root add the following line under the lines talking about drivers

drivers = oss

4. use synaptic and make sure you have libsdl1.2debian-pulseaudio installed

5. reboot

you should be good to go

---

### Post by RabidWeezle on 2009-11-17
> **lessmemorelove said:**
> i copied this from another thread response trying to make sure the word gets out. hopefully this will help people as i know i was bothered by this since karmic came out.

i was having sound issues in these games with karmic, too. i found the solution that works for me. it allows dosbox, wine, and openal games to all play nice. this idea has been taken from other places on the forums and cobbled together.

1. edit /etc/default/pulseaudio as root and change PULSEAUDIO_SYSTEM_START=0 to PULSEAUDIO_SYSTEM_START=1

2.  add your user name to the pulse audio family with this command in terminal:

sudo adduser $user pulse-access

substitute your user name in for $user

3. edit /ect/openal/alsoft.conf as root add the following line under the lines talking about drivers

drivers = oss

4. use synaptic and make sure you have libsdl1.2debian-pulseaudio installed

5. reboot

you should be good to go

hrm, after doing that, now I have no sound at all with stuff like flash, quake wars, audacious, vlc, etc. But I do have sound only with stuff that uses openal o_O

---

### Post by lessmemorelove on 2009-11-18
change PULSEAUDIO_SYSTEM_START=1 back to PULSEAUDIO_SYSTEM_START=0 but leave everything else alone and you should be ok then. weird how some people need pulse as a daemon and others cant have it that way.

---

### Post by lessmemorelove on 2009-11-25
solved?

---

### Post by matmota on 2009-12-10
I too had this problem trying to run Torcs, and it was solved by adding myself to the pulse-access group and setting the OpenAL driver to OSS as you said.
I tried setting "drivers=pulse" for OpenAL but Torcs hanged up when starting the race and I had to switch to a virtual terminal and kill it. Setting "drivers=alsa,oss" apparently used alsa and gave me the same broken sound as before.

I did not need to change PulseAudio's configuration from the default, which in my case was PULSEAUDIO_SYSTEM_START=0

This is in a ThinkPad W500, with Ubuntu 9.10 updated from 9.04.

---

### Post by bilalakhtar on 2010-02-03
> Re: Torcs/SuperTuxKart/Random other games sound issues
i copied this from another thread response trying to make sure the word gets out. hopefully this will help people as i know i was bothered by this since karmic came out.

i was having sound issues in these games with karmic, too. i found the solution that works for me. it allows dosbox, wine, and openal games to all play nice. this idea has been taken from other places on the forums and cobbled together.

1. edit /etc/default/pulseaudio as root and change PULSEAUDIO_SYSTEM_START=0 to PULSEAUDIO_SYSTEM_START=1

2. add your user name to the pulse audio family with this command in terminal:

sudo adduser $user pulse-access

substitute your user name in for $user

3. edit /ect/openal/alsoft.conf as root add the following line under the lines talking about drivers

drivers = oss

4. use synaptic and make sure you have libsdl1.2debian-pulseaudio installed

5. reboot

you should be good to go 
Brilliant, You are a genius! The problem is solved for me!
I didnt have to set PULSEAUDIO_SYSTEM_START to 1 , I left it at its default 0. I followed the rest of the steps and no more sound issues!

---

