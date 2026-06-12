---
title: "Sound Blaster Audigy SE"
date: 2008-02-19
forum: Desktop Environments
---

### Post by uknowho008 on 2008-02-19
Hey, I just bought a "Sound Blaster Audigy SE" card and installed it. It seems to be working however, when i first installed it I had my headphones plugged in and it worked through my headphones. But when I unplugged my headphones sound didn't go to my speaker system until i restarted my computer and now it wont work on my headphones. I searched and couldn't seem to come up with a fix. Also when I adjust the volume with the main controls on ubuntu they don't effect anything. Thanks in advance.

---

### Post by kpkeerthi on 2008-02-19
Type **alsamixer** in a terminal and unmute (use 'm' key) and raise the volumes of the mixer channels.

---

### Post by uknowho008 on 2008-02-19
it doesnt seem to be working at all today. i raised all the levels and un-muted before i checked if there was any sound coming out. but now there is nothing.

---

### Post by uknowho008 on 2008-02-19
woops. i guess i muted it instead of un-muting it. but i still dont get any sound from my front jack to my headphones and i still cant control sound with ubuntus main volume control.

---

### Post by adubas on 2008-05-22
> **uknowho008 said:**
> woops. i guess i muted it instead of un-muting it. but i still dont get any sound from my front jack to my headphones and i still cant control sound with ubuntus main volume control.

Ever find a fix for this? I have the same card and same problem... volume control does not work...

---

### Post by kpkeerthi on 2008-05-23
To have the volume control control your card, go to System -> Preferences -> Sound and Select the channels you want to be controlled. Usually, Master & PCM.

---

### Post by adubas on 2008-05-27
> **kpkeerthi said:**
> To have the volume control control your card, go to System -> Preferences -> Sound and Select the channels you want to be controlled. Usually, Master & PCM.

I am running mythbuntu and don't have normal System -> Preferences. Not sure how to get it either to show up on the menu... anyway, this may be bug related... [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382")I tried a lot of things to get it to work and nothing...

The volume indicator moves on the screen but the sound level does not change at all... I have to manually use the volume dial on the speakers to change volume...

---

