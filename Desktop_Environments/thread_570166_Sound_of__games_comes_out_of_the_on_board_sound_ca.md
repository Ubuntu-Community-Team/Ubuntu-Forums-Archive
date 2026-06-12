---
title: "Sound of  games comes out of the on board sound card"
date: 2007-10-07
forum: Desktop Environments
---

### Post by neofreak on 2007-10-07
every time I try to play quake3, unreal tournament or unreal tournament 2004 the sound output comes out of the onboard sound card instead of my sb live!, which works fine for everything else.
I'd like to know how I can fix this, and also, if possible, how to disable altogether the on board sound card. the bios setting which completely disabled it in windows since I last had it is still off.

some information:
```

god@magi:~$ sudo asoundconf list
Password:
Names of available sound cards:
V8237
Live
god@magi:~$ sudo asoundconf set-default-card Live
god@magi:~$ sudo asoundconf list
Names of available sound cards:
V8237
Live
```

also:
```

god@magi:~$ cat .asoundrc
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/god/.asoundrc.asoundconf>
```

```
god@magi:~$ cat .asoundrc.asoundconf 
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card Live
defaults.ctl.card Live
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix_max_periods 0
defaults.pcm.dmix_rate 48000
defaults.pcm.dmix_format S16
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
```

please help! :)

---

### Post by Jouke74 on 2007-10-08
Under the mixer settings, there should also be preferred device. Switch that one to the Live instead of the non-selected standard.

---

### Post by neofreak on 2007-10-08
yes, that's already done, otherwise I wouldn't have sound anywhere and I do playing music, movies, etc. the problem is just with these games. it's a bit deeper than the mixer settings, unfortunely :(

thanks.

---

