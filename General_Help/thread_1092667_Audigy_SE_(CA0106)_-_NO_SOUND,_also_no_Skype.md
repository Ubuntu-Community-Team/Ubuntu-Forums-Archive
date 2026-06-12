---
title: "Audigy SE (CA0106) - NO SOUND, also no Skype"
date: 2009-03-10
forum: General Help
---

### Post by emarkay on 2009-03-10
First, please don't tell me to look at the ONE HUNDRED AND FIFTEEN page post about Pulse Audio.  I gave up at about page 20...


Make it simple, This is a Dell Dimension B110 with a Soundblaster Audigy SE sound card.

I have a few times heard the Ubuntu "drum" sounds on booting, and have heard the Skype test call, but have never heard more than a whisper in the mic playback.

Yes, ALL LEVELS are maxed, and I have spent almost an hour and a bazillion reboots etc, and my fingers are starting to hurt.

Anyone with similar config that has it working?

FWIW  in SOUND,Preferences, Sound Events, Sound Playback I have:

1 Autodetect
2 Intel entries with ALSA
4 Audigy entries with ALSA
3 Intel with OSS
3 Audigy with OSS
1 ALSA
1 OSS
1 Pulse Audio

---

### Post by emarkay on 2009-03-12
Well, he gave up and went back to Windows - I wish I knew more so I could have helped - he's a devoted Skype user - he grumbled about this "Geek Linux Bu&&Sh(t" and we lost another potential convert...  :(

---

### Post by shagy on 2009-07-24
Well, about a year ago a became new to Ubuntu. Let me tell you that I upgraded to Ubuntu 9.04 and I am unable to get that sound card working with youtube videos.How I got working the sound card? First go to System/Preferences/Sound. Once there on Default Mixer Tracks select CA106 (ALSA Mixer). Then on Sound events select Audigy SE[SB0570]CA0106. Then on Music and Movies select the same. Notice that the device is in AlSA and the options above on OSS. That works with the sound from the music players but not from youtube videos. The problem seems to be that youtube requires ALSA but the soound works  only with  OSS on Sound Events and so on, as I said. My suggestion is that you download and install Ubuntu 8.04.3 LTS because the Audigy SE worked best on that release. What I mean with best? The sound  from youtube videos works. That release will enable you to upgrade to the next LTS which will come on 2010. Hope this helps.

---

### Post by shagy on 2009-07-25
If anyone out there gets stuck with this issue on Ubuntu 9.04 here is the solution that worked for me. Go to System/Preferences/ Sound and put the options as the photo I am posting if you use the Creative Sound Blaster Audigy SE. Hope this helps. If this does not work for yo check out the following links that helped me. [https://answers.launchpad.net/ubuntu/+question/68518]("https://answers.launchpad.net/ubuntu/+question/68518")

The second one is the following:
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html]("http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html")

---

### Post by shagy on 2009-07-25
Oops! I forgot the image. But I can´t upload the image because I don't have a webpage. So once you are in Sound you you'll need do select the following.

Sound Events: Pulse Audio Sound Server
Music and Movies: The same as above.
Audio Conferencing: The same as above on both selections.
Default Mixer tracks: CA0106 (Alsa Mixer)

---

### Post by Johnius on 2009-08-03
Check out this thread, too:  [http://ubuntuforums.org/showthread.php?t=1222557&highlight=audigy&page=2](http://ubuntuforums.org/showthread.php?t=1222557&highlight=audigy&page=2)

---

