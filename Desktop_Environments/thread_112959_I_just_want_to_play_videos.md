---
title: "I just want to play videos"
date: 2006-01-05
forum: Desktop Environments
---

### Post by elver on 2006-01-05
I've been a Linux user for, uh, 4 or 5 years now? Even did some part-time work as a Linux server admin at a couple of places. Switched from Gentoo to Ubuntu on all my systems about 5 months ago. I'm studying Computer Science and been programming for years. So advanced replies and the like are welcome.

That said, over these years I've come to the realisation that all I want is an OS that is easy to set up and use, doesn't crash on me all the time, and takes care of my essential computing needs: browsing, e-mail, coding, audio, and video.

I'm having problems with that last item.

On my Windows XP install that I rarely use, BSPlayer takes care of it. Just play a video with it and it works.

With Ubuntu, I'm essentially having the same problem on all three of the machines currently sitting on my desktop: playing videos only works for a tiny subset of all the videos out there.

For an example video, I'm going to use a speech by Yuri Gagarin that I found while researching the Soviet space program. You can download it at [http://www.rgantd.ru/gag70_cd/data/video/gagarin4.avi]("http://www.rgantd.ru/gag70_cd/data/video/gagarin4.avi")

An attempt to play it with the default video player, Totem, displays the following messages:

[LIST=1]
[*]Totem could not play 'file:///home/elver/Desktop/gagarin4.avi'. -- Failed to play: Internal GStreamer error: pad problem.  File a bug.
[*]An error occurred -- Internal GStreamer error: negotiation problem.  File a bug.
[*]An error occurred -- Internal GStreamer error: pad problem.  File a bug.
[/LIST]

Trying the same with MPlayer results in a video with sound. *However...*

[LIST=1]
[*]The video stutters. It gets stuck for about half a second every second.
[*]Running mplayer with -ao null removes the stuttering and, not so surprisingly, the sound.
[*]Playing it from the command line results in stuttering being correlated with messages like: alsa-space: xrun of at least 0.058 msecs. resetting stream?,?% 1 0 70%
[*]Who the **** packaged MPlayer without adding out-of-the-box support for a proper fullscreen mode? Why do I have to keep adding -zoom to the command line options? Why does the GUI version keep complaining about missing fonts? Don't tell me about config files. I know where they are and I've gone and done the modifications on one of my computers. What I'm asking, is *why* I have to do any of this in a distro that is supposed to be human-friendly?
[/LIST]

VLC plays the video just find, but without any sound. The following is printed on the console:

VLC media player 0.8.4-svn20040920 Janus
[00000303] oss audio output error: cannot open audio device (/dev/dsp)

Seriously, people. All I want to do is play a couple of videos. Is it really that hard? All this worked just fine out-of-the-box on Gentoo. Why should it be any different on Ubuntu?

The hardware: 1.4ghz AthlonXP, 2.2ghz Athlon64, 1.3ghz Celeron M.

---

### Post by Minyaliel on 2006-01-05
Totem's not that good, really, I never use it, can't understand why *that's* set as a default. But anyway, it's strange that MPlayer chops up the sound like that - are you sure you weren't running anything else, like limewire, that made your computer sluggish or something?

---

### Post by Lord Illidan on 2006-01-05
I use XINE as my media player. I find that it beats Totem and Mplayer handily, and supports full screen.

Also, enabling dma may help improve performance.

```
sudo hdparm -d1 /dev/***
```

As for the sound... try typing

```
killall esd
``` 
As for the fonts in mplayer, you have to install a package with mplayer's fonts , search for "fonts + mplayer" in synaptic. I hope you enabled the extra repos!

---

### Post by elver on 2006-01-05
> are you sure you weren't running anything else, like limewire, that made your computer sluggish or something?

No LimeWire or anything else Java-based. In any case, my main box runs Quake 4 at 1024x768, medium detail, at a steady 60fps while there's Gimp, Inkscape, and several other programs open in the background with huge files loaded. So that's definitely not it.

> Also, enabling dma may help improve performance.

Current mode: udma6.

> killall esd

Didn't help at all.

> As for the fonts in mplayer, you have to install a package with mplayer's fonts

Alright, now we're getting somewhere. That fixed that.

---

### Post by pelle.k on 2006-02-11
About VLC - install the vlc alsa plugin, and change output plugin to alsa in preferences. Should work like a charm.
More and more appz are defaulting to alsa in upcoming dapper release though, which is a good thing.

[edit]I had the same problem with a clean install of mplayer-nogui. It seems setting srate=48000 in config file (or commandline -srate 48000) takes care of this problem[/edit]

---

### Post by antidrugue on 2006-02-21
[QUOTE=elver]
[*]Playing it from the command line results in stuttering being correlated with messages like: alsa-space: xrun of at least 0.058 msecs. resetting stream?,?% 1 0 70%[/QUOTE]

Well, that's no problem, it is in fact [ a bug in alsa 1.10 and up](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=HighDefinitionAudio). Just add
```

srate=48000

```
to /etc/mplayer/mplayer.conf (or to ~/.mplayer/config) and it will solve the issue.

[QUOTE=elver]
[*]Who the **** packaged MPlayer without adding out-of-the-box support for a proper fullscreen mode? Why do I have to keep adding -zoom to the command line options? Why does the GUI version keep complaining about missing fonts? Don't tell me about config files. I know where they are and I've gone and done the modifications on one of my computers. What I'm asking, is [/QUOTE]

Well that only occurs because of compatibility issue. By default mplayer use 
```

vo=x11 

```
(in /etc/mplayer/mplayer.conf), just replace it with 
```

vo=xv

```
or with any video driver that has proper hardware rendering (depends if you have the xv extention enabled on your machine), then you won't need "-zoom" (which you really shouldn't use anyway, it consumes way too much cpu -- software rendering).

Read the [ mplayer docs](http://www.mplayerhq.hu/design7/info.html#docs) for more...

EDIT: sorry for repeting what pelle.k just mentionned (a week ago), didn't read his post before posting...

---

