---
title: "Audio distortion redux"
date: 2006-06-09
forum: Desktop Environments
---

### Post by | MM | on 2006-06-09
So i opened a thread about my problem just before dapper was released,  when the forums got rearranged i think my post kinda got lost.

Anyways my problem:
I have wierd audio distortion on certain mp3 and/or .wma files.  The distortion occurs when playback is done through either rhythmbox or totem.  Distortion does not occur when playback is through mplayer.

I ran Dapper from flight 4, and the issue only occured after i did an fresh install of the amd64 beta2 a week or so before the final was released.  Consequently on final release of Dapper i installed the i386 version, hoping the problem would sort its self out or that it was somehow isolated to the amd64 version, alas the problem has persisted (obviously :P ).

I suspect its a codec issue?
While i cant be sure i dont expect they are of super high quality bit rates, probably 192kbps mp3 rip.

I am aware of the PCM level affecting playback, but the distortion occurs even at PCm levels which leave the track bearly audible.

I attached a screenshot of a few things that may pertain to this issue;  and a short [audio]("http://www.ubuntuforums.org/attachment.php?attachmentid=10935&d=1149840329") file [.ogg in an archive].  you can clearly hear the distortion and even a couple of clicks from the get go, but particularly at about 20 - 22 seconds.  Im referring to the almost high pitch warble.
](*,) 

Any help would be much appreciated.
Cheers

---

### Post by | MM | on 2006-06-09
bump?

---

### Post by | MM | on 2006-06-11
:(

---

### Post by Redeyes_Gambit on 2006-09-16
}{ey | MM |

I'm having the same problem. At least I think I am :P . When your talking about the distortion you mean that kinda warble in the background, almost like a jet flying overhead in the distance, or water in your ears? Words are so inadequate to describe it but I think I know what your talking about. I have that same phenomenon but only in the left channel on certain songs (Extremely annoying! Ruins some of my favorite songs!)

What sound card is listed with device manager on your system?

Mine is a 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 audio controller from Intel corp. My machine is a TravelMate 2420 from Acer (laptop.)

I have VLC media player installed and it doesn't have that odd warble. However I love Rhythmbox because it's easy to use and will scrobble what I'm listening to to [http://www.last.fm/user/Redeyes_Gambit/](http://www.last.fm/user/Redeyes_Gambit/) (you can see what I've been listening to there.)

I agree with you that this must have something to do with a gstreamer codec that's installed. what ones do you have?

I hope we can figure out what is causing this and fix it.

RG

Edit: Just saw your screenshot. Not the same card, so that's not the issue I suppose.

---

### Post by Redeyes_Gambit on 2006-09-18
*bump*

Anyone else having this issue?

---

### Post by kdub432 on 2006-10-24
I AM! So annoying. I also have an AC97 soundcard. perhaps its the culprit in all of this.

---

### Post by kdub432 on 2006-10-24
Hah, got it. Just lower the PCM volume a little :D

---

### Post by bep on 2006-10-28
Have the same problem, seem to be a resampling problem of some kind. Also got a onboard VIA soundcard.

---

### Post by tedrogers on 2006-10-28
I have noticed (informally - not confirmed) that in Ubuntu the volume controls seem to drive the audio processors really hard.

I'm a music production guy by day...and I usually use Mac's and PC's (running windows). To me, 100% should be 0dB, but the odd thing about Ubuntu (and other Linux distros) is that the ALSA driver seems to drive audio outs to more than 100%. I can't confirm this...it's just my assumption based on what I have experienced.

So basically, back off your levels to about 70% and it should sort your problems out. What you're hearing is probably inharmoinic distorion produced by bit-depth overload...if you lower the levels it should fix it.

---

