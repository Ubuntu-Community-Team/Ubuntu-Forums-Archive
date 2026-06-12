---
title: "Trouble with Audio on a Studio 15 Running 8.04"
date: 2009-01-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Noah0504 on 2009-01-16
I have a Studio 15 that originally came with Vista (I know, I know.  I thought I would give it a chance!) that is now running 8.04 after 8.10 had a few bugs that didn't make things friendly (Bluetooth failure being the biggest).

Audio under 8.10 was problematic until I installed updates from the proposed repo.  Now under 8.04, sound from the speakers works great, however, I have no sound when using headphones.  The speakers mute, but I get nothing from the headphones.

After searching around, I seem to only find fixes for those running 8.10 (which is really just to install the new ALSA drivers which can be done by the proposed updates).

I'm wondering if the same fix will work for 8.04.  I just don't know how to go about compiling and installing the latest ALSA drivers.

I have the Intel High Definition Audio card (HDA Intel).  Any help would be welcomed.

I'll end this saying it's good to be back on Ubuntu!

---

### Post by sirebral on 2009-01-16
I know this sounds silly, but have you checked the volume level for you headphones?  Check all devices and see if maybe the headphones are muted.

---

### Post by Noah0504 on 2009-01-16
I've checked, all the volumes seem to be fine.  I also noticed that my volume controls on the computer do not affect the sound through the speakers.  Everything seems to be the same as when I had everything working in 8.10 after installing the proposed updates.

EDIT:

I was tinkering with the sound settings again and didn't think I had changed anything when the headphones started working (I almost went deaf!).  Now, the only think that bothers me is that I have to use the PCM track to adjust the volume for the headphones and speakers.  Should I care?

---

### Post by Android565 on 2009-04-16
This seems to be solved on my laptop by removing mute on the "Surround" mixer

---

