---
title: "GStreamer encountered a general resource error."
date: 2006-10-03
forum: Desktop Environments
---

### Post by Cronjob on 2006-10-03
I can play ogg and mp3 formats with no problem in Amarok, Totem 1.4.3, Mplayer, Beep (after setting it to ALSA or ESD), VLC and XMMS. I don't believe any of these use gstreamer (for example, Amarok uses the xine engine). 

However, I can play ogg but not mp3 in gstreamer players. For example, I can not play mp3 in RhythmBox, Quod Libet, Banshee or Listen Music Player. If I get any error at all, it's usually *GStreamer encountered a general resource error*. The mp3 may or may not be imported into the playlist, but never plays.

I have read through the ubuntu wiki page on enabling proprietary formats and a handful of threads here to no avail, which is why I am posting here. I have a massive mp3 collection (about 180gb) and want a more robust media manager like one of those I've listed above.

I am on Kubuntu (6.06) AMD64 and I have the following gstream items installed:

```

gstreamer0.10-alsa                              install
gstreamer0.10-esd                               install
gstreamer0.10-ffmpeg                            install
gstreamer0.10-fluendo-mp3                       install
gstreamer0.10-fluendo-mpegdemux                 install
gstreamer0.10-gl                                install
gstreamer0.10-gnomevfs                          install
gstreamer0.10-gnonlin                           install
gstreamer0.10-plugins-bad                       install
gstreamer0.10-plugins-bad-multiverse            install
gstreamer0.10-plugins-base                      install
gstreamer0.10-plugins-base-apps                 install
gstreamer0.10-plugins-good                      install
gstreamer0.10-plugins-ugly                      install
gstreamer0.10-plugins-ugly-multiverse           install
gstreamer0.10-sdl                               install
gstreamer0.10-tools                             install
gstreamer0.10-x                                 install
libgstreamer-plugins-base0.10-0                 install
libgstreamer0.10-0                              install

```

If anyone could offer some assistance, I would appreciate it. I posted in a much older related thread topic about ten days ago but it never received a follow up, so I apologize for yet another thread.

---

### Post by Cronjob on 2006-10-03
Anyone able to offer any insight on this? I completely reinstalled my system and I still can't play mp3 files in anything that (I believe) uses gstreamer, despite having all the gstreamer libs and plugins installed.

I've also disabled the onboard audio so it automatically uses my Audigy2 card. I've installed all of the multimedia codecs in automatix (one selection at a time, followed by testing before moving on to the next installation).

It's completely frustrating.

Thank you.

---

### Post by hugmenot on 2006-10-04
File a bug in Malone. The real developers are much more knowledgeable in this area.

---

### Post by RAOF on 2006-10-04
You also might want to run one of the non-working programs from the a terminal, to see if any debugging info is being printed out that would be useful.

---

### Post by Ehtetur on 2006-11-04
I also had this problem. Rhythmbox and banshee played some mp3 files and not others.

My issue was that I installed two gstreamer plugins for playing mp3s:
gstreamer0.10-bad [universe]
gstreamer0.10-fluendo-mp3  [universe]

The solution was to uninstall either one of the two plugins.
I chose to removed gstreamer0.10-fluendo-mp3 and keep gstreamer0.10-bad.
After that, I was able to play mp3s that wouldn't play before.

I found the fix here:
[https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59](https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59)

-Ehtetur

---

