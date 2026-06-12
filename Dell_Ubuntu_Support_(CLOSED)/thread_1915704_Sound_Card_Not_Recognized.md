---
title: "Sound Card Not Recognized"
date: 2012-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tk007LwZFJW5ej on 2012-01-26
I cannot get ubuntu to recognize my sound card. I have a new Dell XPS 17, and I'm running ubuntu 11.10 x64. I followed this tutorial:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

up to step 5, except I substituted ubuntu-restriced-extras and ubuntu-restricted-addons for linux-restricted-modules (not sure if that was correct, but that's what I was told to do). After 

```
sudo apt-get udpate
```, I had new updates to install, and there was definitely something in there about drivers, but, after installing and rebooting, Settings->Additional Drivers still does not find any drivers for me. 

```
aplay -l
``` says no soundcards found.

---

