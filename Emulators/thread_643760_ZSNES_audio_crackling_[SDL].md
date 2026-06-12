---
title: "ZSNES audio crackling [SDL?]"
date: 2007-12-18
forum: Emulators
---

### Post by &#12465;&#12452;&#12488; on 2007-12-18
ZSNES makes awful crackling noises. It's not constant at all, but occasionally distorts the whole audio. Attempting to change the audio settings didn't help anything. As the distortion happens at the exact same time in a song, SFX or similiar, it would seem as if there are some special notes that makes the noise occur.

Tried to search for this both here and on Google, without finding anything helpful. X-Moto also sounds really choppy, so it might be SDL causing the problem. Some posts here said to replace libsdl1.2debian-alsa with oss or esd, but that didn't fix my problem.

By the way, my audio card's hda-intel.

---

### Post by Jason_25 on 2007-12-18
I am battling this myself with my new laptop.  For now, I seem to have fixed it by setting the sound to 48000 hz.

---

### Post by tht00 on 2007-12-18
I've come across this...  I've got crackling on games like Neverball/Neverputt, almost all emulators... really ruins these games.

This happened on Ubuntu when I used it (up through Edgy or Feisty) and it continues even now as I use Gentoo... so it's not something limited to Ubuntu.  Best I can tell, it has to do with SDL audio.

Haven't found a solution yet... it doesn't seem very wide-spread, but there are others with this problem.

I've got a Dell e1505 laptop.  From lspci:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---

### Post by &#12465;&#12452;&#12488; on 2007-12-27
Another thread about this problem was made a couple of days ago, and there I learned that ZSNES now uses libao for audio output.

I started this by pinning the guilt on SDL, but choosing sdl output was actually what fixed my problem.

Start ZSNES from a terminal with the command "zsnes -ad sdl" to select SDL audio output, hopefully that'll do it for you too.

My post in that thread:
[http://ubuntuforums.org/showthread.php?p=4025136#post4025136](http://ubuntuforums.org/showthread.php?p=4025136#post4025136)

---

### Post by FranMichaels on 2007-12-27
I'm glad that solved it. :KS

I have an hda-intel onboard sound as well. 

For those with problems with neverball and neverputt, setting the output to 48000khz solves it for me.

```
gedit ~/.neverball/neverballrc
```

Change it to this (should be on Line 11)

audio_rate           48000

Save it.

Load up neverball and enjoy.

After these tweaks, my sound issues are solved. I really hope they improve the intel-hda driver so it works properly out of the box.

---

### Post by DemonTeethIV on 2008-04-25
When I try to run zsnes with the code > zsnes -ad sdl

there seems to be a problem with even getting it to run. any suggestions to manually doing this?

---

### Post by acoustibop on 2008-04-26
Do zsnes --help to get a list of sound driver options, then try each one with the code &#12465;&#12452;&#12488; suggested, i.e. zsnes -ad <driver option>  When you find the best option, edit ~/.zsnes/zsnesl.cfg and change the libAoDriver option to the one you want to use.

As a general improvement for sound in games, try installing libsdl1.2debian-all.  This will remove libsdl1.2-alsa but don't worry, support for ALSA will be reinstalled as part of libsdl1.2debian-all.

---

### Post by dli8ilb on 2009-08-22
> **acoustibop said:**
> As a general improvement for sound in games, try installing libsdl1.2debian-all.  This will remove libsdl1.2-alsa but don't worry, support for ALSA will be reinstalled as part of libsdl1.2debian-all.

thanks, acoustibop.  i was having the same problem in jaunty & just wanted to confirm that installing libsdl1.2debian-all worked perfectly.

---

### Post by kapcom01 on 2009-11-28
that worked for me too, thanks.

---

### Post by Exüberance on 2012-06-05
The solution didn't work for me on Ubuntu 12.04 64-bit, what what DID work was setting the rate to 48 kHz, then using OSS (through the pauseaudio wrapper since Ubuntu dropped native OSS support)

```
padsp zsnes -ad oss
```
then set the rate to 48000Hz.

Note that using the fast-forward functionality will cause the sound to become desync'd with the audio, so don't do that!

The sound is MUCH clearer than with ALSA or SDL and it doesn't crackle after a while like the others do.

---

### Post by Perfect Storm on 2012-06-06
Old thread. Closed.

---

