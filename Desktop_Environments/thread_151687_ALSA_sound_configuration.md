---
title: "ALSA sound configuration"
date: 2006-03-28
forum: Desktop Environments
---

### Post by Anessen on 2006-03-28
Hello
I have been having some problems with my sound in a few games, it seems to be lagging behind be about half a second. Somebody suggested that maybe the card's hardware wasn't being used, only emulated, and to try the ALSA configuration utility.

The problem is, I can't find this utility. Normally, it has the command alsa-conf, but that doesn't work. I have the ALSA-utils package installed.

My sound card, by the way, is a Soundblaster Audigy LS. It's sort of the Audigy's little brother. My sound card is being recognised by Ubuntu, it is listed in the System -> Preferences -> Sound as "CAO106".

If you could help me get into the ALSA configuration tool, that would be great, or any ideas on how to stop it lagging in OpenGL games would be helpful!

---

### Post by mdmarmer on 2006-03-28
It's alsaconf

alsactl store 

is supposed to save your settings but it doesn't always work

sometimes you need to open a mixer and save the settings there as well

Mike

---

### Post by Anessen on 2006-03-28
alsa-conf doesn't work. Command not found:

```
csniper@x1-6-00-11-2f-cc-37-88:~$ sudo alsaconf
sudo: alsaconf: command not found

```

---

### Post by bionnaki on 2006-03-28
maybe
alsamixer
?

---

### Post by Anessen on 2006-03-28
Well, what i'm looking for is the configuration program for setting up my sound card, not just the volume settings. I remember on SuSE the utility "alsaconf" used to do this.

---

### Post by lab_rat on 2007-11-01
i think you might be looking for asoundconf ??

---

