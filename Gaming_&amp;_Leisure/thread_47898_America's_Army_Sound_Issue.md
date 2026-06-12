---
title: "America's Army Sound Issue"
date: 2005-07-10
forum: Gaming &amp; Leisure
---

### Post by Sephiriz on 2005-07-10
I recently installed America's Army and the sound worked just fine.  This was when I was using my onboard sound.  Yesterday I switched to my sound card, a Sound Blaster Audigy, and I spent the whole day attempting to configure Ubuntu to work with it.

As a result, I have the following sound-related packages installed on Ubuntu:

alsa-base 1.0.8-4ubuntu
alsa-oss 1.0.7-1
libesd-alsa0 0.2.35-2ubuntu2
libopenal0 0.2004090900-1.1

I have the system configured to use ALSA via this little configuration file I picked up in these forums:
```

pcm.card0 {
  type hw
  card 1
# mmap_emulation true
}

#pcm.dmix0 {
#  type dmix 
#  ipc_key 34521 
#  slave {
#    pcm "card1" 
#  }
#}


pcm.dmix0 {
	type dmix
	ipc_key 1024 ## needs to be a power of 2
	slave {
		pcm "hw:1"
		period_time 0
		period_size 1024
		buffer_size 8192
               # format S16_LE
		rate 44100 ## not necessary
	}
#slowptr true
}





pcm.dsnoop0 {
  type dsnoop 
  ipc_key 2048
  slave {
    pcm "card1" 
  #  rate 48000
  }
}

pcm.asym0 {
  type asym 
  playback.pcm "dmix0" 
  capture.pcm "dsnoop0"
}

pcm.pasym0 {
  type plug 
  slave.pcm "asym0"
}

# 'dsp0' is expected by OSS emulation etc.
pcm.dsp0 {
  type                  plug
  slave.pcm             "asym0"
}

ctl.dsp0 {
    type                hw
    card                1
}

pcm.!default {
  type                  plug
  slave.pcm             "asym0"
}

ctl.!default {
    type                hw
    card                1
}


``` 

Now, as I said previously, America's Army won't output sound.  Someone told me it had to do with ALSA and OpenAL not working together, and that the solution was to make a file called ".openalrc" in either the home directory or "openalrc" in the /etc/ directory.  So I made /etc/openalrc and put in the following:

```
 
(define devices '(alsa))
(define alsa-out-device "hw:1")
(define alsa-in-device "hw:1")
(define speaker-num 2) 

``` 

I don't know if this does anything or not, since no difference came up with America's Army.  I'm really stumped, can anyone help me out here?  If you guys need additional information, I'll be more than happy to provide it, since this fix should help in the future, because OpenAL is apparently used in a lot of games.

---

### Post by Sephiriz on 2005-07-10
Alright well I managed to fix it up on my own.  The solution was rather simple, and I'm just writing this so that if anybody else ever stumbles across this problem, be sure to do the following:

If anybody here is using ALSA, realize that there are sound emulators.  For whatever reason, my sound emulation modules were not starting automatically, so I manually added it to my /etc/modules file.  The instructions to do this were taken from [http://www.ubuntuforums.org/showthread.php?t=21211&highlight=snd](http://www.ubuntuforums.org/showthread.php?t=21211&highlight=snd)

I extrapolated the following:

> 
sudo nano /etc/modules
add in

snd-pcm-oss
snd-emu10k1
snd-mixer-oss
 

After a reboot, sound worked for America's Army (and on the side, Wolfenstein: Enemy Territory).  I guess that AA uses OSS maybe?  Not quite sure, but this did it.

At the same time, Enemy Territory wasn't working, and in addition to this, I had to edit the configuration for it and pointed the sound from /dev/dsp to /dev/dsp0, since according to my ALSA config, thats the entry.

Hope this will help someone out.  And if anyone is reading this, don't you think its ironic that this was necessary when Ubuntu is trying to appeal to those new to Linux?  Oh well, I still love Ubuntu!

---

