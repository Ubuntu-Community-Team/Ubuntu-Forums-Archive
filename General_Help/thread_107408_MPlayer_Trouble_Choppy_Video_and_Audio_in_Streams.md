---
title: "MPlayer Trouble: Choppy Video and Audio in Streams"
date: 2005-12-22
forum: General Help
---

### Post by blue_thunder on 2005-12-22
Almost any media I stream has this horrible choppy effect in the video and audio. A few streams work fine, but I can't find any real correlation. Any help would be greatly appreciated.

---

### Post by three_sixteen on 2005-12-22
[QUOTE=blue_thunder]Almost any media I stream has this horrible choppy effect in the video and audio. A few streams work fine, but I can't find any real correlation. Any help would be greatly appreciated.[/QUOTE]

You sure your network just isn't bogged down?  Does non-streamed media play okay?

---

### Post by blue_thunder on 2005-12-22
Non-streamed is just fine, and I'm the only one actively using my network.

---

### Post by Jingo on 2006-01-27
Having this problem too.

Anyone solution?

---

### Post by beerorkid on 2006-01-27
from bennettg here [http://www.ubuntuforums.org/showthread.php?t=116068&highlight=choppy](http://www.ubuntuforums.org/showthread.php?t=116068&highlight=choppy)
> SOLVED.

edit /etc/mplayer/mplayer.conf add the following to the bottom of the file:

srate=48000


THEN EVERYTHING IS BLISS!!!!!!!!!!!!!!!!!!

I rebooted and it is working now

---

### Post by BitTorrentBuddha on 2006-01-28
I'm having a similar problem, except mine is choppy all the time, not just on streams

---

### Post by kewl1uk on 2006-01-28
Playing as the file is being downloaded. Try pausing to give the file a chance to download and then start it.

---

### Post by beerorkid on 2006-01-28
I read on another post that going to about:config in the firefoxand setting
network.dns.disableIPv6 to false helps.

Although it would not matter outside of firefox.

---

### Post by marnom on 2006-01-29
[QUOTE=beerorkid]from bennettg here [http://www.ubuntuforums.org/showthre...ghlight=choppy](http://www.ubuntuforums.org/showthre...ghlight=choppy)
Quote:
SOLVED.

edit /etc/mplayer/mplayer.conf add the following to the bottom of the file:

srate=48000


THEN EVERYTHING IS BLISS!!!!!!!!!!!!!!!!!!

I rebooted and it is working now
__________________
may the forces of evil become confused on the way to your mail server

[www.beerorkid.com](www.beerorkid.com) and [www.fuckbirdflu.com](www.fuckbirdflu.com) [/QUOTE]

It works, thanks!!!

---

### Post by BitTorrentBuddha on 2006-01-30
adding srate=48000 made it so that my audio plays slightly faster than video while in full screen mode and they get out of sync [noticeably] after about a minute

---

### Post by beerorkid on 2006-01-30
I did notice that as well.  srry

---

### Post by BitTorrentBuddha on 2006-02-01
Is there a known fix that will make the video play well but also let it keep up with the sound?

---

### Post by pelle.k on 2006-02-11
*bump*

I've got the same problem, which seems to be cured by setting srate to 48000, however - this solution is only necessary on SOME, but not all movies i've got.

srate, or not - mplayer still gets out of sync, and I think we should investigate this matter further!

Suggestions anyone?

[edit]ok. so far i have been investigating, and it seems (at leat for me) alsa is causing the out of sync issues. oss works great, but oss only works when the sound card is free (not in use)
That sucks...[/edit]

---

### Post by pelle.k on 2006-02-11
This explains a lot. (gentoo users - they friggin rock)
[read this]("http://forums.gentoo.org//viewtopic-p-3018703.html?sid=1fb50ade6058e948f74e7dd8fffad51d#3018703")

what it says is, try: ao=alsa:device=hw (command line: -ao alsa:device=hw)

So chose the lesser of two evils (crappy oss, buggy alsa)

Seriously. I know... alsa doesn't suck and it will be sorted out in due time.
If this doesn't work out for ya... why not take a look at the FAQ at mplayerhq

[edit]ooops. it seems it may not work using the 2.6.12 kernel in breezy. I really dont know because i'm in dapper :( you'll have to try it out and report back. sorry for that. if it doesn't work, maybe you shold have a shot on oss emulation layer using alsa...[/edit]

---

### Post by OldGaf on 2006-02-15
Can I use gxine or some other app to stream vid from pages like [www.video.google.com?](www.video.google.com?)

---

