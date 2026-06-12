---
title: "xps 1530 microphone not working"
date: 2009-11-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dougleduck on 2009-11-02
Using Skype and the sound recorder not been able to get my microphone working.

Changed from microphone 1 to 2 in the sound properties, this gave small signal in sound recorder, but almost nothing.

Tried all the different drivers, including Alsa, using 'Multimedia Settings Selector'. No joy.

Running Karmic, works under Vista.

---

### Post by Zoot7 on 2009-11-02
Mine doesn't work either. The only way I could get it to work was to remove Pulseaudio, but sadly Pulseaudio is more integrated this time. It used to work fine with just plain old alsa.

Does the Mic work in apps like Audacity?

---

### Post by dougleduck on 2009-11-10
bump.

no joy with audacity.

---

### Post by Stanko on 2009-11-18
Hmmm one more bump!
Same problem here, I used to remove pulseaudio and the mic worked fine. But now after removing it mic still doesn't work :/

---

### Post by depaulmatthew on 2009-11-30
> **Stanko said:**
> Hmmm one more bump!
Same problem here, I used to remove pulseaudio and the mic worked fine. But now after removing it mic still doesn't work :/

I got the same problem too.. mic not working.. Im using dell studio 15. It used work fine with jaunty. proble started after the upgrade. any clues?

---

### Post by dougleduck on 2009-12-28
bump! :(

---

### Post by Pascal11110 on 2009-12-30
I know this doesn't pertain exactly to your version, but this may help a little bit:

[A nice little wiki]("https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530")

---

### Post by dougleduck on 2010-01-10
This doesn't mention my ubuntu version 9.10, so I don't know if I can trust instructions for older releases.

---

### Post by PacktLikeFishees on 2010-02-11
Hey, I got my mic to work by installing pavucontrol and then going to the "Input Devices" tab. It turns out that it was muted, so I just clicked unmute and it worked perfectly. I hope this helps you guys out.

---

