---
title: "Sound works but not nearly as loud as Windows?"
date: 2005-05-12
forum: Desktop Environments
---

### Post by NoTiG on 2005-05-12
In my multimedia systems selector it says im using ESD for sink, and OSS for source.
Is there any way i can get sound as loud as it is on windows? I mean... when i watch a DVD the highest setting for sound (all the way up) is about as loud as it is 1/4 of the way up on windows.

btw this is a fresh install of 32 bit hoary... the only thing ive installed so far is the automated script for new installs that installed the libdvd css to watch dvds and such.....

---

### Post by jcooper on 2005-05-12
Have you set the volume (the speaker icon in the notification area) to maximum?

It might also be necessary to open you volume properties and set most things to max (be wary of setting PCM too close to max, however).

---

### Post by NoTiG on 2005-05-12
Yes that is all the way up :P . and the sound is still pretty quiet.... compared to windows. and no, im not hard of hearing! . where exactly is "sound properties " ??? 
in system/preferences ... there are no controls under "sounds" or "multimedia systems selector"

---

### Post by jcooper on 2005-05-12
From memory, as I'm sat at an XP machine, you either right click the speaker or double click it...

At least I think thats what I've always done!

---

### Post by wulf on 2005-05-12
There are a lot more controls than in Windows. It seems to vary from soundcard to soundcard but on the various systems I've used Ubuntu lets me, if anything, get more volume than Windows. Make sure you experiment with all the settings (including the "obvious" thing of remembering to scroll left and right so you see them all!).

Wulf

---

### Post by NoTiG on 2005-05-12
In the volume control....... the volume was turned all the way up. however... the PCM values were at like 3/4 or 4/5 ... so i turned them all the way up . it DID make a difference........ and its louder now but its still not as loud as windows! . Maybe like half as loud instead of 1/4 . 

oh hold on a second...... Aparently there was an option that was not enabled by default. i had to right click on the sound, open volume control, then go to 
edit-preferences... and there was an unchecked value called "PCM2" . so i enabled it.. turned it up slightly and NOW ITS LOUDER THAN WINDOWS HAHA >:P

---

### Post by derrick1985 on 2005-05-12
[QUOTE=NoTiG]In the volume control....... the volume was turned all the way up. however... the PCM values were at like 3/4 or 4/5 ... so i turned them all the way up . it DID make a difference........ and its louder now but its still not as loud as windows! . Maybe like half as loud instead of 1/4 . 

oh hold on a second...... Aparently there was an option that was not enabled by default. i had to right click on the sound, open volume control, then go to 
edit-preferences... and there was an unchecked value called "PCM2" . so i enabled it.. turned it up slightly and NOW ITS LOUDER THAN WINDOWS HAHA >:P[/QUOTE]

now i'm going to have to check that out when i get home...

---

### Post by bored2k on 2005-05-12
Sound has always been better here in my experience, specially after applying Gandalf's ALSA trick.

---

