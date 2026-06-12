---
title: "Default players and c-span video"
date: 2006-01-15
forum: General Help
---

### Post by adana on 2006-01-15
Two questions:

1) How do I set default players for audiol/video. I have installed realplayer but when I click on "recent programs", totem opens (and is unable to play the video) and I don't know how to change that. (In windows, realplayer works on these c-span videos.)

I see a file /usr/share/applications/defaults.list.  Do I have to edit that manually? 

2) I really don't care which application plays my audio/video as long as it works. Totem can't play those c-span videos -- is it missing something?  I hear gxine is good, but how would I make that the default player?  (Back to question 1, I guess.)

---

### Post by adana on 2006-01-16
no one can tell me how to change the default player?

---

### Post by adana on 2006-01-18
I guess not.  ok.

---

### Post by mcduck on 2006-01-18
It's done just the same way it's done in windows. Right-click a file, select Properties and then Open With.. There you can add new applications and select the default app to open files of that type.

By the way, if you install totem-xine (and win32codecs) totem will show all your videos with no problems.

---

### Post by adana on 2006-01-19
Yes, that worked!  (installing totem-xine).

I would still like to know how to change the default players in firefox, but at totem at least works now.

Now I would like to know how to get xine to play the videos in this link:    

[http://bloggingheads.tv/?id=50&tid=131](http://bloggingheads.tv/?id=50&tid=131)

I get the "no demuxer" error, although I have all the win32 codecs.

Thanks for the help!

---

### Post by mcduck on 2006-01-19
I use mplayer plugin with firefox. You could try if that works for you.

I tried the videos on that site too. mplayer plugin tries to open the video, but I get no picture. But I clicked the 'help' link under the video frame, and there are links that can be opened in external player. That way Totem-Xine shows the video fine. (I have Totem configured as default player for .wmv in Gnome)

---

