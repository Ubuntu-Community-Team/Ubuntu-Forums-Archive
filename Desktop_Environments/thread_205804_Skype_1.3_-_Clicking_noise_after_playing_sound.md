---
title: "Skype 1.3 - Clicking noise after playing sound"
date: 2006-06-29
forum: Desktop Environments
---

### Post by padre999 on 2006-06-29
As mentioned before here [http://www.ubuntuforums.org/showthread.php?t=205400](http://www.ubuntuforums.org/showthread.php?t=205400)
there is a new Skype version out which I installed yesterday.

One thing that doesn't quite work for me is that every time after skype finishes playing a sound there is a loud "crack" in the speakers.
If you go to Tools>Options>Sounds you can play the skype sounds. The "busy signal" sound and the ones below show this kind of behaviour on my system.

Quite annoying in a chat. Everytime I recieve a message I get that ugly noise.

Someone experiencing the same problem? Any ideas what it could be?

Edit:

It is a known bug. On [http://share.skype.com/sites/linux/2006/06/open_beta.html](http://share.skype.com/sites/linux/2006/06/open_beta.html) it says:

> New sounds are in place, but due to a small bug they might click at the end &#8212; please test and tell if they click for you or not.

---

### Post by Kabal on 2006-06-29
Well I do hear a crack after receiving a msg.. little annoying.
But this new version is way faster in startup and sound duplex issues are fixed now.
 Still no drag&drop support tough.. waiting for that :)

---

### Post by crazy___cow on 2006-06-29
Same problem. Changing sound files resolves the problem....you can use the files from skype 1.2!

---

### Post by hawko on 2006-06-29
[QUOTE=crazy___cow]Same problem. Changing sound files resolves the problem....you can use the files from skype 1.2![/QUOTE]

Same problem here. Where do the old sounds reside?

---

### Post by crazy___cow on 2006-06-30
The  sounds are located in /usr/share/skype/sound/. For the old sounds, you can download "skype-1.2.0.18.tar.bz2" and extract them.....

---

### Post by AiBo on 2006-06-30
Just downloaded the new skype.

Echo test sounds great, but I cannot seem to get it to pick up my voice.  I am using a IBM Thinkpad T22 with a built in original sound card setup.  The mic picks up, I can hear it through the speakers when I speak into it, but I do not think it is capturing the sound, because it does not play back.

I have enabled everything in Volume Control.  I have tried both ALSA and OSS.  Same problem with both.

It would be great if I could solve this problem.  We are a small company with a number of people using IBM Thinkpad T22.  I have been trying to move our company over to Ubuntu.  I have managed to convince one person, but his willingness is fading quickly as skype is needed for some of our international business.

I have encounter the same problem when I run skype thru wine.  Although if I boot into window$ everything works like a charm.

Thanks in advance for any help any of you may be able to give!

---

### Post by padre999 on 2006-06-30
[QUOTE=AiBo]
Echo test sounds great, but I cannot seem to get it to pick up my voice.  [/QUOTE]

Did you use the prior version with dsp-hijacker? Then you should have a look here

[http://ubuntuforums.org/showthread.php?t=205400](http://ubuntuforums.org/showthread.php?t=205400)

Otherwise I would start a new thread in this forum describing your problem, as it doesn't really fit into this thread. The problem I described has nothing to do with the one you describe. I think you will find help more quickly if you make your own posting.

Another helpful place to check out are the skype forums.

[http://forum.skype.com/](http://forum.skype.com/) especially the Linux section...

good luck

---

### Post by hawko on 2006-06-30
[QUOTE=crazy___cow]The  sounds are located in /usr/share/skype/sound/. For the old sounds, you can download "skype-1.2.0.18.tar.bz2" and extract them.....[/QUOTE]

Thanks mate!

---

