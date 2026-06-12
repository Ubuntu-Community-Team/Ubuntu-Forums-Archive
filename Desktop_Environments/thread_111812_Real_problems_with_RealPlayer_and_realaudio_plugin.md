---
title: "Real problems with RealPlayer and realaudio plugin"
date: 2006-01-03
forum: Desktop Environments
---

### Post by diffuser78 on 2006-01-03
Hi,

I think this is nearly unsolved problem in Ubuntu ( I have been posting this for almost 6 months now). 

I have had problems playing music on [www.raaga.com/hindi](www.raaga.com/hindi) using mozilla firefox as an embedded realplayer. It is because of the following error.
The following components are required

audio/x-pn-realaudio-plugin

Can anybody suggest or throw some pointer as to how to get them. I have gone on to various forums to get some info about audio/x-pn-realaudio-plugin
but with no success.

I appreciate all your help
Thanks guys

---

### Post by Perfect Storm on 2006-01-05
audio/x-pn-realaudio-plugin is part of mplayerplug-in and not realplayer.

```

RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.11

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
```

So you might try get mplayerplug-in and see if it solves your problem.

---

### Post by neilg4rqn on 2008-06-08
One of the main things I wanted Ubuntu to do was to allow me to go to [www.bbc.co.uk/radioscotland](www.bbc.co.uk/radioscotland) and listen to one of my favourite radio programmes. No such luck. The site wants me to use Real Player which I have installed version 11. When I go to 'Listen Live' I am invited to use "stand-alone real player". The resulting sound is completely broken up, absolutely useless. :(

I had written the above out ready to post when I read this thread and the suggestion from 'Artificial Intelligence' - Now my sound works just fine and I can record/listen to my programme. **Many thanks AI** as I have been tearing my hair out since 8.04 came out! I just didn't make the connection between mplayer and real player... :)

---

### Post by Perfect Storm on 2008-06-08
My pleasure ^_^

---

