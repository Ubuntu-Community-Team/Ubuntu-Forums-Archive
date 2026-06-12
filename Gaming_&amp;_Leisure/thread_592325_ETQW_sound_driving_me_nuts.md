---
title: "ETQW sound driving me nuts"
date: 2007-10-26
forum: Gaming &amp; Leisure
---

### Post by AbyssUK on 2007-10-26
Ok guys I need help now i've tried everything I can find...
Firstly all sound works everywhere xmms/xine etc etc all in 5.1 dvd's play fine
Also Speaker-test -c6 works perfectly

Basically i get this and etqw has no sound :(

```

----- Initializing Sound System ------
sound system initialized.
--------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.14a
opened Alsa PCM device default for playback
buffer size select failed: Invalid argument
close pcm
dlclose
WARNING: sound subsystem disabled

--------------------------------------
----------- Alsa Shutdown ------------
--------------------------------------

```

After reading some forums I have tried to increase my buffer size in my asound.rc file which is

```

pcm.!dmix {
   type dmix
   ipc_key 1024
   slave {
       pcm "hw:0,0"
       channels 6
       period_size 512
       buffer_size 5460
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 6
   route_policy average
}

pcm.doom {
   type plug
   slave.pcm "surround51"
   slave.channels 6
   route_policy average
}


```

The max i can use for my buffer is 5460 any higher and nothing works then, it can't even initiate the driver

Forcing etqw to use the pcm.doom setting which uses the surround51 gives the same error.

Foricing etqw to use OSS does give me very broken slowed down sound..

I get full alsa sound using wine!

I have an built in sound card on my asus motherboard it reports as a nvidia CK804

Any help/ideas considered!! Thanks alot

AbyssUK

edit:- Should mention i am running 7.10 :) and that ETQW does start up and i can play etc just no sound

---

### Post by AbyssUK on 2007-11-06
Still haven't figured this out :( Please help me...

BTW its an AC97 based sound card which i know causes problems in windows.

AbyssUK

---

