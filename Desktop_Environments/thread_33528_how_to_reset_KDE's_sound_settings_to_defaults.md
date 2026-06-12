---
title: "how to reset KDE's sound settings to defaults?"
date: 2005-05-11
forum: Desktop Environments
---

### Post by F for Fragging on 2005-05-11
Can anyone tell me how I reset the sound settings of KDE back to default, and how to reset the Kaffeine settings?

I posted about this problem here as well: [http://ubuntuforums.org/showthread.php?t=32177](http://ubuntuforums.org/showthread.php?t=32177) but nobody has been able to help me. My sound has been working fine in Kubuntu since the installation, until I was watching a video file with AC-3 sound in Kaffeine. I accidentally pressed the U-key for "Mute". I pressed it again so that it would unmute, and I heard the sound again. After a while I closed Kaffeine and opened another video file, one that didn't have AC-3. Now I didn't hear any sound anymore. I tried pressing the mute key again, but then Kaffeine only displays "Mute: On", it doesn't toggle between mute: off and mute: on.
The problem seems to be system wide, because I can't get sound in games, amaroK as well. Only if I play a video file AC-3 it works, even with the mute on when I press the mute key.

So my question is, how can I erase/reset to the default my personal settings for Kaffeine, and the sound stuff for KDE? I suspect that if I do that it will work again, because my sound worked fine before this incident. I hope that anyone can tell me this, otherwise I'd have reinstall Kubuntu (or another distro, because Kubuntu is driving me mad) completely, and then I'd have to backup everything.

---

### Post by verzonen on 2005-05-11
You can try "Control Center" from the menu 

But I had some similar problems with sound in kde after I did an upgrade of the kdelibs, I had to select the hardware manualy

Anyway have a go in that menu

---

### Post by F for Fragging on 2005-05-11
I tried that but it didn't work.

I've also just tried to delete all the config files in my home dir which are related to Xine, KMix and Kaffeine. I deleted them all, I assumed that the config files would be recreated with their defaults when I would restart KDE. I rebooted KDE and I noticed that I was right about that, when I started Kaffeine I got the first-run wizard again, and Xine and KMix were also back at their default settings. However still no sound.

I also created a new user to verify my suspicion that this problem is system wide. I logged in as that new user and opened amaroK, and played a stream with it. No sound there either.

So it isn't Kaffeine, KMix or Xine.



So it must be something else. So my question is more specifically, how do I change the settings of the KDE soundsystem, aRts, EsounD, Alsa or whatever back to their defaults?

---

### Post by F for Fragging on 2005-05-12
Ok, a small update. I know why I didn't hear sound now. Stereo sound is played though my rear speakers for some strange reason now. Again, I'm sure that it is not my hardware, because it works fine in Windows XP.

As I wrote in my original topic, I have a Soundblaster Audigy Player soundcard and a Creative Desktop Theatre DTT 2500 Digital 5.1 speakerset. The DTT2500 can be switched to "stereo mode" so that it uses only the two front speakers if listening to stereo audio, the fourpoint mode which uses all 4 speakers except for the center speaker if playing games with 5.1 audio, and it can be switched to AC-3 so that it uses all speakers.

When I set it to fourpoint it uses the rear and front speakers. Then I can hear the sound through my rear speakers if I'm listening to stereo audio. As I said, I can still hear AC-3 audio fine, then all the speakers are used.



Question is, how do I get the stereo sound to go though my front speakers again? I've filtered out most of the things which can cause the problem, so I suspect that it is some setting in my ALSA config, or whatever program has to do with it, which changed during the accident. How do I restore my ALSa config back to defaults then, when my sound worked fine?

---

