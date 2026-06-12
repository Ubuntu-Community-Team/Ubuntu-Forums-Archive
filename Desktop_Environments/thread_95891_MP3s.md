---
title: "MP3s"
date: 2005-11-27
forum: Desktop Environments
---

### Post by NiceMarmot on 2005-11-27
New to Ubuntu, got everything set up(even wireless:D ) but for some reason, I can't get Rythmbox or Serpentine to recognize MP3s as audio files. I can play them in Limewire's built in player, but not in Rythmbox. I installed all of the gstreamer packages, but it still doesn't see them. Am I missing something?
Thanks

---

### Post by Kjell on 2005-11-27
Hello 

To be able to play mp3 using Rhythmbox (0.9.0) I installed: 

gstreamer0.8-mad

Using synaptic, you find it in  universe repository

//Kjell

---

### Post by tomwell on 2005-11-27
Nice marmot,

Hey, MP3 is not an opensource file format, the people that invented it charge money for using it in an media player... 

as Kjell said you need to install gstreamer [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs)

Peace 

Tom

---

### Post by NiceMarmot on 2005-11-27
Thanks, got it working, i think I missed the gstreamer packages taht I needed.

---

