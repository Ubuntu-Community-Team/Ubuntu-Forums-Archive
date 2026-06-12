---
title: "Custom log in sound doesn't work"
date: 2008-05-10
forum: Desktop Environments
---

### Post by ad_267 on 2008-05-10
I'm using Ubuntu 8.04. I went to System - Preferences - Sound - Sounds and selected a wav file as the log in sound but when I click play it won't play this file and it doesn't play when I log in. The file plays fine from any other application. Also after I click on play then none of the other sounds in the list will play either.

I tried moving the file to /usr/share/sounds/ but that didn't help. I checked the file ~/.gnome/sound/events/gnome.soundlist and that appeared to be fine. Is this a bug?

---

### Post by unutbu on 2008-05-10
I don't know if this is the kosher way to handle this, but...

```
gksudo gedit /etc/gdm/gdm.conf
```

Search for 'SoundOnLoginFile', about 71% of the way down (line 525). Change 
```
SoundOnLoginFile=/usr/share/sounds/question.wav
```
to whatever you like. I haven't tried it, but I think this should work, assuming you use gdm...

---

### Post by ad_267 on 2008-05-10
That's not the sound I want to change. That one can be changed by going to System - Administration - Login Window - Accessibility. I want to change the log in sound (default is the African sounding music) that is set for each user. You should be able to change this in System - Preferences - Sound but it isn't working. I only want to change this for one user so I can't just replace /usr/share/sounds/startup.wav

---

### Post by unutbu on 2008-05-10
Okay, now I understand.

I just used System>Preferences>Sounds to change my login sound to card_shuffle.wav. I then did a grep, looking for all files in ~/.gnome* which had text matching the word card.

This is the only file I found:
/home/cyrano/.gnome/sound/events/gnome.soundlist
```


[login]
file=/usr/share/sounds/card_shuffle.wav
```

(Is that what your one user's file looks like?)
I logged out, and upon logging in, I do hear the card shuffle. I'm on a 7.10 system. Sorry, that's all I know.

---

### Post by ad_267 on 2008-05-10
Yeah I found that too. I think it must be something about my particular wave file that it doesn't like because I copied startup.wav and called it something else and that file worked.

---

### Post by ad_267 on 2008-05-11
I've got this working now. I had to save the sound as an 8 bit wave file which is weird because all of the default sounds in /usr/share/sounds/ are 16 bit.

---

