---
title: "No sound, but only in KDE."
date: 2005-07-11
forum: Desktop Environments
---

### Post by perseus on 2005-07-11
Hello everybody!
I think that some of you knows about the audio delay that sometimes, and with some audio devices, happens with linux. I found and followed this HowTo: [http://www.ubuntuforums.org/showthread.php?t=26567&highlight=audio+delay](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=audio+delay)

Now all my apps, games, all the audio in my system is real-time and perfect!

That's my problem. Unfortunatly Kde stopped singing. I explain it better.
When I did the modifies that are described in the HowTo, when I started again kde a message appeared, and thold me  that it was impossible to initialize the sound server, using null as output. This only in kde, because for example Nexuiz's audio is BAM!
I found that if I use esound as audio device there is no error message, but anyway I've got no audio in kde with any device that can be set in kcontrol (alsa, oss, toss... Always no audio or error message). And, as I told, this happens only and only in kde. Midi, media player, CD... In the apps the sound is perfect!
Ah! I forgot to tell that unfortunately I've got a SiS SI7012 integrated audio with a weird CMedia 8738 chip. Compatible but in my experience one of the worst devices for linux. No volume control, bad driver support.

Any help really appreciated! Thanks!

-------

After few minutes I tried also this post [http://www.ubuntuforums.org/showthread.php?t=44753&highlight=sound+kde](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=sound+kde)

No sound in kde and full and perfect sound in the other apps. This is the output of the sound server:
Sound server fatal error:
AudioSubSystem::handleIO: write failed
len = 4096, can_write = 6000, errno = 17 (File exists)
This might be a sound hardware/driver specific problem (see aRts FAQ)

---

### Post by perseus on 2005-07-12
Excuse me if I answer myself, but there's really no one that have got my same problems? Is this post badly described? Maybe I wrong something! My english is not perfect, but I think I can explain myself.
I'm sorry, but I still have the same problem, no sound in kde, full perfect sound in every app I use.

Thanks you for any little or big help you can give me!!!

---

### Post by varunus on 2005-07-12
There's a howto in the tips and tricks section on how to get KDE to play sounds without using the ARTS sound server.  If you follow that, everything should work.  Do gnome applications have sound in KDE?  what about ALSA applications?  I'm pretty sure I've gotten it to work by setting ARTS to use ESD as the output method in the control center before...but that was on Warty.

---

### Post by perseus on 2005-07-14
Varunus... Thanks a lot!
Now I've got a perfect sounding kubuntu system.
Really big thanks!

---

### Post by vedro on 2005-07-14
ellow...

What did you do?

hand,
vedro

---

### Post by perseus on 2005-07-15
Licterally follow this howto:
[http://www.ubuntuforums.org/showthr...ght=audio+delay](http://www.ubuntuforums.org/showthr...ght=audio+delay)

Reboot. It's better.

Then follow this howto:
[http://www.ubuntuforums.org/showthread.php?t=47387&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=47387&highlight=sound)

Et voila'!!! Full, no delay, also full duplex sounding kde and apps!!!

 :grin: Ciao, and thanks to all the authors of the howtos!!!! :grin:

---

