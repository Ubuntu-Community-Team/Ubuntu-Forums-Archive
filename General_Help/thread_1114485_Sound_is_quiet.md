---
title: "Sound is quiet"
date: 2009-04-02
forum: General Help
---

### Post by Danger Fox on 2009-04-02
I am a new Linux user and so far I've been able to find solutions to all the problems I've had come up so far (driver installation and flash), but the sound configuration is something that I can't seem to fix. I get some sound but it is very quiet. I have the master volume turned up all the way and my headphones are turned up all the way and it is still quiet. I have tried solutions such as removing pulse audio, trying to configure pulse audio, and downloading and installing the latest ALSA drivers. I did all these through guides on this forum and other places, but nothing changed. Also, when I say new user, I mean I started using Ubuntu 3 days ago, so if possible keep things pretty simple. I'm an experienced Windows user but I was not prepared for how different Linux was.

---

### Post by HermanAB on 2009-04-02
There are multiple places where the volume can be adjusted - one of them is too low.

Find a mixer application that shows *all* options and play with *all* settings, including the ones that don't make sense, eg. aumix.

'Hope that helps!

---

### Post by buminatrain on 2009-04-02
fire up a terminal (applications>accessories>terminal or alt+f2 then type gnome-terminal) run the command "alsamixer" turn your master and your pcm all the way up.  all other volume controls run off of this mixers settings, so if something is low in here turning anything else all the way up will still not have the volume at 100%.

---

### Post by Danger Fox on 2009-04-02
Both those methods worked fine. Thanks for the help!

---

