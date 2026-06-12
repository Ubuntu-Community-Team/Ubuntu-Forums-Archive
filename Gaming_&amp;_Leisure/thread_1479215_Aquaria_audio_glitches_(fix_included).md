---
title: "Aquaria audio glitches (fix included)"
date: 2010-05-10
forum: Gaming &amp; Leisure
---

### Post by Kevinator on 2010-05-10
I was having this issue with Aquaria from the Humble Indie Bundle. The sound would work fine at first, but before long it would begin clicking.  It's an irregular rapid click, at a rate of maybe 2 clicks per second.  Once it starts it never goes away until I exit the game.

When running from the console, an error about ALSA underrun is printed (I'll add the exact error message later, I'm not posting from home). I think this is some kind of failure to recover from a buffer underrun, so once an underrun occurs the noise begins and continues indefinitely.

To work around this, I force it to use the version of the OpenAL library that is installed on the system rather than the version packaged with the game. The work-around looks like this:

LD_PRELOAD=/usr/lib/libopenal.so ./aquaria

This seems to work perfectly. My guess is that the Debian/Ubuntu version of OpenAL fixes some upstream issue that's present in the version distributed with Aquaria.

I don't know if anyone else is having this issue, but I thought I should post my fix just in case.

Edit: The exact error message I see is this:

```
ALSA lib pcm.c:7234:(snd_pcm_recover) underrun occured
```

Also, here's a suggestion for a more permanent fix than the LD_PRELOAD method. In the Aquaria installation folder, do the following:

```

$ mv libopenal.so.1 libopenal.so.1.original
$ ln -s /usr/lib/libopenal.so.1 .

```

I should also mention, in case it's not obvious, that either fix requires having the package libopenal1 installed.

---

### Post by madjr on 2010-05-10
cool thanks

i haven downloaded aquaria yet, but if i have this issue i'll come back here :)

you got this fix from their forums ?

maybe they are not aware of it

---

### Post by Kevinator on 2010-05-10
> **madjr said:**
> you got this fix from their forums ?

maybe they are not aware of it

No, I found some references to possible issues with OpenAL, so I decided to try using a different one. I was going to report a bug, but their bugzilla requires more registration than I felt like doing.

I noticed another comment somewhere on ubuntuforums where someone used a similar trick to work around a "no audio" problem in Aquaria. They replaced Aquaria's copy of libopenal.so.1 with a symlink the the one in /usr/lib. This should have about the same effect, but is a more permanent fix.

---

### Post by Buttink on 2010-05-14
I did the fix and it worked.... then today it stopped working??? anyone else have this or is this just me (maybe i updated something >.>  )

```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
AL lib: ALc.c:1808: alcCloseDevice(): deleting 195 Buffer(s)
```

is what the command line barfs up

---

