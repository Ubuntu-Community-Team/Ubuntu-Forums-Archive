---
title: "VLC and w32codecs?"
date: 2005-07-26
forum: Desktop Environments
---

### Post by Hamman on 2005-07-26
I'm a recent user of Ubuntu and I'm currently trying out different media players. I've found Quod Libet to be the best for audio. and for video I'm using totem-xine and VLC. I must say that I like VLC better, but only totem plays restricted formats such as real and wmv. I've got w32codecs installed. Is there any way to make VLC use these to (so I can remove everything related to totem :P)?

---

### Post by frodon on 2005-07-26
There is a field in VLC prferences to set the path to w32codecs, find this field and add the path of your w32codecs (probably /usr/lib/w32codec ....). I think it's all you have to do, I have used VLC without any problems in the past but I prefer totem now.

---

### Post by Hamman on 2005-07-26
[QUOTE=frodon]There is a field in VLC prferences to set the path to w32codecs, find this field and add the path of your w32codecs (probably /usr/lib/w32codec ....). I think it's all you have to do, I have used VLC without any problems in the past but I prefer totem now.[/QUOTE]
 Thanks alot for the extremely quick reply!
You don't happen to know exactly were in the preferences one would change this? :P
I tried Misc. ---> "Modules search path" and pointed it to /usr/lib/win32 (where synaptic told me the w32codecs were), but it didn't work :(.

---

### Post by frodon on 2005-07-26
I'm not in front of my computer, but if I remember well it's not in this field. Something in video or codec tab , but be careful that some option are not available in beginner mode (you can set this mode in the first tab if I remember well).

EDIT : I find a [thread](http://ubuntuforums.org/showthread.php?t=37786&highlight=vlc+wmv)  interesting for your issue.
This one could also help you : [http://ubuntuforums.org/showthread.php?t=40932&highlight=vlc+wmv](http://ubuntuforums.org/showthread.php?t=40932&highlight=vlc+wmv).

---

### Post by Hamman on 2005-07-26
Thanks a lot for your time, and pardon my inability to search :P Just searched for vlc w32codecs, 
Tried reinstalling w32codecs, still no go.

---

### Post by frodon on 2005-07-26
It was the same for me when I began with ubuntu and this forum ;-) 
Have you installed ffmpeg ?

---

### Post by Hamman on 2005-07-26
[QUOTE=frodon]It was the same for me when I began with ubuntu and this forum ;-) 
Have you installed ffmpeg ?[/QUOTE]
 I installed ffmpeg but it made no difference... I also reinstalled vlc, but to no avail :(
I'm sure I'm doing some stupid misstake, I just can't figure out what....

---

### Post by frodon on 2005-07-27
If you still have problems try totem-xine, the interface is really nice and all work without any problems. I don't know why you have these problems with VLC, I tried yesterday to install it and play wmv files ...... and it works perfectly, you should search in the [ubuntu guide](http://www.frankandjacq.com/ubuntuguide/5.04/index.html) what you have forgot to install.
But my advise is to use totem-xine (you can find it in synaptic).

---

### Post by Hamman on 2005-07-27
[QUOTE=frodon]If you still have problems try totem-xine, the interface is really nice and all work without any problems. I don't know why you have these problems with VLC, I tried yesterday to install it and play wmv files ...... and it works perfectly, you should search in the [ubuntu guide](http://www.frankandjacq.com/ubuntuguide/5.04/index.html) what you have forgot to install.
But my advise is to use totem-xine (you can find it in synaptic).[/QUOTE]
 Yeah, I've got totem-xine installed and it's pretty good, but VLC supports some advanced features that totem lacks. For example support for .idx  subtitle files. I guess I'll use VLC for XviD etc and totem for real and wmv. Thanks for the help again!

---

