---
title: "Horrible Sound WINE Diablo 2 LOD"
date: 2007-04-25
forum: Gaming &amp; Leisure
---

### Post by GSF1200S on 2007-04-25
Well, I managed to get Diablo 2 installed without too much trouble. 

The only thing is... the sound is horrible! Now, I read all about the 0.9.31 wine patch messing up the sound, and that 0.9.30 was fine, so that is what Im running now. The game seems to me like its running a *little* too fast, so maybe this is contributing to my sound issues.

I used the Glide video drivers as the video test couldnt find anything else (I know my 3D works- I play OpenArena and can use Beryl). I used the ALSA audio drivers as suggested in the install walkthrough. Whenever I open winecfg in a terminal and click on audio, it freezes for about 5 seconds, while the terminal complains about not having libjack.so 

So I have a few questions:

1) Is my sound issue due to the glide drivers and/or the fact the game runs a little fast?

2) Is the sound horrible because of this missing "libjack.so"?

3) Would the newest version of WINE (0.9.35) fix my current issues?

Any ideas, really.. I really want at least one game on the linux side of my HD, but the sound is so bad it really takes from the game.. Ill do whatever I have to to NOT install this game on Windows!

Cheers...

---

### Post by cogadh on 2007-04-25
I use 0.9.35 and I also had sound problems. Installing Jack didn't fix it, but it does make those annoying messages go away. I actually fixed through a Wine registry edit. Run regedit and add the following string:

HKCU/Software/Wine/Alsa Driver/UseDirectHW=y

That totally corrected my audio stuttering and timing issues.

---

### Post by ceno-byte on 2007-04-25
im having the same problem im running wine 0.9.33 where exactly do i put that string in regedit

---

### Post by cogadh on 2007-04-25
Under HKEY_CURRENT_USER->Software->Wine->Alsa Driver add the string "UseDirectHW" and modify the value to "y". See screenshot:

[IMG]http://home.comcast.net/~cogadh/pics/Screenshot-Wine_desktop.png[/IMG]

---

### Post by disturbedite on 2007-04-25
alsa audio support in diablo 2 has been screwy since about 0.9.31 and i believe still has not been resolved or "fixed" yet in 0.9.35.  it is not due to glide or jack, its a known issue (bug).

---

### Post by ceno-byte on 2007-04-25
OMG thnxs so much cogadh  you are a very helpful person :grin: it fixed the sound issue thank you so much for the screenshot on how to do it now i can play diablo 2 in harmony thnxs again

---

### Post by GSF1200S on 2007-04-25
> **cogadh said:**
> I use 0.9.35 and I also had sound problems. Installing Jack didn't fix it, but it does make those annoying messages go away. I actually fixed through a Wine registry edit. Run regedit and add the following string:

HKCU/Software/Wine/Alsa Driver/UseDirectHW=y

That totally corrected my audio stuttering and timing issues.


Would you suggest I upgrade WINE to 0.0.35 in order for this fix to work? I currently have 0.9.30...

Thanks so much for the info.. ill be trying it as soon as im off work!

---

### Post by cogadh on 2007-04-25
Not necessarily. The registry key should also work with 0.9.30. I would try that first, if it doesn't work, then try upgrading to 0.9.35.

---

### Post by GSF1200S on 2007-04-25
> **cogadh said:**
> Not necessarily. The registry key should also work with 0.9.30. I would try that first, if it doesn't work, then try upgrading to 0.9.35.
Cool.. ill give it a try.

Im guessing I can get libjack through synaptic, so Ill get that installed first when I get off work. Ill let you know how it all turns out. If this works, it may be a good idea for you to contact the author of the Diablo 2 tutorials and let them know what you figured out. This is good stuff that will help people get this game up and going! Thanks..

---

### Post by cogadh on 2007-04-26
I got it from the WineHQ site, in the developer's wiki. There are other registry keys that can be manually set, but I haven't really tested any of them to see what they can really do:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

EDIT - Except I have tested the "VideoMemorySize" key. Since Wine apparently emulates the video card specs, it will usually have the wrong video memory (default is 64 MB). This caused some problems for me with games that check for minimum requirements when launching. I edited the key to my correct video memory amount and problem solved. :)

---

