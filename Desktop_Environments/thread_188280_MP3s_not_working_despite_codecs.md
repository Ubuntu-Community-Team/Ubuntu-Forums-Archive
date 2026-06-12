---
title: "MP3s not working despite codecs"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Nrbelex on 2006-06-03
I just installed Dapper Drake and ran EasyUbuntu. I figured with all the multimedia selections checked off, MP3s wouldn't need any more work - No such luck. So then I went on the Ubuntu IRC channel and was told that I should install XMMS. XMMS works but I would prefer to use a program like Rhythmbox  instead and it still can't play MP3s. Totem also can't play them and gives the error "could not get/set settings from/on resource." Help would be much appreciated.

~ Brett

---

### Post by JoWilly on 2006-06-03
Have you installed all the gstreamer10 plugins (especially fluendo mp3) ?

This will get you all you need in totem,rythmbox etc...

EDIT : don't forget to enable the universe and multiverse repos.

---

### Post by Nrbelex on 2006-06-04
Yes to all of the above...

~ Brett

---

### Post by Nrbelex on 2006-06-05
... bump? ](*,) 

I had them all installed from EasyUbuntu but since that didn't work, I manually re-installed all the gstreamer codecs. 

~ Brett

---

### Post by titus1950 on 2006-06-05
[QUOTE=Nrbelex]... bump? ](*,) 

I had them all installed from EasyUbuntu but since that didn't work, I manually re-installed all the gstreamer codecs. 

~ Brett[/QUOTE]

I dont know what you have done so far but try to follow this ....

[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

---

### Post by Nrbelex on 2006-06-05
I've done that and looked at that page *many* times. I definitely have that installed.

~ Brett

---

### Post by titus1950 on 2006-06-05
[QUOTE=Nrbelex]I've done that and looked at that page *many* times. I definitely have that installed.

~ Brett[/QUOTE]

If you want do as I do,

Install:    Totem Xine,Xine-ui ,xine extra codecs,Amarok and amarok xine engine. (only a recomendation)....

If you install all the other codecs they just work perfectly.

---

