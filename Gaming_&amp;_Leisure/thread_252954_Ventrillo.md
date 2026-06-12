---
title: "Ventrillo?"
date: 2006-09-07
forum: Gaming &amp; Leisure
---

### Post by deboring21 on 2006-09-07
Hey,
I'm doing some reseach on getting Ventrillo to work with wine so that I can take my guild to the next level with raiding. Has anyone had any success with getting it to work well enough for long term use? Thanks for your responces ahead of time.
-Ryan

---

### Post by linuksamiko on 2006-09-07
I got ventrilo to work. But it has been a while since I used it because I couldn't use the "Push-to-talk" option. But if you like to use voice detection I should works.
But I had at first problems with talking to other people. They couldn't here me very good. That was a codec issu and was fixed after I changed to another codec.

---

### Post by ahood on 2006-09-08
I recently got ventrilo (version 2.3.0) to work. Although a bit dated, I simply followed the instructions provided by endy, see [Ventrilo and wine]("http://ubuntuforums.org/showthread.php?t=41737") and it worked on my Dapper.

Once installed, I start a terminal and cd to the dirctory that contains the Ventrilo program files. I then start Ventrilo with the command

> wine ./Ventrilo.exe

I too had a problem with binding keys, but was able after unchecking the Setup option 'Use DirectInput to detect Hotkey' and using 'B' as the hotkey. Ctrl or Alt keys won't work.

Hope this helps.

---

### Post by Tantalus90 on 2006-09-08
Ugh , yes you can get ventrilo to work but having had 3 posts deleted without comment from the ventrilo forums for the offence of asking about the pending (well pending from 05.2005) linux client I really suggest using Teamspeak or another program. 

I wouldnt mind but they refuse to open the linux section of the forum so we can try sharing how to set it up in Wine 

Tant

---

### Post by jdunn on 2006-09-08
Use Teamspeak.  Its cross-platform and runs fine native in linux.  A long over-due update is expected later this year but the current version is every bit as good as ventrilo

---

### Post by ahood on 2006-09-08
I agree with Trant that it is best to use TeamSpeak as it runs in linux natively (I think). However, it may not be up to you (or me) when we are connecting to another's network. Teamspeak works really well in linux and has way more features than the linux version of ventrilo.

---

