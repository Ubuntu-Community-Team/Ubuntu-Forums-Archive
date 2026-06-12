---
title: "assaultcube sound problem"
date: 2009-11-29
forum: Gaming &amp; Leisure
---

### Post by h2z on 2009-11-29
I've installed assaultcube from getdeb, the latest openal libs and libsdl pulse, but can't seem to get any sound when playing the game. In fact, as soon as I start the game, all sounds stop (I have rythembox playing) and I get the following errors:

```

stefan@StefanUbuntu:~$ assaultcube
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

```

Only way to enable the sounds back is to goto sound preferences, disable and re enable the hardware profile.

Is there a fix for this?


EDIT: Just tried without rythembox running and sounds work in game. I would still like to have music playing and have in game sounds tho...

---

### Post by kostkon on 2009-11-29
Give this in a terminal (to create a file that specifies which device to be used by OpenAL):
```
echo "(define devices '(sdl))" > ~/.openalrc
```
Restart your apps and test the sound again.

Hope that helps.

---

### Post by h2z on 2009-12-04
I see no apparent change, rhytembox is playing and when launching the game all sounds stop playing :(

---

### Post by haittah on 2010-03-15
> **h2z said:**
> I've installed assaultcube from getdeb, the latest openal libs and libsdl pulse, but can't seem to get any sound when playing the game. In fact, as soon as I start the game, all sounds stop (I have rythembox playing) and I get the following errors:

```

stefan@StefanUbuntu:~$ assaultcube
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

```Only way to enable the sounds back is to goto sound preferences, disable and re enable the hardware profile.

Is there a fix for this?


EDIT: Just tried without rythembox running and sounds work in game. I would still like to have music playing and have in game sounds tho...




I had the same problem, there was something terribly wrong with the sound (something was ripping my speakers)... Not only with AC, the same thing was happening with openarena... But when i turned off the option  for openAL in openarena, the sound problems stopped.... SO I FOUND THE PROBLEM.... After searching the web for the option to disable openAL in AC, some guy (thank God for him) suggested this fix :)))) i am going to pass it to you my friends :))))) CAUSE IT WORKS :
TYPE IN YOUR TERMINAL THIS:
  	 	 	 	 	 	  sudo apt-get remove pulseaudio


p.s. hope it works for you too :))))))))

---

### Post by h2z on 2010-03-16
I have no intentions of removing pulse (...just yet), but thanks for the suggestion!

---

### Post by haittah on 2010-03-17
> **h2z said:**
> I have no intentions of removing pulse (...just yet), but thanks for the suggestion!

ok, your choice,my friend....but this tread is for all of those that have the same problem like we do :).

P.S.  i wanted to add one more thing:   when i removed pulseaudio, all the games work nicely (AC, Openarena, or wormux, that before didn't have any sound :))
But, there can be a side effect: when i removed pulseaudio, i really had problems with totem (so i removed it and installed VLC that works great), but the pleasure i have playing games in LINUX, is well worth the sacrifice of pulseaudio :D

---

### Post by altonbr on 2010-07-08
I had to remove pulseaudio to get openarena to work.

```
sudo aptitude purge pulseaudio
```

---

