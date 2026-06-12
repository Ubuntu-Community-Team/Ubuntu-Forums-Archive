---
title: "Help solve my sound issues."
date: 2005-10-15
forum: Desktop Environments
---

### Post by CAE on 2005-10-15
I guess I'm in a slightly odd situation. I have two active "soundcards" in my machine - one, an onboard sound system and the other is a PCI SoundBlaster Live, which I use and have speakers plugged in to. Now, I can't disable the onboard sound without enabling a jumper on my motherboard, and I don't want to do this as it would mean opening up my machine and pulling a lot of stuff out, due to poor layout. Previously, using Ubuntu, I've just messed with config files to get it going right, but I have no idea what to do with Kubuntu.

Exploring KControl and the Sound configuration, I've noticed under the hardware tab that you can override the default sound device. I figure this is what I want, but what do I set it to? The onboard sound is obviously device 0 and the card is device 1. Can anyone help me?

---

### Post by Estariel on 2005-10-15
hw:0,0 is the first sound device and
hw:1,0 is the second one.

if you set the output of the soundserver to one of these, all sounds piped through arts will get to this device, but all others won't.

You can set amarok to use arts, if you want to use gstreamer, you should set the amarok-gstreamer device as well. (This can be done in amaroks config dialog)

---

### Post by CAE on 2005-10-15
Brilliant, that was great answer, Estrariel.

The only other question I have is whether there's some sort of global config for gstreamer, or will I have to set applications up on an individual basis?

---

### Post by CAE on 2005-10-15
Hrm, I think I've solved my own problem with a bit of Googling. Another post on these forums suggested adding the following to /etc/asound.conf:

```
pcm.!default {
type hw
card 1
}

ctl.!default {
type hw
card 1
}
```

So if Gstreamer uses alsa, it'll default to card 1, right? The only problem I'm having now is that I can't figure out how to restart alsa now if I can't use the init script. How does alsa-utils work?

---

### Post by Estariel on 2005-10-15
You can install gstreamer0.8-artsd (this will pipe all gstreamer output through arts) and set arts to your desired soundcard (in the kde control center).

I tried this a few minutes ago, and my system froze a few times, so I think there is a bug somewhere; but you might be lucky and it might only be my system that's doing this...

---

