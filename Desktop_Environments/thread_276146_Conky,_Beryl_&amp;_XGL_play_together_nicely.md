---
title: "Conky, Beryl &amp; XGL play together nicely?"
date: 2006-10-12
forum: Desktop Environments
---

### Post by Aberrix on 2006-10-12
I followed this ([link]("http://ubuntuforums.org/showthread.php?t=268036")) to set up Beryl w/ xgl. I absolutely love it and want to keep it.

Also, I followed this ([link]("http://ubuntuforums.org/showthread.php?t=205865")) to get Conky 1.4.2 up and running just how I want. Also, I absolutely love this little app and want to keep it going.

However, when I got it all working my desktop icons were not showing up, they were there but its like conky was taking up my fullscreen and refreshing every second and "hiding" them. I tried this ([link]("http://forum.beryl-project.org/topic-5139-icons-missing-boot-problem-fixed-work-around")) and it seemed to solve my disappearing icons, however it then screwed up my conky and it did not show up properly. I can see it running via 'ps -aux | grep conky', however I don't see it. If I go to a command terminal and run it then everything is just fine.  What am I missing? has anyone gotten berryl & conky to play together nicely? Thanks in advance for your repsonse(s).

---

### Post by dcherryholmes on 2006-10-12
These are my options in .conkyrc.  It's working *pretty* well for me.  Sometimes I get dropshadows around the border of my conky window and every now and then I'll get a flicker of the window re-drawing.  So, not perfect, but it doesn't happen all that often, either.

# Create own window instead of using desktop (required in nautilus)
#own_window no
own_window yes
own_window_type override
own_window_transparent 1

---

### Post by Aberrix on 2006-10-12
> **dcherryholmes said:**
> 
# Create own window instead of using desktop (required in nautilus)
#own_window no
own_window yes
own_window_type override
own_window_transparent 1


and you do not have issues with it affecting your beryl or desktop icons?

thanks for the tips, i'll try it as soon as I get home ;)

---

### Post by m.musashi on 2006-10-13
> **Aberrix said:**
> I followed this ([link]("http://ubuntuforums.org/showthread.php?t=268036")) to set up Beryl w/ xgl. I absolutely love it and want to keep it.

Also, I followed this ([link]("http://ubuntuforums.org/showthread.php?t=205865")) to get Conky 1.4.2 up and running just how I want. Also, I absolutely love this little app and want to keep it going.

However, when I got it all working my desktop icons were not showing up, they were there but its like conky was taking up my fullscreen and refreshing every second and "hiding" them. I tried this ([link]("http://forum.beryl-project.org/topic-5139-icons-missing-boot-problem-fixed-work-around")) and it seemed to solve my disappearing icons, however it then screwed up my conky and it did not show up properly. I can see it running via 'ps -aux | grep conky', however I don't see it. If I go to a command terminal and run it then everything is just fine.  What am I missing? has anyone gotten berryl & conky to play together nicely? Thanks in advance for your repsonse(s).
I have similar problems with beryl and conky. For me, conky "steals" focus. About every 5-10 seconds, the page or app I'm viewing/using dims as if I clicked on something else - very annoying if you are typing. I had to turn off conky to get anything done. I suspect this is related to the symptoms you describe.

PS That is a sweet setup you have. I particularly like the tripple drive set up. Are the raptors that much faster than a 7200 drive? Are they noisy? I have a micro atx case and can only use 2 drives. I could partition a raptor and put ubuntu and windows each on a half and use my 250GB WD for storage. I might have to look into that.

---

### Post by Aberrix on 2006-10-13
> **dcherryholmes said:**
> 
# Create own window instead of using desktop (required in nautilus)
#own_window no
own_window yes
own_window_type override
own_window_transparent 1

This fixed my problem perfectly! Thank you!

---

### Post by Aberrix on 2006-10-13
> **m.musashi said:**
> 
PS That is a sweet setup you have. I particularly like the tripple drive set up. Are the raptors that much faster than a 7200 drive? Are they noisy?

I think the raptors noticably faster than a 7200 drive, especially when it comes to installing an OS or copying files. They aren't 1990's noisy if you know what I mean, but they're noticably louder than today's quiet drives, but still not terrible.

---

