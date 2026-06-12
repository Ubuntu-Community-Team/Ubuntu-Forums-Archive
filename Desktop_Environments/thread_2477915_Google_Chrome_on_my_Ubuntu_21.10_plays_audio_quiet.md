---
title: "Google Chrome on my Ubuntu 21.10 plays audio quieter than Firefox"
date: 2022-08-10
forum: Desktop Environments
---

### Post by yurad on 2022-08-10
Google Chrome on my laptop with Ubuntu 21.10 plays audio quieter than Firefox and Chromium. This affects all videos: streaming, like YouTube and local from the disk. The maximum volume in Chrome sounds like  60% of the maximum volume in Firefox and Chromium. I always have the latest version of Chrome. Can someone tell me what is going in Chrome?

---

### Post by guiverc on 2022-08-11
Ubuntu 21.10 (along with all *flavors*) is ***End-of-Life***

 Notices of approaching EOL were sent out ~six weeks before EOL, and again after EOL was reached.

- [https://fridge.ubuntu.com/2022/06/01/ubuntu-21-10-impish-indri-reaches-end-of-life-on-july-14-2022/](https://fridge.ubuntu.com/2022/06/01/ubuntu-21-10-impish-indri-reaches-end-of-life-on-july-14-2022/) 
- [https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/](https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/)

I suggest you *release-upgrade* to a *supported* release ASAP if your machine is on-line.

The notices included a link on how to upgrade, however given EOL is now in the past, you may need to perform an extra step which is documented at [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by yurad on 2022-08-11
Upgrading now...  It was on my plate. Couldn't do it before because of ongoing project. I'll let you know right after.

---

### Post by yurad on 2022-08-12
@guiverc
I upgraded to 22.04. Previously I had bad experience with the performance after the upgrade to 21.10. That's why I delayed with 22.04.  Alas, I already encountered problems on 22.04 after yesterday's upgrade. One Chrome freezes. Later, I was unable to unlock the screen  after closing lid. I had to kill the X session. ( I am using Xorg.)  However, that's another topic.
There are no changes regarding the state of sound in Chrome. Firefox and Chromium are much louder.

---

### Post by &amp;KyT$0P# on 2022-08-13
How did you install Google Chrome? (What type of package is it installed as?)
Does the problem still occur in a new Google Chrome profile?

---

### Post by guiverc on 2022-08-13
I'm not a chrome user, so I likely can't help much.

I also sit on the *development* cycle, so whilst I was using *jammy* for six months, I've been off it for many months now, but I think the not-being a chrome user is my biggest drawback.

I'd assume it's a chrome config; but google/chrome being a 3rd party package can do its own thing.

Firefox is mostly Mozilla (3rd party) but it goes through Ubuntu repositories & the Desktop Team are involved in its creation, as they are with chromium (packaged by Ubuntu).

I'd look through the settings of chrome, also peek (*using terminal as changes are made*) to see where it stores its config/changes & look for clues that way. Being a 3rd party program/package it maybe the identical package that was used by *impish/jammy*, my own is as a `apt-cache policy google-chrome-stable` shows it came from `[http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main` so I'd not expect it to have changed when I switched from *impish* to *jammy* to *kinetic*, just update when google give a new version.

I'd likely change values on google-chrome that take effect, looking for where the config files change, once found, change the setting on volume that annoys you, see if you detect a config file change for that one.  exit the program (assuming it's the next start that has the issue), see if the config file changed? then re-start and look..  I actually control my levels using `pavucontrol`  (or `pavucontrol-qt` with LXQt) for the most part, and not via apps themselves, but google-chrome may differ to chromium; you could look there too, but the volume setting can only be changed (via pulse-audio-control) when the app is actually playing audio.

---

### Post by yurad on 2022-08-14
Normally I am a Firefox user. Just on 21.10 I had performance issues. I don't know why, but Firefox took much more memory than Chrome. That's why I switched to Chrome.  
I believe I installed google-chrome from the Google site. It was in 2017. After Chrome was regularly updated via Software Updater. 

I have several Chrome profiles. The problem occurs with all of them. Right now I tried a new Google Chrome profile.  The problem occurs in the new profile as well.

However, when I open a second Gnome session with another user the sound volume in all 3 browsers is the same. 
I will try to research more.

---

### Post by Holger_Gehrke on 2022-08-14
In pulseaudio you can set the volume separately and persistently per source - meaning per program asking pulse to play audio for them. I'd look in pavucontrol whether you at some time set the volume for chrome and forgot about it. That it is specific to the user but not to the profile fits well with that theory; pulse has separate settings per user but can't tell profiles apart (it's the same program, run by the same user ...).

Holger

---

### Post by yurad on 2022-08-14
Hi guys! Thanks for the advices!
1. Since Chrome was working fine in another user session, I tried the new Chrome configuration. ~/.config/google-chrome. It didn't change anything. The volume was low.
2. I never changed anything with pulseaudio, I didn't even have pavucontrol installed. Sometimes, not often, my laptop stopped playing all sounds, then I killed the daemon with pulseaudio -k and the sound always was back.
Anyway, I installed pavucontrol and found that Chrome's volume was lower than in other browsers. I ran into a few more glitches, but finally I set Chrome's volume to the same level as Firefox and Chromium.
I believe it was some kind of glitch. The pulseaudio setting was somehow changed without pavucontrol. Chrome sound is now working fine.
Thank you all again for your help!

---

