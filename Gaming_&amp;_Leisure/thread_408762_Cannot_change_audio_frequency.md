---
title: "Cannot change audio frequency"
date: 2007-04-13
forum: Gaming &amp; Leisure
---

### Post by R%&amp;92GH&amp; on 2007-04-13
Hello

Yesterday I downloaded the linux version of the game (FretsOnFire-1.2.438-linux) and it ran very smoothly (much more than in Vista), but when I began playing a song, I realised that it was out of sync, the audio was faster than the video. In fact, the audio was faster than usual, so I tryed to lower the song frequency and rising the buffer (I also disabled all the graphic effects, just in case), but the song played exactly as fast as before (even if I put the frequency to 8000).

I'm using ubuntu edgy, and my soundcard is an integrated nvidia nforce4 (linux recognises it as NVidia CK804 - IEC958

any1 has any idea? thnx

---

### Post by buttons on 2007-04-13
> **marcpalaus said:**
> Hello

Yesterday I downloaded the linux version of the game (FretsOnFire-1.2.438-linux) and it ran very smoothly (much more than in Vista), but when I began playing a song, I realised that it was out of sync, the audio was faster than the video. In fact, the audio was faster than usual, so I tryed to lower the song frequency and rising the buffer (I also disabled all the graphic effects, just in case), but the song played exactly as fast as before (even if I put the frequency to 8000).

I'm using ubuntu edgy, and my soundcard is an integrated nvidia nforce4 (linux recognises it as NVidia CK804 - IEC958

any1 has any idea? thnx

Tough one.  I find the best way to reduce the lag is the following:
1. Freq 44100 (otherwise the music is higher and lags)
2. Delay 0
3. Buffer 256 (if it's not this low it will not lag at the beginning, but as the song goes on it will lag)

YMMV.  I also find this reduces crashes to once every 1.5 songs or so. :roll:

---

### Post by ViperKnight on 2007-04-14
Check your ".asoundrc" file in your home directory and make sure that "rate" is set to 44100.

I have the same sound card (Realtek ALC850, or Nvidia CK804) and it took ages for me to finally tweak it.  I had the same issues with sounds being choppy first, then playing too fast.  It was because my card was set to 48khz.

My current .asoundrc has Dmix added so I can run multiple ALSA programs at the same time as well as proper 5.1 and Stereo mixing (so that stereo sound is played through all speakers, not just the front).  I also fixed the annoying buffer issues with ALSA with this file :D 

Backup your file and try mine if you want.  (Anybody else with the same sound card...feel free to use it too ;) )

```

###########33
pcm.snd_card {
     type hw
     card 0 # change to your cards number or name
}

# 6 channel dmix:
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false # let multiple users share
        ipc_perm 0660 # IPC permissions (octal, default 0600)
        slave {
                pcm snd_card # see below
                rate 44100
                channels 6
		period_time 0
		period_size 1024
		buffer_time 0
		buffer_size 4096               # in case of skipping, try increasing
        }
     }

# upmixing: 
pcm.ch51dup {
        type route
        slave.pcm dmix6
        slave.channels 6
        ttable.0.0 1
        ttable.1.1 1
        ttable.0.2 1
        ttable.1.3 1
        ttable.0.4 0.5
        ttable.1.4 0.5
        ttable.0.5 0.5
        ttable.1.5 0.5
   }

pcm.duplex {
     type asym
     playback.pcm "ch51dup" # upmix first
#     playback.pcm "dmix6"  # just pass to 6 channel dmix
#     capture.pcm "dsnoop:0" # doesn't work for me
     capture.pcm "snd_card"
}

# change default device:
pcm.!default {
     type plug
     slave.pcm "duplex"
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"

```

---

### Post by R%&amp;92GH&amp; on 2007-04-14
THANK YOU THANK YOU THANK YOU!!

ViperKnight, I used your .asoundrc file instead of mine (it was really simple), and now the songs play at normal speed :-)

Buttons, I already tryed that, but no matter what options i changed, the sound was exactly the same. they had no effects on the game.

btw, viperknight, are you able to control the sound of all speakers together? I can only clone the stereo sound to the back speakers, but if i change the master volume the rear speakers continue to play at the same volume (they're independent). And I cannot use the central speaker and the subwoofer...

---

### Post by ViperKnight on 2007-04-14
I haven't gotten around to assigning all the volume controls to the Master yet.....

Sound should be coming out of the Center and Sub though....
They'll be marked as "Center" and "LFE" in the Alsa mixer.  Also make sure you have them plugged into the right jacks because the ALC850 is actually a 7.1 surround card.  My .asoundrc on works with 5.1.

Here's what settings I have in the Alsa Mixer as well.  I think you may have Surround Jack Mode on shared or maybe the channels setting is only set to 4ch.

Switches Tab (all not mentioned are unchecked):
-Video
-Mix
-Mix Mono
-External Amplifier

Options Tab
Surround Jack Mode: Independent
Mic Select: Mic1
IEC Playback Source: PCM
Mono Output Select: Mix
Channel Mode: 6ch

EDIT: Also make sure you use "default" as your Alsa device in your programs ;)
You probably won't get the channel upmixing in OSS though.  I'm still relatively new to linux and have yet to find/fiddle with the OSS settings :P

---

