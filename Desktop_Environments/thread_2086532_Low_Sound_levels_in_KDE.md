---
title: "Low Sound levels in KDE"
date: 2012-11-21
forum: Desktop Environments
---

### Post by reklan on 2012-11-21
Morning All..

I have a question/problem that I would like to try and get answered.

I am currently running Kubuntu 12.10 on my desktop (however this applies to any KDE distro i have tried).

The sound levels are a lot lower than either Ubuntu (Unity or Gnome) or Xubuntu..

i..e I Have to turn my speakers up to halfway to get the same level as the others at a quarter way.

I have set the sound levels to their, highest on the desktop volume control and in the sound settings.

Is their any way of increasing the levels ( i.e. on Ubuntu you have the option of increasing the sound over and above 100% level)

your help would be appreciated..

---

### Post by reklan on 2012-11-24
Any one got any Ideas??

---

### Post by ankspo71 on 2012-11-25
I use PulseAudio Volume Control ('pavucontrol') in Kubuntu and it is capable of raising the volume to 153%. You might need to install 'pulseaudio' too if it isn't already installed. Installing pavucontrol does not change the maximum volume level in KDE's volume control "Kmix" (or while using a keyboard's multimedia keys) though, so you will need to open PulseAudio Volume Control in the start menu and adjust the volume there.

---

### Post by ankspo71 on 2012-11-25
You might also want to try the following:

Open a terminal window ans type in:
```
alsamixer
```

Then check the volume levels for "Master" "Front" and "PCM". On my system setup, Kmix controls the Master volume only, but Front and PCM also control my volume, and greatly effect the overall volume.

If you don't see many volume sliders then press F6 to choose the correct sound card to adjust, and then press F5 to show all available volume sliders.

---

### Post by reklan on 2012-11-26
cheers will give these ago, when I get home tonight..

---

### Post by reklan on 2012-12-21
Apologies for late reply... the "alsamixer "fixed the problem perfectly thanks..

---

