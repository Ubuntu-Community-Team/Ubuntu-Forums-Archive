---
title: "Doom3/Quake4 audio delay"
date: 2010-08-30
forum: Gaming &amp; Leisure
---

### Post by bigseb on 2010-08-30
I installed Doom 3 and Quake 4 about a month ago and went through the usual installation procedures, etc. However there is one thing I haven't been able to sort out: the audio. There seems to be a delay between what I see and what I hear. This delay can be anywhere from a few seconds to two minutes. If it isn't there from the moment I start the game then it usually develops after a few minutes. Beyond that the games seem to work just fine. 

How do I fix this really annoying problem. Someone suggested I install libsdl1.2debian-alsa but that didn't really do anything. Please help.

---

### Post by odinfromvalhalla on 2010-08-30
this might help you: [http://ubuntuforums.org/showthread.php?t=1507104](http://ubuntuforums.org/showthread.php?t=1507104)

---

### Post by J.K.Makowka on 2010-08-30
Same happens in ET:QuakeWars.

It's pulseaudio related, but I have yet to come across an easy fix other than deinstalling pulesaudio.

---

### Post by bigseb on 2010-08-30
> **J.K.Makowka said:**
> Same happens in ET:QuakeWars.

It's pulseaudio related, but I have yet to come across an easy fix other than deinstalling pulesaudio.
Is that a problem?

---

### Post by alexandrius on 2010-08-30
add this to last line in doom3
```
+set s_alsa_pcm plughw:0 +set NumberOfSpeakers 2 "$@"
```

so that it look like this:
```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/home/alex/Apps/Games/Doom3/"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec ./doom.x86 +set s_alsa_pcm plughw:0 +set NumberOfSpeakers 2 "$@"
```

---

### Post by J.K.Makowka on 2010-08-30
Wow, this actually also seems to work for ET:QW

Why wasn't this pointed out in the several pages long ET:QW sound problems thread a while back?

---

### Post by bigseb on 2010-08-31
> **alexandrius said:**
> add this to last line in doom3
```
+set s_alsa_pcm plughw:0 +set NumberOfSpeakers 2 "$@"
```so that it look like this:
```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/home/alex/Apps/Games/Doom3/"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec ./doom.x86 +set s_alsa_pcm plughw:0 +set NumberOfSpeakers 2 "$@"
```
This may sound really ignorant but I'm not on your level regarding coding: How does one go about adding stuff... and add it to what?

---

### Post by J.K.Makowka on 2010-08-31
It's much easier than it looks. Just go to your doom3 directory and look for the doom3 start script. open it with a text editor and add the one line behind the executable so that it looks like the bottom example.

---

### Post by bigseb on 2010-08-31
it seems to have done the trick. Hurrah! Will the same work for Quake?

---

### Post by bigseb on 2010-08-31
> **bigseb said:**
> it seems to have done the trick. Hurrah! Will the same work for Quake?
Never mind... tried it on Quake and it seems to work fine now too. Hope to test it properly later.

Thanks!!

---

### Post by Brebs on 2010-09-01
> **bigseb said:**
> This delay can be anywhere from a few seconds to two minutes.
Please file a bug report against pulseaudio. That sort of delay is beyond ludicrous.

---

### Post by bigseb on 2010-09-01
Never filed a bug report before. How does one go about that?

---

### Post by J.K.Makowka on 2010-09-01
Long known:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/577727](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/577727)

---

### Post by glaasje on 2010-09-01
thanks!
is had the same problem too:D

---

### Post by oldos2er on 2010-09-09
> **J.K.Makowka said:**
> It's pulseaudio related, but I have yet to come across an easy fix other than deinstalling pulesaudio.

Following this tut worked for me: [http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/)

Then to run Doom3 ```
pulseaudio --kill
doom3 +set s_driver alsa
```

---

### Post by Rhemat on 2010-11-04
I followed the guide you posted oldos2er, but unfortunately Pulse comes back.  I swear that PA has been programmed to persist beyond any attempt to kill it, and if you do get rid of it, it takes audio with you.
Some times the audio in Quake 4 behaves, but it might just go at any time.  Are there any other guides that could help?  Is there any hope that Gnome will stop shoving PA down our throats?

---

### Post by Shazzner on 2010-11-04
The tip posted earlier about setting the launch script worked for me unfortunately it'll only run if I shutdown all other alsa devices including my browser which is really annoying.

I don't really know what's the problem here, I feel it's a driver issue with onboard sound cards but who knows? The bug is against ia32-libs which suggest it's a 64bit problem, but I'm using 32bit ubuntu and I have the same issue.

It's ridiculous this problem still exists, I don't really know where to file the bug upstream to either.

Edit: The command posted in the bug report worked well for me:
pasuspender -- doom3 +set s_alsa_pcm plughw:0

Still though, why are we using ugly hacks like this instead of actually fixing the problem?

---

### Post by bigseb on 2010-11-08
I actually got mine working perfectly. Can't remember what I did, wrote it all down. I'll have to find my notes. When I do I'll post it.

---

### Post by Sean.m on 2011-03-31
#alexandrius: Your solution worked on my laptop, Lenovo Y530 and desktop with Intel HDA sound. Brilliant, thank you!

---

### Post by JamButty on 2011-12-31
[alexandrius]("http://ubuntuforums.org/member.php?u=865266") - your solution is still working for Doom under Oneiric (HP Elitebok, Mobility Radeon HD 3650)
Sound is a huge part of the atmosphere. Thanks!

---

### Post by ahso4271 on 2012-05-15
Cool thanks.


+set s_alsa_pcm plughw:0 +set NumberOfSpeakers 2 "$@"

Doom3 is still ahead of most new games with beautiful textures, mirrors in the toilets etc. For ex. Rage is boring, X-Plane still struggling to get nice, flickerfree shadows etc.

---

### Post by acjohnson on 2012-09-12
> **alexandrius said:**
> add this to last line in doom3
```
+set s_alsa_pcm plughw:0 +set NumberOfSpeakers 2 "$@"
```

so that it look like this:
```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/home/alex/Apps/Games/Doom3/"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec ./doom.x86 +set s_alsa_pcm plughw:0 +set NumberOfSpeakers 2 "$@"
```

To me it makes sense just to stick these settings into your DoomConfig.cfg file so you don't have to add it to your shortcut:

```

nano ~/.doom3/base/DoomConfig.cfg

```
Change the following lines to say:
```

seta s_numberOfSpeakers "2"

```
and
```

seta s_alsa_pcm "plughw:0"

```
I tested this on Ubuntu 12.04 32-bit and it works perfectly.

---

