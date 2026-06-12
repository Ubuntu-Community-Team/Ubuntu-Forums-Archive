---
title: "Sound problem with NWN and other applications"
date: 2008-01-13
forum: Gaming &amp; Leisure
---

### Post by Elphizo on 2008-01-13
Hi all. I'm a new Ubuntu user and I'm new in this community. I encountered several problems but I was able to solve them watching other threads...until now. I installed Neverwinter Nights client on ubuntu and, as many other peoples, I encountered the sound problem. I fixed that installing pulseaudio and everything worked fine in nwn. I was happy until I discovered that other applications, in particular TuxGuitar and M.U.G.E.N., lost their voice. In TuxGuitar I can't chose the Timidity plugin anymore and It's totally muted. If I uninstall pulseaudio everything turn back to normal..even the orrible sound in nwn :( . I don't know what to do. Can anyone help me whit this? Thanks!

---

### Post by dartoung on 2008-01-15
I faced the same dilemma when I first tried NWN in Ubuntu.  After a period of trying to get pulseaudio working with everything as well as it worked with NWN, I happened across the following thread (not specific to NWN):

[http://ubuntuforums.org/showthread.php?t=618131]("http://ubuntuforums.org/showthread.php?t=618131")

...which got me thinking that a solution may be just to disable pulseaudio before running a program with which it agrees.  It's clunky, but seems to work, and it's better than uninstalling.  If the pulseoff script listed there is run, then other applications will be able to access alsa or whatever else is being overridden by pulseaudio.

There's some weirdness for me with the pulseon script and NWN...  I find the only way to get sound back in NWN is to run pulseoff, then run NWN once (with no sound), then start it back up again, whereupon the sound works.  Once again clunky, but seems to work.  I don't really need the pulseon script at all, ultimately.

Anyway, I'm pretty new to Ubuntu as well, so this may well be the most inelegant solution possible.  But it works, so I live with it.  Hope this at least gives you some ideas!

---

