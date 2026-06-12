---
title: "ubuntu is bloated?"
date: 2009-05-04
forum: General Help
---

### Post by Keymone on 2009-05-04
too loud topic name probbly

imo ubuntu suffers from very fuzzy separation of functional subsystems

i tried removing everything related to bluetooth few days ago and aptitude told me it would break pulseaudio. why? do we really need audio system to be dependant on bluetooth?

on the other hand i stuck with broken microphone and have no idea what exactly is not working. alsa? oss? alsa-oss? pulseaudio?

2 things we need

1. strong dependencies and decent functionality testing probably involving user to answer some questions(like "do you hear me?") for all the subsystems

2. minimal cross-dependencies between subsystems. pusleaudio definitely should not break apart if i remove bluetooth support from ubuntu.

i just want to uncheck a single checkbox and have bluetooth / printing stuff / networking system / desktop environment to just vanish without leaving any related libraries but leaving the rest of the system completely functional.

i hope this topic makes sense..

---

### Post by KhaaL on 2009-05-04
You can safetly remove pulseaudio and have the audio functional with only alsa. why BT depends on PA is because of streaming audio through BT will be played with PA. if you want a really minimal ubuntu installation, try the ubuntu minimal CD image wich will give you the power to hand-pick what you want in your system: 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

