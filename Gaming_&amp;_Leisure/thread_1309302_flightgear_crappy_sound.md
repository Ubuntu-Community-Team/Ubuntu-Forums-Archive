---
title: "flightgear crappy sound"
date: 2009-11-01
forum: Gaming &amp; Leisure
---

### Post by kainalu on 2009-11-01
Hello,

Trying to play flightgear (Koala) and get sound that sounds good for about 10 seconds and then goes to something that reminds me heavily of old dial up sounds. I found an old thread:

[http://ubuntuforums.org/archive/index.php/t-1125214.html](http://ubuntuforums.org/archive/index.php/t-1125214.html)

and some other stuff (cant re-find it now) that suggests that this problem may be that I need to manually compile the openal stuff, but the launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/openal/+bug/194919](https://bugs.launchpad.net/ubuntu/+source/openal/+bug/194919)
dates back to Hardy. No way it still exists in such a more modern Ubuntu right? if so, how do I go about making sure i compile this "open AL" correcty? can i just switch to another sound system like in prev. Ubuntu's? the feature seems to have gone missing from the  sound control panel. Any ideas?

Thanks

---

### Post by kainalu on 2009-11-03
Does anyone have any ideas on how to repair/replace openal or how to use a different audio manager? would switching audio managers even help? 


thanks!

---

### Post by dearingj on 2009-11-03
I've been having the same problem with other games that use OpenAL. I found these instructions on another forum; following these has significantly reduced (but not eliminated) the sound problem I was having:

Open up a text editor and copy & paste this into a new file:
```
(define devices '(dsp native))
```

Save the file in your home folder with the name ".openalrc". Then try running the game.

---

### Post by kainalu on 2009-11-03
That made it like 75% better. Much more playable than before. Still will mess up but generally a lot less and it comes and goes instead of being constant.  THANKS!!

---

### Post by kainalu on 2009-11-15
OK this noise is horrible. Is there a way to disable/remove Pulse and switch back to ALSA for karmic? If not, Im going to have to go back to Ubuntu 8.10 to avoid all the problems Ive been having with Karmic.

---

### Post by stephanb2 on 2010-08-13
Flightgear is using OpenAL to play sounds. It seems that there is a bug with OpenAL + ALSA + Pulseaudio. I set OpenAL to use OSS rather than ALSA and it solved the problem on my system (Karmic x64 with the snd_hda_intel module).

This is done by creating a .openalrc file in your home folder with the following line:

```
drivers = oss
```For more control, copy /etc/openal/alsoft.conf to ~/.openalrc and edit it.

---

