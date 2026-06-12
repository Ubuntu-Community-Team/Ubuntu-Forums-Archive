---
title: "Fluxbox Audio/Video Problems"
date: 2009-10-07
forum: Desktop Environments
---

### Post by LaneLester on 2009-10-07
I'm running Fluxbox 1.x in Ubuntu Karmic. Web videos would not play the audio portion, although the video was OK.

I rebooted my computer, logged on to Gnome, and the videos were fine.

I logged out and in to Fluxbox, and now neither the video nor audio will play.

Is there some /dev or other specification that's different between Gnome and Fluxbox? Or some other cause of the problem?

Lane

---

### Post by LaneLester on 2009-10-07
OK, I found a [**blog post**]("http://linuxcritic.wordpress.com/2009/08/11/fluxbox-on-ubuntu-two-more-problems-two-more-solutions/2/") by a guy who had the same problem. It turns out that Fluxbox, when it starts, mutes the ALSA driver and zeroes the master volume. 

The solution was to run alsamixergui after Fluxbox is running, change the settings, and then add "alsactl restore &" to the startup file.

Lane

---

### Post by LaneLester on 2009-10-08
Well, I rejoiced too soon. In addition to separately-hosted YouTube videos not playing at all, videos created with Camtasia play very badly. The video advances very slowly, and the sound is in repeated bursts.

Lane

---

### Post by LaneLester on 2009-10-08
I just did a huge update on Ubuntu Karmic Alpha, and now the Camtasia videos work in Fluxbox! I don't understand it, but I'm glad for it.

Lane

---

