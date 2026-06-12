---
title: "Jaunty Pulseaudio problems"
date: 2009-05-09
forum: General Help
---

### Post by James78 on 2009-05-09
Hi,

I use Kubuntu Jaunty Jackalope, I installed Gnome a bit ago and started having sound problems due to Pulseaudio overloading CPU, then it'd shutdown. So I made a attempt to fix this for awhile, and eventually after doing something, flash (latest version) on Firefox 3.0.10 jumps. Basically, I go to any video, I let it play, and it'll be fine for about a minute or 2, then the video will automatically get jumpy, the sound still works, but it sounds like the video is forwarding, and it almost appears to go 2 seconds at a time. Really odd behaviour. Another noticed thing is that when this happens, Firefox jumps from a regular 30% CPU usage to over 80%. If I stop the video and press play again, it plays like it's forwarding, but if I move the video slider, it goes away until about a minute later. I've tried Reinstalling Firefox, and Flash many times, the problem still occurs.

Note: I tried to uninstall all traces of Pulseaudio since it was being a pain, and now my hardware is falling back to my ALSA driver configuration, although in my System Settings -> Multimedia panel, it still says "Pulse Audio" in there for some reason; I put it at the bottom of the list. Libstd pulse won't uninstall without removing the core of KDE for some reason, and Libstd alsa isn't installed at this moment. Video playback in VLC, and music playback in Songbird is flawless (except for small jumps and bumps in the audio, I assume normal? Perhaps not. Pulseaudio didn't bump like that..)

I played a flash video in Songbird, and it does the exact same thing, which leads me to believe it's not flash or the browser that's causing the issue. It almost seems like when I play music, and get these little skips and gaps, actually it seems more like the sound repeats itself, that it's around the same time that the flash video would start doing this annoying problem. For all it seems, I'm still having major sound issues on my system, and that may be the cause. :(

Update: Now, I reinstalled all Pulseaudio related packages, and the whenever sound is played Pulseaudio eats up the cpu after 15 seconds and terminates due to CPU overload. Really, this whole thing is related to something wrong with my sound system, no idea what, but it's frustrating.

Anyone have any ideas? I would like to get this fixed asap!

If anyone wants to see a closer look at it, I can record a video of it.

---

### Post by James78 on 2009-05-09
Bump..

---

### Post by KhurramM on 2009-05-09
See if sox is installed.

If not, install and reboot, Maybe u get this solved.

Adios.

---

### Post by James78 on 2009-05-09
I now just noticed that when I am playing a video, pulseaudio eats out my CPU! This would indeed explain why it kills itself due to CPU overload. That would appear to be the problem! Any ideas about caps.c?

I will test out the sox thing soon.

---

### Post by James78 on 2009-05-10
Sox didn't help anything unfortunately.

---

### Post by James78 on 2009-05-10
Bump....

---

### Post by linux_tech on 2009-05-10
```
sudo killall pulseaudio
```
stops pulseaudio

check alsa settings

```
gnome-alsamixer

```

---

### Post by James78 on 2009-05-10
Nope, that didn't help anything.:confused:

---

### Post by danwood76 on 2009-05-10
> 
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.

is normal.

The issues sound like pulse is leaking somewhere.
It might be a case of adjusting the resampling algorithm to something simpler as maybe your PC cant quite handle it?
There is another option which will stop pulse from limiting its CPU usage but I assume its disabled for a reason.

How much CPU does pulse normally take?

---

### Post by James78 on 2009-05-10
Generally 3-6%, idle it appears to be perfectly fine (less than 1%), but after about a minute of playing a video w/sound, or audio, it will jump to around 90%, and everything will lag. That would be due to the fact that I disabled the CPU termination for it, which after this I realized it was turned on for good reason. So, since you say that caps.c is completely normal, then the real issue here is that pulse is jumping up it's CPU usage immensely when it is used for a little bit (video, music, etc). If I find out why, and fix it, everything will be good. :)

Therefore, summary, small sounds like login sound are perfectly fine, video, music, long sounds are not fine.

I have a single core 2.2Ghz processor. I've never had this issue before.. Either it happened after I insalled Gnome in Kubuntu (likely since Gnome probably installed Pulseaudio on my system), or it happened when I did a fresh install of Kubuntu 9.04 Jaunty. But really, in either way, I still don't think this should be an issue.

---

### Post by James78 on 2009-05-10
Bump..

---

### Post by James78 on 2009-05-10
Bump..

---

### Post by James78 on 2009-05-11
Bump..?

---

### Post by James78 on 2009-05-11
Downloaded 0.9.15 test 8, compiled and installed. Pulseaudio version information says it's still 0.9.14, it won't start up in the command line, but I have a sh script that automatically starts it up at system startup, and that works great. There appear to be no CPU overloads, and sound quality is far superior to anything I've ever used!

---

