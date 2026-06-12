---
title: "Strange sound issue w/ certain apps"
date: 2005-11-09
forum: Desktop Environments
---

### Post by remick182 on 2005-11-09
I just recently upgraded to Breezy and have been making some modifications to my system and I think I fudged something.  My sound works for videos (mpegs played through totem or xine) and it works for system sounds (startup, shut down and all the other little beeps).  I had been going down the list here:

[COLOR="RoyalBlue"]http://help.ubuntu.com/starterguide/C/faqguide-all.html[/COLOR]

installing all of the apps I would use.  I tested them after installation and all seemed O.K.  I played Frozen Bubble for awhile and the sound and music worked fine.  However, at some point, I must have tried to edit something, and now I have _no_ sound whenever I play Frozen Bubble (the sound block is unchecked and I can't check it manually).

The games I play through cedega have the same issue of lacking sound, but I've had some luck by closing cedega and restarting it a few times and sometimes, very rarely, but sometimes the sound will work.  This may be an unrelated issue though.

Another oddity (to me) is that my wife has a profile on Ubuntu which I just started configuring for her today.  All I've done to her account is change the background image.  I tried to play Frozen Bubble on her login out of curiousity.  _The sound worked fine_.

I tried to compare sound and multimedia settings, but they appear the same.

Under **System > Preferences > Sound**:
Enable sound server startup = [COLOR="Lime"]yes[/COLOR]
Sounds for events = [COLOR="Lime"]yes[/COLOR]
Default sound card = [COLOR="Orange"]Intel 82801DB-ICH4[/COLOR]

Under **System > Preferences > Multimedia Systems Selector**
Default Sink: Output = [COLOR="RoyalBlue"]ESD[/COLOR]
Default Source: Input = [COLOR="RoyalBlue"]OSS[/COLOR]

If anyone can help with this issue, it would be greatly appreciated!  I am still new in Linux, but I'm learning and having fun!  Thanks in advance.

---

### Post by Kapre on 2005-11-09
> I tried to compare sound and multimedia settings, but they appear the same.

Under **System > Preferences > Sound**:
Enable sound server startup = [COLOR="Lime"]yes[/COLOR]
Sounds for events = [COLOR="Lime"]yes[/COLOR]
Default sound card = [COLOR="Orange"]Intel 82801DB-ICH4[/COLOR]

Under **System > Preferences > Multimedia Systems Selector**
Default Sink: Output = [COLOR="RoyalBlue"]ESD[/COLOR]
Default Source: Input = [COLOR="RoyalBlue"]OSS[/COLOR]

If anyone can help with this issue, it would be greatly appreciated!  I am still new in Linux, but I'm learning and having fun!  Thanks in advance.

Remin - compare the default sink output and input on your profile and your wife's. I think they are not the same that is why she has sound and you dont. You can also check on the sound preference tab (System---Preferences-----Sound) and try if the wav files will sound.

K

---

### Post by remick182 on 2005-11-11
I think I found the issue with my sound not working, but I still see some small oddities.  First, I right-clicked on the little _speaker_ icon on went down to [COLOR="RoyalBlue"]Preferences[/COLOR].  Under the [COLOR="SeaGreen"]Volume Control Preferences[/COLOR] window, I had **Headphones** highlighted, so I switched it back to **Master**.  After I ran the game in cedega, the sound worked fine.  Kinda feel like a dolt, but I'm still learning Linux.

Something that I just noticed, too, is that every once in a while, I'm not sure if it happens at the login startup, but I've had no sound for music or games again.  I checked the speaker prefs again, and I was on Master.  Then I opened volume control and noticed that the PCM was muted.  I'm not sure why it keeps doing that now.

---

