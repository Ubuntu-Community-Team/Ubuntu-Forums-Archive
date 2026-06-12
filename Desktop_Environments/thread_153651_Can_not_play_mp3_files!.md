---
title: "Can not play mp3 files!"
date: 2006-04-01
forum: Desktop Environments
---

### Post by atheist on 2006-04-01
Hello,

When I click on an mp3 file I am getting a message:
[COLOR="Black"][B]
Totem could not start up.

The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector.[/B][/COLOR]

I do not have other video or audio programs running. What is wrong?

---

### Post by taurus on 2006-04-01
You can use xmms to play your mp3s and if you don't have xmms, use synaptic to install it together with xmms-mp3.  You can use the search for everything that is related to xmms by typing xmms in the field.  First, make sure you remove the # in front of the lines for universe and multiverse in /etc/apt/sources.list.
```

sudo gedit /etc/apt/sources.list

```

---

### Post by atheist on 2006-04-01
Thank you for the advice, I will install xmms.

But... - what is wrong with Totem? Can I fix the problem? Is it  bug in Ubuntu?

---

### Post by taurus on 2006-04-01
I am not sure whether it's a bug in totem but perhaps you need to install gstreamer plugins to get it working!  Personally, I'd never like totem.  I use xmms to play my mp3s, mplayer to play my movies, and xine to play my DVDs...  ;)

---

