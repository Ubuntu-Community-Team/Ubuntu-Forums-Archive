---
title: "Unreal 1 and Unreal Tournament sound issues"
date: 2011-09-25
forum: Gaming &amp; Leisure
---

### Post by Virus666 on 2011-09-25
Hi all,

I am trying to play **Unreal** and **Unreal Tournament** natively on Ubuntu. However, as you can imagine I am experiencing some sound problems...

First of all there was no sound; then I found out that **padsp** fixes that problem.

I could get the sound but there was 1-2 seconds of sound delay and popping noise. Then I discovered that changing **AudioDevice=ALAudio.ALAudioSubsystem** line as **AudioDevice=Audio.GenericAudioSubsystem** in **Unreal.ini** file solves the delay.

[https://help.ubuntu.com/community/Games/Native/UnrealTournament#No_sound](https://help.ubuntu.com/community/Games/Native/UnrealTournament#No_sound)

However, the random popping noise still existed and I fixed that issue by adding **snd_hda_intel position_fix=1** line to the **/etc/modprobe.d/alsa-base.conf** . But it appears that that solution has messed my **Skype** audio.

[http://ubuntuforums.org/showpost.php?p=2462987&postcount=14](http://ubuntuforums.org/showpost.php?p=2462987&postcount=14)

So, how can get rid of that popping noise without breaking Skype audio?

Thank you...

---

### Post by Virus666 on 2011-09-26
Any ideas?

---

### Post by maever on 2011-09-26
Hey Virus666,

Unreal Tournament 1 is somewhere high on my favorites list.
Though it choppy in it's narrative it was a very atmospheric game.

after a bit of searching I did find some tips on:
[http://fingel.com/ut/howtos/utonlinux.html](http://fingel.com/ut/howtos/utonlinux.html)

one of them referring to sound was:
;AudioDevice=ALAudio.ALAudioSubsystem
AudioDevice=Audio.GenericAudioSubsystem

Let me know how that works for you.

---

### Post by Virus666 on 2011-09-27
> **maever said:**
> Hey Virus666,

Unreal Tournament 1 is somewhere high on my favorites list.
Though it choppy in it's narrative it was a very atmospheric game.

after a bit of searching I did find some tips on:
[http://fingel.com/ut/howtos/utonlinux.html](http://fingel.com/ut/howtos/utonlinux.html)

one of them referring to sound was:
;AudioDevice=ALAudio.ALAudioSubsystem
AudioDevice=Audio.GenericAudioSubsystem

Let me know how that works for you.

Yeah, as I mentioned before I did that change and that fixes the audio delay with padsp. My problem was the random popping noise. By the way, that not disturb during the gameplay; it generally appears during the main manu. Thus, I prefer to ignore that little main manu noise; I am marking the threat as SOLVED.

Thank you... :)

---

