---
title: "Quake4 no sound, OSS and ALSA not working properly, Dapper"
date: 2006-05-20
forum: Gaming &amp; Leisure
---

### Post by weh on 2006-05-20
I've got the latest Dapper install, and I'm having problems with getting the sound to work for Q4.  I've tried the "+set s_driver oss" thing, and it doesn't work.  ALSA works, but it's garbled badly.  The only thing that I can think of, is that the sound device in the audio settings in the game is greyed out.  I don't know how to change that since I'm new to Ubuntu/Linux in generaly since I've just started in the past week.  Any help would be much appreciated.  Thanks!

---

### Post by jrasith on 2006-06-04
I am also having the exact same problem... I am running Dapper and I have also tried "+set s_alsa_pcm plughw:0" and "+set s_alsa_pcm surround51" with "+set s_numberOfSpeakers 2" without any luck...

Peace;
-Joshua

---

### Post by jrasith on 2006-06-05
Alright, well I figured it out... OSS is muted by default (duhh, I know), so all you have to do is switch Quake to use oss as stated as above (two speakers might not be a bad idea as well, I hear it boosts performance) and go into volume control (if you are under gnome), then File -> Change Device and select the oss option, turn the volume up and you're all set!

---

### Post by RawMustard on 2006-07-05
I just went into my ~/.quake4/q4base/Quake4Config.cfg and changed the line seta s_driver "best" to seta s_driver "oss"

Worked for me!

---

### Post by ELD on 2007-09-26
I set mine to "oss" but it gives no sound at all :(

When on alsa or best the sound is really wierd and i can't heard a word people say ingame :(

---

### Post by acorey on 2007-10-06
Make sure you have oss-compat installed from the repo. then start with the oss command. I have alsa and was stumped as well. even with the alsa-oss wrapper it didn't work. 

I hope this works for others.

---

### Post by ELD on 2007-10-07
Updating to the latest version makes all sound work perfectly for me.

---

### Post by paulikabz on 2010-07-30
Actually i found the cause(for XP) its something from control panel.Click Sound and audio devices, then from the tabs up the window click Audio.Click Advanced at the first thing u find there and then Performance and make sure the hardware acceleration is at max.
        This worked perfectly for me

---

