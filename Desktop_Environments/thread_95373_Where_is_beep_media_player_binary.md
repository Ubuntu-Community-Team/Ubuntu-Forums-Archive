---
title: "Where is beep media player binary?"
date: 2005-11-26
forum: Desktop Environments
---

### Post by rturner on 2005-11-26
I really liked the Beep Media player for playing .pls files at shoutcast.com, mainly because it listed the artist.  Be that as it may, I installed RealPlayer and it hijacked Beep Media Player's spot as the default .pls plugin in Firefox.  I tried locating the binary when the "play using default...." window comes up but I can't find it.  Which and whereis only located the beep .gz file.  I'd appreciate any guidance.

---

### Post by Xian on 2005-11-26
```
$ whereis beep-media-player
beep-media-player: /usr/bin/beep-media-player <snip>
```

/usr/bin/beep-media-player

---

### Post by rturner on 2005-11-26
Thanks.  I found it.  And it looks like I was whereis-ing for the wrong name for beep-media-player.

---

### Post by stalefries on 2005-11-26
Try downloading a .pls file to your Desktop. Then right-click the file, and go to Properties (I think, I know that it's one of the right click menu options). Then in the window that pops up, there should be something about what program to open the file in. Select Beep and set it as default. 

I'm sorry if this is sort of vague, but it should be enough to get you through the process.

---

### Post by rturner on 2005-11-26
Yes, that works.  Prior to installing Ubuntu I always had trouble getting the sound to work at all.  I'd spend time researching how to get Alsa working with my sound card and I'd finally get something going only to have it break a month later.  With the Ubuntu live cd I got sound working right out of the box, so I've switched (to Hoary, now Breezy) and now I'm getting picky about which app I'm using.  :smile:  I even bought decent speakers yesterday.

---

