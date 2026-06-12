---
title: "Sound and video out of phase in mplayer"
date: 2005-12-02
forum: Desktop Environments
---

### Post by frankabel on 2005-12-02
I have installed the mplayer-586 and mplayer-fonts packages. After that, I download and install a win32codecs pakage . The problem is that when I play a film the audio and video are out of phase, the audio go about 4 seconds first that the video.

Any idea?

---

### Post by mlomker on 2005-12-03
Is it a file that plays normally on another machine?  I know that video/audio synchronization is a common problem when you rip video.

Mplayer is a common application, so I think I'll move your thread to the Gnome forum where more people will see it.

---

### Post by flopsy on 2005-12-03
[QUOTE=frankabel]I have installed the mplayer-586 and mplayer-fonts packages. After that, I download and install a win32codecs pakage . The problem is that when I play a film the audio and video are out of phase, the audio go about 4 seconds first that the video.

Any idea?[/QUOTE]

If the delay is constant, the + and - keys will adjust the a/v sync by .1 second. You can control this from the command line too: if the audio is out by 4s, for example, use the -delay 4 option.

If it plays OK in other players/on other computers, try the [-autosync]("http://www.mplayerhq.hu/DOCS/HTML/en/audio.html") option.

---

### Post by frankabel on 2005-12-03
Well, after play with some options of sound and video at mplayer I found that if I choose the "xv X11/Xv" driver I can play a .avi without any problem, but the rest of format (I test with wmv and mpg) state with the "out of phase" betwen the audio and video. I test in other OS (M$) and the videos play ok. I have a Acer Travelmate 520 with ATI RAGE video card and Trident sound adapter.

---

