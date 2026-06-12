---
title: "playing movies with subtitles"
date: 2009-05-13
forum: Desktop Environments
---

### Post by duott on 2009-05-13
Currently the only video player which runs vids with SOUND in Kubuntu Jaunty is Dragonplayer (no sound in Vlc, Smplayer and Firefox flash, and various Gnome players fail as well). However, Dragonplayer doesn't have SUBTITLES support enabled. 

Is there any fix yet to play movies with subs?

---

### Post by Monsieur Gonzalez on 2009-05-13
All players run fine here. Have you tried changing the audio settings in the players? For Smplayer, I have "alsa" as the audio out, but it might look for pulseaudio, which I don't know if is installed by default on Kubuntu.

---

### Post by HavocXphere on 2009-05-13
imo your best chance is to fix VLC.

VLC works...its just a bit tricky to get it working and it keeps forgetting the settings (under 8.10 at least).:(

Set it to ALSA in the settings. Then switch to the advanced view of settings. Go to output module->ALSA and then select your device there. (This is the setting it keeps forgetting)

Make sure nothing else is using the sound card...cause there is some issue with only being able to play 1 sound app at a time.

Setting default ALSA output device:
asoundconf list
asoundconf set-default-device [device_name_from_listing]

Fixing ALSA freeze
alsa force-reload

Hope that helps.

---

### Post by duott on 2009-05-13
Thanks guys it works ):P I've set "Audigy2" as output device in Smplayer and "UNIX OSS" in VLC and voilà! they have sound.

Flash with no sound is still a major disappointment though :(

---

### Post by Monsieur Gonzalez on 2009-05-13
Did you install Flash-nonfree from the repos? From your sig, it looks like you're running x86_64; did you try the 64 bits native flash player or the one in ubuntu's repo? 

[Here]("http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html") you'll find the directions on how to install the native flash player for 64 bits.

---

### Post by Zorael on 2009-05-13
Obviously, first check your volume settings and see you don't have any channels muted. See [http://ubuntuforums.org/showthread.php?p=6883063](http://ubuntuforums.org/showthread.php?p=6883063).

Second, if you have several soundcards - which sounds like it's the case if you had to set a specific one as your output in smplayer - you need to set one as your *ALSA* default. It's *NOT* necessarily the same one as your KDE Phonon default, which Dragon Player etc obeys. See [http://ubuntuforums.org/showthread.php?p=6879677](http://ubuntuforums.org/showthread.php?p=6879677).

---

### Post by duott on 2009-05-26
> Did you install Flash-nonfree from the repos? From your sig, it looks like you're running x86_64; did you try the 64 bits native flash player or the one in ubuntu's repo?

Tried both, nothing works.

> Obviously, first check your volume settings and see you don't have any channels muted.

I don't.

> Second, if you have several soundcards - which sounds like it's the case if you had to set a specific one as your output in smplayer - you need to set one as your *ALSA* default. It's *NOT* necessarily the same one as your KDE Phonon default, which Dragon Player etc obeys

I came across this solution already but it didn't help. I have Audigy2 (which I use) and some kind of standard built-in soundcard.

---

