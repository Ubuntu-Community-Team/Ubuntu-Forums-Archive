---
title: "No sound after upgrade to breezy"
date: 2005-11-28
forum: Desktop Environments
---

### Post by sudharshan on 2005-11-28
hi all,
upgraded my hoary to breezy 2day, but sadly i dont get to hear any of the cool system sounds. Now i do get the drumming sound when the gdm loads. but after login i dont get any, i m able to use xmms and oolite though. no trouble with that. i checked and rechecked whether i hav the proper multimedia sink selected (ALSA) and i hav no problem with that. i even tried reinstalling alsa no avail. what could be rong. i hav installed the ubuntu-sound package but i dont get to hear any of the system bells.

---

### Post by sudharshan on 2005-11-29
ok whers's the trouble.. do i need to edit some configuration files. heres something else i noticed. My sound card is getting detected properly in system > preferences > sound.
but no sound is heard when i run the device database wizard. isnt it strange,, i m able to get sound from the appliations but not system sounds and others

---

### Post by mrmcctt on 2005-11-29
Try this...

Go to MAIN MENU>SYSTEM>PREFERENCES>SOUND and check the box to "enable sound server startup".  This should give you your system sounds.  

Just so you know, if you play any games in Ubuntu you may have to uncheck this box before playing them or you may lose sound for the games.

---

### Post by mrmcctt on 2005-11-29
You might also want to go to MAIN MENU>SYSTEM>PREFERENCES>MULTIMEDIA SYSTEMS SELECTOR and try to run ALSA instead of ESD.  I had this problem when I first installed Ubuntu.  ESD was set to run by default.

---

### Post by sudharshan on 2005-11-29
i had already seen to these options as i had mentioned sound was working just fine in haory. the moment i upgraded to breezy evrything went quiet. i rechecked the multimedia system selector and i hav chosen alsa and also enabled 'sound server startup' and all. guess i need to edit some conf files. and did i mention i can hear the drumming sound when gdm starts

---

### Post by sudharshan on 2005-11-29
[QUOTE=mrmcctt]Try this...
Just so you know, if you play any games in Ubuntu you may have to uncheck this box before playing them or you may lose sound for the games.[/QUOTE]
 ok i got a clue...now i remember i could not get any sound in pingus in haory. dat was because the sound server was running. now i hav enable the 'sound server startup' but strangely i m able to hear the music from the games

this means that the sound server has not started even though its enabled...any commands to do so?

---

### Post by mrmcctt on 2005-11-29
[THIS LINK]("http://ubuntuguide.org/#configuresoundproperly") is from the Ubuntu Guide on configuring sound for Gnome.  Hopefully you haven't seen this and it may help you out.

Sorry about the previous posts.  My sound server is set to 'off' and I still get the drum sound at the GDM screen so I thought that might be a problem.  With the sound server 'off' I can still play mp3s and video with sound and not get any o fthe system sounds.

---

### Post by sudharshan on 2005-11-29
:D thanx mate...u r real life saver
worked like a charm...thanx again for pointing out ubuntuguide..didnt even know such a thing existed

---

### Post by mrmcctt on 2005-11-29
Just glad it worked out for you.

The two places I check first is that guide and [The Index of How-To's]("http://www.ubuntuforums.org/showthread.php?t=53050").  They have helped a lot and I keep them bookmarked.

---