### Post by GSF1200S on 2007-04-26
Dangit!! I dont even HAVE Alsa driver in regedit.. do I modify one of the others, or would it work if you gave me the values from scratch?

Heres a screenshot...

---

### Post by GSF1200S on 2007-04-26
Update:

I installed WINE 0.9.35, and I compiled Jack from source...

For some reason, I still dont have a ALSA Audio registry entry in WINE, and I still get an error message about not finding libjack.so when I click on the audio tab...

Any ideas? :confused:

---

### Post by cogadh on 2007-04-26
You have to create the ALSA key manually, it won't appear on it's own. You also have to have ALSA selected in winecfg as your sound driver.

---

### Post by GSF1200S on 2007-04-26
> **cogadh said:**
> You have to create the ALSA key manually, it won't appear on it's own. You also have to have ALSA selected in winecfg as your sound driver.

Ok.. should have realized that! Sound works perfect now. You should submit that to the tutorial guys so they can incorporate that into there guides. Many people across the internet think that WINE is broken after 0.9.30 for Diablo 2, but with your mod the sound is perfect. Thanks for the help! :)

---

### Post by cogadh on 2007-04-26
Glad to be of assistance! 8-)

---

### Post by disturbedite on 2007-04-27
dang!  i reinstalled my distro recently (kubuntu feisty) and finally got around to reinstalling d2 (+ lod) with wine 0.9.36.  i checked the registry and that key didn't exist.  so i created it, tried to run d2 (twice) and it didn't make slightest difference whatsoever for me.  ;(  
(i double checked the registry settings to make sure i didn't make a typo anywhere but it was to no avail).

---

### Post by GSF1200S on 2007-04-28
> **disturbedite said:**
> dang!  i reinstalled my distro recently (kubuntu feisty) and finally got around to reinstalling d2 (+ lod) with wine 0.9.36.  i checked the registry and that key didn't exist.  so i created it, tried to run d2 (twice) and it didn't make slightest difference whatsoever for me.  ;(  
(i double checked the registry settings to make sure i didn't make a typo anywhere but it was to no avail).

Well as cogadh told me, you are supposed to create it. Honestly, I didnt expect it to work, but it immediately did. 

Maybe its due to the fact that its 0.9.36... revert back to 35 and see what happens.. thats what im using right now..

---

### Post by disturbedite on 2007-04-28
eh...its not that important to me.  i don't play it that much, i'll just wait it out.

---

### Post by God Of Atheism on 2007-05-08
In Edgy, I had the sound working fine, even when running a media player such as Banshee or Beep to listen to music while playing Diablo II. I upgraded to Feisty the other day, and only now tried the game, and noticed that the sound was fine. That is, until I tried to listen to music simultaneously. At that moment, not only the sound, but also the game itself began to stutter, although it must be said, not immediately. First I started up Banshee, then Diablo II, and all was fine, until Banshee switched to the next track, then the above happened. I had the same with Beep, although the problems started earlier, probably due to me not rebooting in between. After I tried the method outlined above, Beep gives the message that the sound system is already in use, and closes itself. (this time I started Diablo II before starting beep)

In Edgy I sometimes started the media player first, sometimes first the game, and I had no problems. Okay, I must add that was Wine 9.30, which might be the reason for the lack of problems (apart from having to manually remove the arts driver or have winecfg crash on the audio-tab)

Is there a way to both play Diablo II with sound effects and listen to music (other than the game music) at the same time in Feisty? (which seems to have Wine 9.33)
Should I maybe get back to Wine 9.30? Or should I select different drivers for Wine and for the media player I want to use? (for example one using Alsa and the other Oss) I think I tried something like that for a different situation some time ago, with no luck. Or should I go through the hassle of using Jack (for both)? It is a solution that might actually work, but every time I use Ardour (which admittedly is not very often), setting up the Jack server is taking up way too much time, and success seems to be mostly dependent on lucky guesses as to what to connect to what and when.

Edit:
I forgot to mention that I use Diablo II Lod 1.11b

One option I thought about is having a media player running under Wine as well, however, I've noticed that Wine tends to crash when invoked twice. In particular, I tried to run Diablo II and [Atma](http://atma.diabloii.net) simultaneously, but with crashes as a result.

---

### Post by mrklaw on 2010-05-19
thanks for the registry hack for the Alsa driver in Wine. It fixed my choppy sound problems too.

---

