---
title: "Totem Media Player issue"
date: 2005-04-06
forum: Desktop Environments
---

### Post by Runewalsh3 on 2005-04-06
Hey, I am a little new to ubuntu, but I am somewhat experianced with linux. I was wondering, when I try to play a file in Totem, for some reason I get an error box such as this one. I installed libmad, and pretty much every other mp3 codec I could think of. To no avail. Here is the dialogue box:
[IMG]http://www.freewebs.com/battlefieldfbla/Screenshot-Error.png[/IMG] 
Does Totem/ubuntu not come with an mp3 codec? Any ideas?

---

### Post by Runewalsh3 on 2005-04-06
If it helps, I tried to start audacity and it also came up with an error:

There was an error initilizing the audio i/o layer. You will not be able to play or record audio.

Error:Host Error

I am thinking these two are somehow related.

---

### Post by Runewalsh3 on 2005-04-07
No one?? Any help?

---

### Post by Nis on 2005-04-07
Try installting totem-xine and then loading the file again.

---

### Post by Runewalsh3 on 2005-04-07
thanks! it works fine now, but I audacity still reports the error. Any ideas on that? If not, you have helped plenty  :D

---

### Post by eric71 on 2005-04-08
The Audacity problem is unrelated to the totem probblem.  Audacity doesn't know how to use Gnome's default sound system (ESD).  To use Audacity in Gnome you have to go to System>Preferences>Sound and uncheck "Enable sound server startup".  Of course this will shut off Gnome's system sounds, like all the cute little drum beats you hear.  It's a sacrifice you have to make to get Audacity and SKype to work in Ubuntu.  You'll also have to follow the Alsa config file part of this guide 

[http://www.ubuntuforums.org/showthread.php?t=8882&highlight=multiple+sounds](http://www.ubuntuforums.org/showthread.php?t=8882&highlight=multiple+sounds)

to enable hearing multiple sounds (i.e. xmms playing and skype ringing) at once.  ESD normally does this type of sound mixing, but if you disable it, Alsa can do it.

---

### Post by Runewalsh3 on 2005-04-08
That would really be great, being able to hear two sounds at once. Not that I would use it very much. :P

---

