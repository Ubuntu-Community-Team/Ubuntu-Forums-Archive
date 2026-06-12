---
title: "Does anyone know of a good Desktop AUDIO recorder?"
date: 2010-05-22
forum: Desktop Environments
---

### Post by erwinsoo on 2010-05-22
I have used GTK recordmydesktop but it records both video and audio. Does anyone know of any software that records only audio or whatever is playing through the PC's soundcard?

---

### Post by Kleenux on 2010-05-22
You may want to try Ardour GTK2.

It looks really great... (unfortunately I didn't have enough luck to get my Digital-IN recognized and thus could not use it ; but you may not have that problem ;-)

---

### Post by meho_r on 2010-05-22
Audacity works fine (I also had to change "Profile" in "Hardware" tab in "Sound Preferences" to a profile with output only, i.e. without analog stereo input. So, if recording doesn't work, take a look there first).

---

### Post by erwinsoo on 2010-05-22
> **Kleenux said:**
> You may want to try Ardour GTK2.

It looks really great... (unfortunately I didn't have enough luck to get my Digital-IN recognized and thus could not use it ; but you may not have that problem ;-)

Tried. Setting up the audio at the beginning throws me an error on Jack server or parameters set incorrectly.

---

### Post by erwinsoo on 2010-05-22
> **meho_r said:**
> Audacity works fine (I also had to change "Profile" in "Hardware" tab in "Sound Preferences" to a profile with output only, i.e. without analog stereo input. So, if recording doesn't work, take a look there first).

Actually, I was wondering if there was any software that could just record whatever I was hearing off the speakers. Creative Technology has a software to record realtime whatever that was playing through the soundcard but its windows based. Since gtkrecordmydesktop could record both video and sound, wouldnt it be possible to develop a similiar software that only records the audio. 

I did try audacity but it requires you to line in from an external audio source and also could not find the menu options you mentioned in your post egsound preferences, profile. I'm using the version provided in  10.04 repo 

Not sure if i missed anything

---

### Post by kev77 on 2010-05-22
> **meho_r said:**
> Audacity works fine (I also had to change "Profile" in "Hardware" tab in "Sound Preferences" to a profile with output only, i.e. without analog stereo input. So, if recording doesn't work, take a look there first).

i second that, audacity is fantastic, i have produced 2 albums using a mixture of audacity and hydrogen with my band, audacity has a very large plugin base and the effect that can be produced are very professional. a friend bought a USB turntable for his windows PC and audacity was included, he was amazed when i guided him through the process of reducing scratches on his old records and enhancing the overall sound quality of the tracks with just the standard plugins that are included, he has successfully remastered a pile of old audio cassettes too using audacity to reduce the tape-hiss. brilliant!:)

---

### Post by meho_r on 2010-05-23
> **erwinsoo said:**
> Actually, I was wondering if there was any software that could just record whatever I was hearing off the speakers. Creative Technology has a software to record realtime whatever that was playing through the soundcard but its windows based. Since gtkrecordmydesktop could record both video and sound, wouldnt it be possible to develop a similiar software that only records the audio. 

I did try audacity but it requires you to line in from an external audio source and also could not find the menu options you mentioned in your post egsound preferences, profile. I'm using the version provided in  10.04 repo 

Not sure if i missed anything

Sorry about the confusion. Yes, Audacity is able to record anything you hear from speakers. You probably don't have to set anything in Audacity itself, just press the "Record" button. Sound preferences I meant is Ubuntu/Gnome's Sound preferences: **System > Preferences > Sound**, then take a look at the **Hardware** tab, on the bottom you'll see the **Profile** drop-down menu. On my system, it is set to *Analog Stereo Duplex* by default and I had to switch to *Analog Stereo Output* to successfully record sound in Audacity (I let a song play in Banshee and activated button sounds for testing purposes; everything was recorded properly). However, when you need to record from a microphone, don't forget to change the profile back (as well as set the **Connector** in the **Input** tab to *Microphone*).

There is also "plain" sound recorder (which is installed by default on Ubuntu: **Applications > Sound & Video > Sound Recorder**) for most basic recording, but I'd always go with Audacity.

@kev77: yeah, it's amazing piece of software indeed :) I discovered a book published in March this year: [Getting Started with Audacity 1.3](https://www.packtpub.com/getting-started-with-audacity-1-3/book), which looks like a nice intro for beginners (and maybe useful to advanced users too).

---

### Post by erwinsoo on 2010-05-30
> **meho_r said:**
> Sorry about the confusion. Yes, Audacity is able to record anything you hear from speakers. You probably don't have to set anything in Audacity itself, just press the "Record" button. Sound preferences I meant is Ubuntu/Gnome's Sound preferences: **System > Preferences > Sound**, then take a look at the **Hardware** tab, on the bottom you'll see the **Profile** drop-down menu. On my system, it is set to *Analog Stereo Duplex* by default and I had to switch to *Analog Stereo Output* to successfully record sound in Audacity (I let a song play in Banshee and activated button sounds for testing purposes; everything was recorded properly). However, when you need to record from a microphone, don't forget to change the profile back (as well as set the **Connector** in the **Input** tab to *Microphone*).

There is also "plain" sound recorder (which is installed by default on Ubuntu: **Applications > Sound & Video > Sound Recorder**) for most basic recording, but I'd always go with Audacity.

@kev77: yeah, it's amazing piece of software indeed :) I discovered a book published in March this year: [Getting Started with Audacity 1.3](https://www.packtpub.com/getting-started-with-audacity-1-3/book), which looks like a nice intro for beginners (and maybe useful to advanced users too).

THANKS! will try it out asap:guitar:

---

