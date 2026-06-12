---
title: "SDL + Pulseaudio = choppy sound"
date: 2009-02-15
forum: General Help
---

### Post by sumguy231 on 2009-02-15
I'm having a problem with sound in games which use SDL on Hardy. Pulseaudio seems to be generally configured right and working with most applications despite a console error on startup which states "PULSEAUDIO: Unable to connect: Connection Refused". However, games which use SDL such as frozen-bubble and the World Of Goo demo have extremely choppy audio. I've tried tweaking the SDL_AUDIODRIVER environment variable but it doesn't seem to help. Does anyone know how to resolve this?

---

### Post by sumguy231 on 2009-02-16
One bump, because I'll be annoyed if I have to go figure this out myself.

---

### Post by ouija on 2009-02-25
[COLOR="Red"]Update:[/COLOR] I have successfully fixed this issue! (and here it is two years since you posted about it!)

This was in regards to a problem I was experiencing with Kdenlive.

Basically, Kdenlive uses SDL for sound, and Ubuntu Intrepid relies on PulseAudio.

Providing you are still using the Pulseaudio package within your Ubuntu setup; If not, install the "pulseaudio" package to follow these instructions.

Then you'll simply need to install the "pulseaudio-esound-compat" package and the "libsdl1.2debian-esd" package.

Then, open up the Terminal and enter the following:
> $ export SDL_AUDIODRIVER=esd
Then try testing the sound using the command:
> $ inigo myvideo.mpg

And voila! Stuttering sound is a thing of the past! (at least it was for me) And I think this should fix any related issues with Programs that rely on ESD while running under PulseAudio.

Hope this is helpful for anyone else experiencing the same issue.

---

### Post by davidbenson on 2009-03-27
Thanks for posting a response to this...  I'd never had this problem but after the last update, my sound went choppy in SDL apps...  This worked perfectly...

---

### Post by jaygo on 2009-11-06
> **ouija said:**
> 
Then you'll simply need to install the "pulseaudio-esound-compat" package and the "libsdl1.2debian-esd" package.

Then, open up the Terminal and enter the following:
Then try testing the sound using the command:

Many thanks! That + disabling compiz made kdenlive usable. Now I can stop troubleshooting six different video programs and get working!

in ubuntu 9.10, installing that libsdl package required the removal of the libsdl...alsa package, so instead I installed the libsdl1.2debian-all package so I wouldn't lose any compatibility with other software.

---

### Post by hellocatfood on 2009-11-09
> **ouija said:**
> Then, open up the Terminal and enter the following:

Then try testing the sound using the command:
$ export SDL_AUDIODRIVER=esd 

Just in case I should want to undo this what command should I use?

---

### Post by atrus on 2009-11-14
Choppyness went away as soon as i did:

sudo apt-get install libsdl1.2debian-pulseaudio

---

### Post by ju2wheels on 2009-11-14
> **hellocatfood said:**
> Just in case I should want to undo this what command should I use?

```
$ unset SDL_AUDIODRIVER
```

---

### Post by hellocatfood on 2009-11-14
Thanks guys, that fixed my issue!

---

### Post by kthxbai2u on 2010-03-15
None of these fixes work...

I have googled millions of fixes and tried them all.

I still have choppy audio (after the last karmic update) and cant seem to fix it...

---

### Post by pbrane on 2010-03-15
One thing I did that helped me was to create a file in my home directory called **.alsoftrc** with the contents *drivers = oss*. Don't know why that works but now my games have sound that works.

---

### Post by afrodeity on 2010-10-22
bump

---

### Post by aaronLund on 2011-03-13
> **kthxbai2u said:**
> None of these fixes work...

I have googled millions of fixes and tried them all.

I still have choppy audio (after the last karmic update) and cant seem to fix it...

me too.  i'm on 10.04 now.

perhaps it'd be worth posting the results of a:

```
lspci |grep audio
```

Here's mine:

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

---

### Post by aaronLund on 2011-03-21
Weird.

So if you're having this issue in Kdenlive, "hide" your audio file and play the video.

In my case, the audio will play just fine (sans video).  The choppiness only starts once you play the video along with the audio.

I'm now wondering if this is, in fact, a video issue and not an audio issue.

```
lspci |grep VGA

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```

---

