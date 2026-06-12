---
title: "Ubuntu wont give me space."
date: 2008-11-21
forum: Desktop Environments
---

### Post by Zigbigadoorlue on 2008-11-21
Ubuntu 8.4
Firefox 3.0.3
Opera 9.27
Epiphany 2.22.2

Run of the mill hardware, AMD 32bit 2gig processor, ATI 9800pro graphics card.

I have been having space issues. My home folder says I have 0 bites of free space even though I just deleted 600mb off of my desktop (which also says it has 0 bites). I have added nothing because I cant: "There is not enough disk space to save the file. Please free some disk space and try again." My browser works to a degree, it will brows sights but can only play the first 15 seconds of flash videos, presumably for space issues, though it seems like it wouldn't be able to play any at all, go figure. I cant burn music cd's because the music files need to be cashed and I cant view PDF on the internet.

I posted earlier about the problems I was having [here]("http://ubuntuforums.org/showthread.php?t=954072"). But now I think it specifically has to do with programs not being able to access space for temporary files. Maybe I don't have the right permissions to access my own space? I'm kinda noobtastic so I don't know if this is possible.

For some reason I can't run opera/epiphany without sudo. Firefox acts weird without sudo (won't recognize keywords and other annoying behaviors listed in detail in my other post linked above).

And one more bizarre symptom is clicking shutdown dose not work. It just shuts down the GUI, nothing but the background and the mouse pointer remains. I then have to enter terminal and manually shutdown.

Ive been having these problems for a month or more possibly since a new kernel was pushed through.

Any brain waves? If I cant figure something out soon I'm going to do my favorite Fix All for windows and format. Then I'll Install 8.10. My highest appreciation for anyone who can help. 

Rowan

---

### Post by taurus on 2008-11-21
Don't forget to empty your trash bin too.

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by Zigbigadoorlue on 2008-11-23
That is kind of rediculus how simple that was. Yes empying my Trash solved all of my problems including not being able to start opera and not being able to shut down.
 
This sounds like a bug. Why would haveing my trash full affect all those other things in that way? Also it seem like it should warn me that my trash is full, I didn't even think to look there especialy with all these weird simptoms, what if I was so noob I didn't know what a forum was?

Anyway thanks so much for the help now my computer works again.

Rowan

---

