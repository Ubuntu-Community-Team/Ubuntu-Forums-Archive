---
title: "Sound Output not being made available to other apps"
date: 2005-07-22
forum: Desktop Environments
---

### Post by cam8001 on 2005-07-22
Hi there,

I have just done an install of Ubuntu for the first time and have installed Amarok, Totem-Xine, and other bits and pieces. Most things work well. Unfortunately I am having a problem with sound.

It seems that if I play something in one app, like Amarok, it will work ok. But then if I try to play something else in another player like Totem there will be no sound unless I reset Gnome. Vice-versa is also true.

It seems like my sound output is locked for use by one app, and then not released for the other. Can anyone help me with this?

I am using a soundstorm on an nForce 2 motherboard, if that helps. Amarok is set up to use gstreamer, although it works with Xine also (but the problem persists). When I check in Volume control there are two soundcards it seems - Realtek ALC650E (OSS) and nVidia nForce2 (ALSA). Changing between these makes no difference.

Any help would be appreciated.

---

### Post by aggiechemist on 2005-07-22
Look under the preferences area for the multimedia selection thing. It will give you options for the "audio sink" and such. This has been reviewed pretty well on the forums, but in brief there are three ways of handling audio (OSS, ESD, ALSA). It kind of sounds like you are using OSS.

OSS (I think) is only smart enough to handle one sound at a time. It cannot mix sound from two applications in the software. Moving the sound system to newer things like ALSA or ESD should get around that. Sound is kind of a big issue in Linux, so there are some great forums on this and several that have "stickies" to note how important they are. [This](http://ubuntuforums.org/showthread.php?t=32063) is one of the best.

Good luck.

---

### Post by cam8001 on 2005-07-23
Thank you for very much for this, the information in that thread solved my problem perfectly.

---

